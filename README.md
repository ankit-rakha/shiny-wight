shiny-wight
===========

:speech_balloon: all you need to know about HP Vertica and Cloudera distribution of Hadoop


Vertica - 360 degree view
===========
 
We use a bash script that runs against vertica database and give us all the necessary statistics to debug an issue or gain insights on performance.
 
Usage:
1) Download the script or copy the contents of the script and save it as vsql_queries.sh
2) Make it executable: chmod +x vsql_queries.sh reads from standard input or command line
3) Run the script: time ./vsql_queries.sh username password > log.out 2> log_error.out
 
Please note we are displaying an example output only below. For comprehensive results, please check log.out and for any errors log_error.out.

Example output:
 
==> QUERY 1. Checking Vertica Version:
 
              VERSION
------------------------------------
 Vertica Analytic Database v7.0.0-1
(1 row)
 
==> QUERY 2. CPU USAGE
 
       node_name        |     start_time      |      end_time       | average_cpu_usage_percent
------------------------+---------------------+---------------------+---------------------------
 v_verticatest_node0001 | 2014-05-02 03:47:00 | 2014-05-02 03:48:00 |                     24.94
 v_verticatest_node0001 | 2014-05-02 18:17:00 | 2014-05-02 18:18:00 |                     24.62
 v_verticatest_node0001 | 2014-05-02 18:16:00 | 2014-05-02 18:17:00 |                     21.89
 v_verticatest_node0001 | 2014-05-02 03:51:00 | 2014-05-02 03:52:00 |                     20.61
 v_verticatest_node0001 | 2014-05-02 03:46:00 | 2014-05-02 03:47:00 |                     17.79
 v_verticatest_node0001 | 2014-05-07 06:11:00 | 2014-05-07 06:12:00 |                     17.08
 v_verticatest_node0001 | 2014-05-02 03:52:00 | 2014-05-02 03:53:00 |                     15.69
 v_verticatest_node0003 | 2014-05-02 03:47:00 | 2014-05-02 03:48:00 |                     13.86
 v_verticatest_node0001 | 2014-05-07 08:10:00 | 2014-05-07 08:11:00 |                     13.38
 v_verticatest_node0002 | 2014-05-02 03:47:00 | 2014-05-02 03:48:00 |                     10.96
 
==> QUERY 3. NETWORK USAGE I
 
       node_name        |     start_time      |      end_time       | tx_kb  | rx_kb
------------------------+---------------------+---------------------+--------+--------
 v_verticatest_node0003 | 2014-05-07 15:05:00 | 2014-05-07 15:06:00 | 512.07 | 788.99
 v_verticatest_node0002 | 2014-05-07 15:05:00 | 2014-05-07 15:06:00 | 515.69 | 786.77
 v_verticatest_node0003 | 2014-05-07 14:53:00 | 2014-05-07 14:54:00 | 489.73 | 753.47
 v_verticatest_node0002 | 2014-05-07 14:53:00 | 2014-05-07 14:54:00 | 491.85 | 751.53
 v_verticatest_node0003 | 2014-05-06 20:09:00 | 2014-05-06 20:10:00 | 433.16 | 697.56
 v_verticatest_node0003 | 2014-05-06 19:48:00 | 2014-05-06 19:49:00 | 433.73 | 697.45
 v_verticatest_node0002 | 2014-05-06 20:09:00 | 2014-05-06 20:10:00 | 435.18 | 695.77
 v_verticatest_node0002 | 2014-05-06 19:48:00 | 2014-05-06 19:49:00 | 435.28 | 695.64
 v_verticatest_node0003 | 2014-05-06 18:01:00 | 2014-05-06 18:02:00 | 430.25 | 689.13
 v_verticatest_node0003 | 2014-05-06 18:09:00 | 2014-05-06 18:10:00 | 430.04 | 688.09
 
==> QUERY 4. MaxClientSessions
 
 CURRENT_VALUE
---------------
 50
(1 row)
 
==> QUERY 5. LICENSE INFO.
 
                          DISPLAY_LICENSE
-------------------------------------------------------------------
 Vertica Community Edition
2011-11-22
Perpetual
0
1TB CE Nodes 3
 
==> QUERY 6. Check K-Safety
 
 DESIGNED_FAULT_TOLERANCE | CURRENT_FAULT_TOLERANCE
--------------------------+-------------------------
                        1 |                       1
(1 row)
 
==> QUERY 7. ROLES
 
      name       | assigned_roles
-----------------+----------------
 public          |
 dbduser         |
 dbadmin         | dbduser*
 pseudosuperuser | dbadmin*
 master          |
 admin           |
 ops             |
 writer          |
 reader          |
(9 rows)
 
==> QUERY 8. critical nodes
 
 node_id | node_name
---------+-----------
(0 rows)
 

