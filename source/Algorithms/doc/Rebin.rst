Usage
-----

**Example - simple rebin histogram workspace:**  

.. testcode:: ExHistSimple

   # create histogram workspace
   dataX = [0,1,2,3,4,5,6,7,8,9] # or use dataX=range(0,10) 
   dataY = [1,1,1,1,1,1,1,1,1] # or use dataY=[1]*9 
   ws = CreateWorkspace(dataX, dataY)
   
   # rebin from min to max with size bin = 2
   ws = Rebin(ws, 2)   
   
   print "The rebinned X values are: " + str(ws.readX(0))   

.. testcleanup:: ExHistSimple

   DeleteWorkspace(ws)

Output:

.. testoutput:: ExHistSimple
   
   The rebinned X values are: [ 0.  2.  4.  6.  8.  9.]

**Example - logarithmic rebinning:**   

.. testcode:: ExHistLog

   # create histogram workspace
   dataX = [1,2,3,4,5,6,7,8,9,10] # or use dataX=range(1,11) 
   dataY = [1,2,3,4,5,6,7,8,9] # or use dataY=range(1,10)
   ws = CreateWorkspace(dataX, dataY)
   
   # rebin from min to max with logarithmic bins of 0.5
   ws = Rebin(ws, -0.5)   
   
   # print out rebinned x values
   print ws.readX(0)   

.. testcleanup:: ExHistLog

   DeleteWorkspace(ws)
   
.. testoutput:: ExHistLog
   
   [  1.        1.5       2.25      3.375     5.0625    7.59375  10.     ]   

Example - custom rebin histogram workspace:
   
.. testcode:: ExHistCustom

   # create histogram workspace
   dataX = [0,1,2,3,4,5,6,7,8,9] # or use dataX=range(0,10) 
   dataY = [0,1,2,3,4,5,6,7,8] # or use dataY=range(0,9)
   ws = CreateWorkspace(dataX, dataY)
   
   # rebin from 0 to 3 in steps of 2 and from 3 to 9 in steps of 3
   ws = Rebin(ws, "1,2,3,3,9")   
   
   # print out rebinned x values
   print ws.readX(0)   

.. testcleanup:: ExHistCustom

   DeleteWorkspace(ws)
   
.. testoutput:: ExHistCustom
   :hide:
   
   [ 1.  3.  6.  9.]   

Example - use option FullBinsOnly:
   
.. testcode:: ExHistFullBinsOnly

   # create histogram workspace
   dataX = [0,1,2,3,4,5,6,7,8,9] # or use dataX=range(0,10) 
   dataY = [0,1,2,3,4,5,6,7,8] # or use dataY=range(0,9)
   ws = CreateWorkspace(dataX, dataY)
   
   # rebin from min to max with size bin = 2
   ws = Rebin(ws, 2, FullBinsOnly=True)   
   
   # print out rebinned x values
   print ws.readX(0)   

.. testcleanup:: ExHistFullBinsOnly

   DeleteWorkspace(ws)
   
.. testoutput:: ExHistFullBinsOnly
   :hide:
   
   [ 0.  2.  4.  6.  8.]


