Usage
-----

.. include:: howToDownloadUsageData.txt

**Example - Diffraction focussing of HRPD data:**

.. testcode:: ExHRPDFocussing

   # Load HRP dataset
   ws = Load('HRP39180.RAW') 

   # specify groupping file, here using CalFile format
   cal_file = "hrpd_new_072_01_corr.cal"
   
   # For HRPD data, perform a unit convertion TOF->d-spacing, taking into account detector position offsets
   ws = AlignDetectors(InputWorkspace='ws',CalibrationFile=cal_file)
   # Focus the data
   ws = DiffractionFocussing(InputWorkspace='ws',GroupingFileName=cal_file)
      
   print("The 51st y-value is: %.3f" % ws.readY(0)[50])  

.. testcleanup:: ExHRPDFocussing

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExHRPDFocussing
   
   The 51st y-value is: 900.709

**Example - Demonstrating option PreserveEvents:**

.. testcode:: ExEventFocussing

   # create event workspace with one bank of 4 detectors
   ws = CreateSampleWorkspace(WorkspaceType="Event", XUnit="dSpacing", NumBanks=1, BankPixelWidth=2)
   
   # focus data in 4 spectra to 2 spectra according to .cal file and don't perserve events
   ws = DiffractionFocussing(InputWorkspace='ws', GroupingFileName="4detector_cal_example_file.cal" \
        , PreserveEvents=False)
   
   print "Number of focussed spectra: " + str(ws.getNumberHistograms()) 
   print "What type is the workspace after focussing: " + str(type(ws))

.. testcleanup:: ExEventFocussing

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExEventFocussing
   
   Number of focussed spectra: 2
   What type is the workspace after focussing: <class 'mantid.api._api.MatrixWorkspace'>
