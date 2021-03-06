Usage
-----

.. include:: howToDownloadUsageData.txt

**Example - Load without any optional arguments:**

.. testcode:: ExLoadISISnexus

   # Load LOQ histogram dataset
   ws = LoadISISNexus('LOQ49886.nxs')
   
   print "The 1st x-value of the first spectrum is: " + str(ws.readX(0)[0])   

.. testcleanup:: ExLoadISISnexus

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExLoadISISnexus
   
   The 1st x-value of the first spectrum is: 5.0

**Example - Using SpectrumMin and SpectrumMax:**  

.. testcode:: ExLoadSpectrumMinMax

   # Load from LOQ data file spectrum 2 to 3. 
   ws = LoadISISNexus('LOQ49886.nxs',SpectrumMin=2,SpectrumMax=3) 
   
   print "The number of histograms (spectra) is: " + str(ws.getNumberHistograms())

.. testcleanup:: ExLoadSpectrumMinMax

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExLoadSpectrumMinMax
   
   The number of histograms (spectra) is: 2  

**Example - Using EntryNumber:** 

.. testcode:: ExLoadEntryNumber

   # Load first period of multiperiod POLREF data file 
   ws = LoadISISNexus('POLREF00004699.nxs', EntryNumber=1) 
   
   print "The number of histograms (spectra) is: " + str(ws.getNumberHistograms()) 

.. testcleanup:: ExLoadEntryNumber

   DeleteWorkspace(ws)
   
Output:

.. testoutput:: ExLoadEntryNumber
   
   The number of histograms (spectra) is: 246   
   
