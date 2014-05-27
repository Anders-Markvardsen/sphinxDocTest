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

