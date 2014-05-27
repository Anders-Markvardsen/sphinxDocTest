Usage
-----

.. include:: howToDownloadUsageData.txt

**Example - Load ISIS histogram Nexus file:**
(see `LoadISISNexus <http://www.mantidproject.org/LoadISISNexus>`_ for more options)   

.. testcode:: ExLoadISISnexusHist

   # Load ISIS LOQ histogram dataset
   ws = Load('LOQ49886.nxs') 
   
   print "The 1st x-value of the first spectrum is: " + str(ws.readX(0)[0])      

.. testcleanup:: ExLoadISISnexusHist

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExLoadISISnexusHist
   
   The 1st x-value of the first spectrum is: 5.0

**Example - Load SNS/ISIS event Nexus file:** 
(see `LoadEventNexus <http://www.mantidproject.org/LoadEventNexus>`_ for more options)   

.. testcode:: ExLoadEventNexus

   # Load SNS HYS event dataset
   ws = Load('HYS_11092_event.nxs') 
   
   print "The number of histograms (spectra) is: " + str(ws.getNumberHistograms())

.. testcleanup:: ExLoadEventNexus

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExLoadEventNexus
   
   The number of histograms (spectra) is: 20480     
   
**Example - Load ISIS Muon file:**
(see `LoadMuonNexus <http://www.mantidproject.org/LoadMuonNexus>`_ for more options)   

.. testcode:: ExLoadISISMuon

   # Load ISIS multiperiod muon MUSR dataset
   ws = Load('MUSR00015189.nxs') 
   
   print "The number of periods (entries) is: " + str(ws[0].getNumberOfEntries()) 

.. testcleanup:: ExLoadISISMuon

   DeleteWorkspace(ws[0])

Output:

.. testoutput:: ExLoadISISMuon
   
   The number of periods (entries) is: 2    
   
**Example - Load Mantid processed Nexus file ISIS:**
(see `LoadNexusProcessed <http://www.mantidproject.org/LoadNexusProcessed>`_ for more options)  

.. testcode:: ExLoadNexusProcessedWithLoad

   # Load Mantid processed GEM data file  
   ws = Load('GEM63437_Focussed_bank5.nxs') 
   
   print "The number of histograms (spectra) is: " + str(ws.getNumberHistograms()) 

.. testcleanup:: ExLoadNexusProcessedWithLoad

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExLoadNexusProcessedWithLoad
   
   The number of histograms (spectra) is: 1   
