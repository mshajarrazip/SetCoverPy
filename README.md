SetCoverPy
=============

    SetCoverPy
    ----------

    SetCoverPy is developed and maintained by Guangtun Ben Zhu, 
    It is designed to find an (near-)optimal solution to the set cover problem (SCP) as 
    fast as possible. It employs an iterative heuristic approximation method, combining 
    the greedy and Lagrangian relaxation algorithms. It also includes a few useful tools
    for a quick chi-squared fitting given two vectors with measurement errors.

    For the standard tests (4,5,6, A-H instances from Beasley's OR Library), the code yields 
    solutions that are 96%-100% optimal (see scp_BeasleyOR_test_results.txt). 

    As all the codes, this code can always be improved and any feedback will be greatly appreciated.

    And here are some small tips using this SCP solver:
      - If you are not satisfied with the solution, just run it a few more times 
        (when your servers are free) and select the best solution.
        Or you can also select a larger maxiters at the instantiation:

        >> g = setcover.SetCover(a_matrix, cost, maxiters=100)

      - If you are really really lazy and don't want to wait for a near-optimal solution,
        you can just run the greedy solver, which takes no time:

        >> g.greedy()


    Test data
    ----------

    Test data provided with this package only includes on instance from Beasley's OR Library.
    The rest of the Beasley's OR Library can be retrieved here:
      http://www.pha.jhu.edu/~gz323/scp/BeasleyOR/  

    The Archetype test data can be retrieved here:
      http://www.pha.jhu.edu/~gz323/scp/GalaxyTest/

    Run the test
    -------------
    Input: 
        -- a_matrix[mrows, ncols], the binary relationship matrix
           a_matrix[irow, jcol] = True if jcol covers irow
        -- cost[ncols], the cost of columns. 
           I recommend using normalized cost: cost/median(cost)

    Instantiation: 
        >> a_matrix = np.load('./BeasleyOR/scpa4_matrix.npy')
        >> cost = np.load('./BeasleyOR/scpa4_cost.npy')
        >> g = setcover.SetCover(a_matrix, cost)
    Run the solver: 
        >> solution, time_used = g.SolveSCP()
           ......
           Final Best solution: 234
           Took 1.287 minutes to reach current solution.
           (Results of course will depend on the configuration of your machine)

    Output:
        -- g.s, the (near-optimal) minimal set of columns, a binary 1D array, 
           g.s[jcol] = True if jcol is in the solution
        -- g.total_cost, the total cost of the (near-optimal) minimal set of columns

Dependencies
=============
    Python >3.5.1
    Numpy >1.11.0
    Scipy >0.17.0

    I did not fully test the code on earlier versions.

Contact Me
=============
    As all the codes, this code can always be improved and any feedback will be greatly appreciated.


    Sincerely,
    Guangtun Ben Zhu