Usage
-----

To run these usage example please first download the 
`TrainingCourseData <http://download.mantidproject.org/download.psp?f=/SampleData/TrainingCourseData.zip>`_, 
and add these to your path. In MantidPlot this is done using `Manage User Directories <http://www.mantidproject.org/ManageUserDirectories>`_.

Example - Fit a peak in a spectrum, see `LoadISISNexus <http://www.mantidproject.org/LoadISISNexus>`_ for more options:

.. testcode:: ExFitPeak

   # Load HRP dataset
   ws = Load('HRP39182.RAW') 
   
   # Setup fitting:
   workspaceIndex = 0  # the spectrum with which WorkspaceIndex to fit
   startX = 93000      # specify fitting region 
   endX = 93300        #
   tryCentre = str(93150)   # A start guess on peak centre
   sigma = 20          # A start guess on peak width
   height = 10         # A start guess on peak height
   
   # Do the fitting
   d0, chiSq, d1, d2, d3 = Fit(InputWorkspace='ws', WorkspaceIndex=0, \
      StartX = startX, EndX=endX, Output='fit', \
      Function='name=Gaussian,Height=10,PeakCentre='+tryCentre+',Sigma=20')
      
   # print out chi-squared value for fit
   print("%.2f" % chiSq)  

.. testcleanup:: ExFitPeak

   DeleteWorkspace(ws)
   
.. testoutput:: ExFitPeak
   :hide:
   
   1.94

