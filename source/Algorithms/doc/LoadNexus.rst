Usage
-----

To run these usage example please first download the 
`TrainingCourseData <http://download.mantidproject.org/download.psp?f=/SampleData/TrainingCourseData.zip>`_, 
and add these to your path. In MantidPlot this is done using `Manage User Directories <http://www.mantidproject.org/ManageUserDirectories>`_.

Example - Load ISIS histogram Nexus file, see `LoadISISNexus <http://www.mantidproject.org/LoadISISNexus>`_ for more options:

.. testcode:: ExLoadISISnexus

   # Load LOQ histogram dataset
   ws = LoadNexus('LOQ49886.nxs') 
   
   # print out the first x-value of the first spectrum 
   print ws.readX(0)[0]   

.. testcleanup:: ExLoadISISnexus

   DeleteWorkspace(ws)
   
.. testoutput:: ExLoadISISnexus
   :hide:
   
   5.0

Example - Load ISIS Muon file, see `LoadMuonNexus <http://www.mantidproject.org/LoadMuonNexus>`_ for more options:   

.. testcode:: ExLoadISISMuon

   # Load ISIS multiperiod muon MUSR dataset  
   ws = LoadNexus('MUSR00015189.nxs') 
   
   # print out number of periods (entries)
   print ws[0].getNumberOfEntries() 

.. testcleanup:: ExLoadISISMuon

   DeleteWorkspace(ws[0])
   
.. testoutput:: ExLoadISISMuon
   :hide:
   
   2   

Example - Load Mantid processed Nexus file ISIS, see `LoadNexusProcessed <http://www.mantidproject.org/LoadNexusProcessed>`_ for more options:   

.. testcode:: ExLoadNexusProcessed

   # Load Mantid processed GEM data file
   ws = LoadNexus('GEM63437_Focussed_bank5.nxs') 
   
   # print out number of histograms (spectra)
   print ws.getNumberHistograms() 

.. testcleanup:: ExLoadNexusProcessed

   DeleteWorkspace(ws)
   
.. testoutput:: ExLoadNexusProcessed
   :hide:
   
   1      
