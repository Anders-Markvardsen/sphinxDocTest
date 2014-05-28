Usage
-----

**Example - Fit a Gaussian to a peak in a spectrum:**

.. testcode:: ExFitPeak

   # create a workspace with a gaussian peak sitting on top of a linear (here flat) background
   ws = CreateSampleWorkspace(Function="User Defined", UserDefinedFunction="name=LinearBackground, \
      A0=0.3;name=Gaussian, PeakCentre=5, Height=10, Sigma=0.7", NumBanks=1, BankPixelWidth=1, XMin=0, XMax=10, BinWidth=0.1)

   # Setup the data to fit:
   workspaceIndex = 0  # the spectrum with which WorkspaceIndex to fit
   startX = 1      # specify fitting region 
   endX = 9      #
   
   # Setup the model, here a Gaussian, to fit to data
   tryCentre = '4'   # A start guess on peak centre
   sigma = '1'          # A start guess on peak width
   height = '8'         # A start guess on peak height
   myFunc = 'name=Gaussian, Height='+height+', PeakCentre='+tryCentre+', Sigma='+sigma
   # here purposely haven't included a linear background which mean fit will not be spot on
   # to include a linear background uncomment the line below
   #myFunc = 'name=LinearBackground, A0=0.3;name=Gaussian, Height='+height+', PeakCentre='+tryCentre+', Sigma='+sigma

   # Do the fitting
   fitStatus, chiSq, covarianceTable, paramTable, fitWorkspace = Fit(InputWorkspace='ws', \ 
      WorkspaceIndex=0, StartX = startX, EndX=endX, Output='fit', Function=myFunc)

   print "The fit was: " + fitStatus  
   print("chi-squared of fit is: %.2f" % chiSq)
   print("Fitted Height value is: %.2f" % paramTable.column(1)[0])
   print("Fitted centre value is: %.2f" % paramTable.column(1)[1]) 
   print("Fitted sigma value is: %.2f" % paramTable.column(1)[2])
   # fitWorkspace contains the data, the calculated and the difference patterns 
   print "Number of spectra in fitWorkspace is: " +  str(fitWorkspace.getNumberHistograms())
   print("The 20th y-value of the calculated pattern: %.4f" % fitWorkspace.readY(1)[19])    

.. testcleanup:: ExFitPeak

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExFitPeak
   
   The fit was: success
   chi-squared of fit is: 0.14
   Fitted Height value is: 9.79
   Fitted centre value is: 5.05
   Fitted sigma value is: 0.77
   Number of spectra in fitWorkspace is: 3
   The 20th y-value of the calculated pattern: 0.2361

