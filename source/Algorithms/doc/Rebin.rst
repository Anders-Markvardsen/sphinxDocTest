Usage
-----

**Example - simple rebin of a histogram workspace:**  

.. testcode:: ExHistSimple

   # create histogram workspace
   dataX = [0,1,2,3,4,5,6,7,8,9] # or use dataX=range(0,10) 
   dataY = [1,1,1,1,1,1,1,1,1] # or use dataY=[1]*9 
   ws = CreateWorkspace(dataX, dataY)
   
   # rebin from min to max with size bin = 2
   ws = Rebin(ws, 2)   
   
   print "The rebinned X values are: " + str(ws.readX(0))  
   print "The rebinned Y values are: " + str(ws.readY(0)) 

.. testcleanup:: ExHistSimple

   DeleteWorkspace(ws)

Output:

.. testoutput:: ExHistSimple
   
   The rebinned X values are: [ 0.  2.  4.  6.  8.  9.]
   The rebinned Y values are: [ 2.  2.  2.  2.  1.]

**Example - logarithmic rebinning:**   

.. testcode:: ExHistLog

   # create histogram workspace
   dataX = [1,2,3,4,5,6,7,8,9,10] # or use dataX=range(1,11) 
   dataY = [1,2,3,4,5,6,7,8,9] # or use dataY=range(1,10)
   ws = CreateWorkspace(dataX, dataY)
   
   # rebin from min to max with logarithmic bins of 0.5
   ws = Rebin(ws, -0.5)   
   
   print "The 2nd and 3rd rebinned X values are: " + str(ws.readX(0)[1:3])    

.. testcleanup:: ExHistLog

   DeleteWorkspace(ws)

Output:

.. testoutput:: ExHistLog
   
   The 2nd and 3rd rebinned X values are: [ 1.5   2.25]   

**Example - custom two regions rebinning:**
   
.. testcode:: ExHistCustom

   # create histogram workspace
   dataX = [0,1,2,3,4,5,6,7,8,9] # or use dataX=range(0,10) 
   dataY = [0,1,2,3,4,5,6,7,8] # or use dataY=range(0,9)
   ws = CreateWorkspace(dataX, dataY)
   
   # rebin from 0 to 3 in steps of 2 and from 3 to 9 in steps of 3
   ws = Rebin(ws, "1,2,3,3,9")   
   
   print "The rebinned X values are: " + str(ws.readX(0))  

.. testcleanup:: ExHistCustom

   DeleteWorkspace(ws)

Output:

.. testoutput:: ExHistCustom
   
   The rebinned X values are: [ 1.  3.  6.  9.]   

**Example - use option FullBinsOnly:**
   
.. testcode:: ExHistFullBinsOnly

   # create histogram workspace
   dataX = [0,1,2,3,4,5,6,7,8,9] # or use dataX=range(0,10) 
   dataY = [1,1,1,1,1,1,1,1,1] # or use dataY=[1]*9
   ws = CreateWorkspace(dataX, dataY)
   
   # rebin from min to max with size bin = 2
   ws = Rebin(ws, 2, FullBinsOnly=True)   
   
   print "The rebinned X values are: " + str(ws.readX(0))  
   print "The rebinned Y values are: " + str(ws.readY(0))   

.. testcleanup:: ExHistFullBinsOnly

   DeleteWorkspace(ws)

Output:

.. testoutput:: ExHistFullBinsOnly
   
   The rebinned X values are: [ 0.  2.  4.  6.  8.]
   The rebinned Y values are: [ 2.  2.  2.  2.]

**Example - use option PreserveEvents:**
   
.. testcode:: ExEventRebin

   # create some event workspace
   ws = CreateSampleWorkspace(WorkspaceType="Event")

   print "What type is the workspace before 1st rebin: " + str(type(ws)) 
   # rebin from min to max with size bin = 2 preserving event workspace (default behaviour)
   ws = Rebin(ws, 2)   
   print "What type is the workspace after 1st rebin: " + str(type(ws)) 
   ws = Rebin(ws, 2, PreserveEvents=False)   
   print "What type is the workspace after 2nd rebin: " + str(type(ws)) 
   # note you can also check the type of a workspace using: print isinstance(ws, IEventWorkspace)   

.. testcleanup:: ExEventRebin

   DeleteWorkspace(ws)

Output:

.. testoutput:: ExEventRebin
   
   What type is the workspace before 1st rebin: <class 'mantid.api._api.IEventWorkspace'>
   What type is the workspace after 1st rebin: <class 'mantid.api._api.IEventWorkspace'>
   What type is the workspace after 2nd rebin: <class 'mantid.api._api.MatrixWorkspace'>     

