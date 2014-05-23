Usage
-----

To run these usage example please first download the 
`TrainingCourseData <http://download.mantidproject.org/download.psp?f=/SampleData/TrainingCourseData.zip>`_, 
and add these to your path. In MantidPlot this is done using `Manage User Directories <http://www.mantidproject.org/ManageUserDirectories>`_.

Example - Load without any optional arguments

.. testcode:: ExLoadISISnexus

   # Load LOQ histogram dataset
   ws = LoadISISNexus('LOQ49886.nxs')
   
   # print out the first x-value of the first spectrum 
   print ws.readX(0)[0]   

.. testcleanup:: ExLoadISISnexus

   DeleteWorkspace(ws)
   
.. testoutput:: ExLoadISISnexus
   :hide:
   
   5.0

Example - Using SpectrumMin and SpectrumMax:   

.. testcode:: ExLoadSpectrumMinMax

   # Load from LOQ data file spectrum 2 to 3. 
   ws = LoadISISNexus('LOQ49886.nxs',SpectrumMin=2,SpectrumMax=3) 
   
   # print out number of histograms (spectra)
   print ws.getNumberHistograms() 

.. testcleanup:: ExLoadSpectrumMinMax

   DeleteWorkspace(ws)
   
.. testoutput:: ExLoadSpectrumMinMax
   :hide:
   
   2  

Example - Using EntryNumber:   

.. testcode:: ExLoadEntryNumber

   # Load first period of multiperiod POLREF data file 
   ws = LoadISISNexus('POLREF00004699.nxs', EntryNumber=1) 
   
   # print out number of histograms (spectra)
   print ws.getNumberHistograms() 

.. testcleanup:: ExLoadEntryNumber

   DeleteWorkspace(ws)
   
.. testoutput:: ExLoadEntryNumber
   :hide:
   
   246   
   
