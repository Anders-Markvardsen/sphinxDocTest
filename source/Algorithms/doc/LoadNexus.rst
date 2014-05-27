Usage
-----

.. include:: howToDownloadUsageData.txt

**Example - Load ISIS histogram Nexus file:**
(see `LoadISISNexus <http://www.mantidproject.org/LoadISISNexus>`_ for more options)

.. testcode:: ExLoadISISnexus

   # Load LOQ histogram dataset
   ws = LoadNexus('LOQ49886.nxs') 
   
   print "The 1st x-value of the first spectrum is: " + str(ws.readX(0)[0])   

.. testcleanup:: ExLoadISISnexus

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExLoadISISnexus
   
   The 1st x-value of the first spectrum is: 5.0

**Example - Load ISIS Muon file:**
(see `LoadMuonNexus <http://www.mantidproject.org/LoadMuonNexus>`_ for more options)

.. testcode:: ExLoadISISMuon

   # Load ISIS multiperiod muon MUSR dataset  
   ws = LoadNexus('MUSR00015189.nxs') 
   
   print "The number of periods (entries) is: " + str(ws[0].getNumberOfEntries()) 

.. testcleanup:: ExLoadISISMuon

   DeleteWorkspace(ws[0])
   
Output:

.. testoutput:: ExLoadISISMuon
   
   The number of periods (entries) is: 2   

**Example - Load Mantid processed Nexus file ISIS:**
(see `LoadNexusProcessed <http://www.mantidproject.org/LoadNexusProcessed>`_ for more options:   

.. testcode:: ExLoadNexusProcessedWithLoadNexus

   # Load Mantid processed GEM data file
   ws = LoadNexus('GEM63437_Focussed_bank5.nxs') 
   
   print "The number of histograms (spectra) is: " + str(ws.getNumberHistograms()) 

.. testcleanup:: ExLoadNexusProcessedWithLoadNexus

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExLoadNexusProcessedWithLoadNexus
   
   The number of histograms (spectra) is: 1      
