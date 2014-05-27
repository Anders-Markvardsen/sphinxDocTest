Usage
-----

.. include:: howToDownloadUsageData.txt

**Example - Fit a Gaussian to a peak in a spectrum:**

.. testcode:: ExFitPeak

   # Load HRP dataset
   ws = Load('HRP39182.RAW') 
   
   # Setup the data to fit:
   workspaceIndex = 0  # the spectrum with which WorkspaceIndex to fit
   startX = 93000      # specify fitting region 
   endX = 93300        #
   
   # Setup the model, here a Gaussian, to fit to data
   tryCentre = '93150'   # A start guess on peak centre
   sigma = '20'          # A start guess on peak width
   height = '10'         # A start guess on peak height
   myFunc = 'name=Gaussian, Height='+height+', PeakCentre='+tryCentre+ \
              ', Sigma='+sigma
   
   # Do the fitting
   fitStatus, chiSq, covarianceTable, paramTable, fitWorkspace = Fit(InputWorkspace='ws', \ 
      WorkspaceIndex=0, StartX = startX, EndX=endX, Output='fit', Function=myFunc)
      
   print "The fit was: " + fitStatus  
   print("chi-squared of fit is: %.2f" % chiSq)
   print("Fitted Height value is: %.2f" % paramTable.column(1)[0])
   # fitWorkspace contains the data, the calculated and the difference patterns 
   print "Number of spectra in fitWorkspace is: " +  str(fitWorkspace.getNumberHistograms())
   print("The 20th y-value of the calculated pattern: %.4f" % fitWorkspace.readY(1)[19])  

.. testcleanup:: ExFitPeak

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExFitPeak
   
   The fit was: success
   chi-squared of fit is: 1.94
   Fitted Height value is: 20.77
   Number of spectra in fitWorkspace is: 3
   The 20th y-value of the calculated pattern: 6.1831

