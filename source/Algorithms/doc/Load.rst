Usage
-----

.. include:: howToDownloadUsageData.txt

**Example - Load ISIS histogram Nexus file:**
(see `LoadISISNexus <http://www.mantidproject.org/LoadISISNexus>`_ for more options)   

.. testcode:: ExLoadISISnexusHist

   # Load ISIS LOQ histogram dataset
   ws = Load('LOQ49886.nxs') 
   
   # print out the first x-value of the first spectrum 
   print ws.readX(0)[0]   

.. testcleanup:: ExLoadISISnexusHist

   DeleteWorkspace(ws)
   
.. testoutput:: ExLoadISISnexusHist
   :hide:
   
   5.0

**Example - Load SNS/ISIS event Nexus file:** 
(see `LoadEventNexus <http://www.mantidproject.org/LoadEventNexus>`_ for more options)   

.. testcode:: ExLoadEventNexus

   # Load SNS HYS event dataset
   ws = Load('HYS_11092_event.nxs') 
   
   # print out number of histograms (spectra)
   print ws.getNumberHistograms() 

.. testcleanup:: ExLoadEventNexus

   DeleteWorkspace(ws)
   
.. testoutput:: ExLoadEventNexus
   
   20480     
   
**Example - Load ISIS Muon file:**
(see `LoadMuonNexus <http://www.mantidproject.org/LoadMuonNexus>`_ for more options)   

.. testcode:: ExLoadISISMuon

   # Load ISIS multiperiod muon MUSR dataset
   ws = Load('MUSR00015189.nxs') 
   
   # print out number of periods (entries)
   print ws[0].getNumberOfEntries() 

.. testcleanup:: ExLoadISISMuon

   DeleteWorkspace(ws[0])

Output:

.. testoutput:: ExLoadISISMuon
   
   2    
   
Example - Load Mantid processed Nexus file ISIS, see `LoadNexusProcessed <http://www.mantidproject.org/LoadNexusProcessed>`_ for more options:   

.. testcode:: ExLoadNexusProcessedWithLoad

   # Load Mantid processed GEM data file  
   ws = Load('GEM63437_Focussed_bank5.nxs') 
   
   # print out number of histograms (spectra)
   print ws.getNumberHistograms() 

.. testcleanup:: ExLoadNexusProcessedWithLoad

   DeleteWorkspace(ws)
   
.. testoutput:: ExLoadNexusProcessedWithLoad
   :hide:
   
   1   
