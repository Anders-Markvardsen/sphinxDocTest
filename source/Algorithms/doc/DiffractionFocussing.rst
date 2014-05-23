Usage
-----

To run these usage example please first download the 
`TrainingCourseData <http://download.mantidproject.org/download.psp?f=/SampleData/TrainingCourseData.zip>`_, 
and add these to your path. In MantidPlot this is done using `Manage User Directories <http://www.mantidproject.org/ManageUserDirectories>`_.

Example - Diffraction focussing for HRPD data:

.. testcode:: ExHRPDFocussing

   # Load HRP dataset
   ws = Load('HRP39180.RAW') 

   # specify groupping file, here using CalFile format
   cal_file = "hrpd_new_072_01_corr.cal"
   
   # For HRPD data, perform a unit convertion TOF->d-spacing, taking into account detector position offsets
   ws = AlignDetectors(InputWorkspace='ws',CalibrationFile=cal_file)
   # Focus the data
   ws = DiffractionFocussing(InputWorkspace='ws',GroupingFileName=cal_file)
      
   # print out chi-squared value for fit
   print("%.3f" % ws.readY(0)[50])  

.. testcleanup:: ExHRPDFocussing

   DeleteWorkspace(ws)
   
.. testoutput:: ExHRPDFocussing
   :hide:
   
   900.709

