# 1 Parallel loops

# 2 Loop scheduling
http://www.inf.ufsc.br/~bosco.sobral/ensino/ine5645/OpenMP_Dynamic_Scheduling.pdf

By default, OpenMP statically assigns loop iterations to threads. When the
parallel for block is entered, it assigns each thread the set of loop iterations it
is to execute

A static schedule can be non-optimal, however. This is the case when the
different iterations take different amounts of time. This is true of the following
program, in which each loop iteration sleeps for a number of seconds equal to
the iteration number:

# 3 PIPELINE 1
Thread: 2 Reading ...
Thread: 2 processing  i,j 0,6
Thread: 1 processing  i,j 0,3
Thread: 3 processing  i,j 0,8
Thread: 0 processing  i,j 0,0
Thread: 2 processing  i,j 0,7
Thread: 1 processing  i,j 0,4
Thread: 3 processing  i,j 0,9
Thread: 0 processing  i,j 0,1
Thread: 1 processing  i,j 0,5
Thread: 0 processing  i,j 0,2
Thread: 0 Writing ...
Thread: 0 Reading ...
Thread: 0 processing  i,j 1,0
Thread: 1 processing  i,j 1,3
Thread: 2 processing  i,j 1,6
Thread: 3 processing  i,j 1,8
Thread: 1 processing  i,j 1,4
Thread: 2 processing  i,j 1,7
Thread: 3 processing  i,j 1,9
Thread: 0 processing  i,j 1,1
Thread: 0 processing  i,j 1,2
Thread: 1 processing  i,j 1,5
Thread: 0 Writing ...
Thread: 0 Reading ...
Thread: 0 processing  i,j 2,0
Thread: 1 processing  i,j 2,3
Thread: 2 processing  i,j 2,6
Thread: 3 processing  i,j 2,8
Thread: 3 processing  i,j 2,9
Thread: 1 processing  i,j 2,4
Thread: 2 processing  i,j 2,7
Thread: 0 processing  i,j 2,1
Thread: 1 processing  i,j 2,5
Thread: 0 processing  i,j 2,2
Thread: 1 Writing ...
Thread: 1 Reading ...
Thread: 1 processing  i,j 3,3
Thread: 0 processing  i,j 3,0
Thread: 3 processing  i,j 3,8
Thread: 2 processing  i,j 3,6
Thread: 1 processing  i,j 3,4
Thread: 3 processing  i,j 3,9
Thread: 0 processing  i,j 3,1
Thread: 2 processing  i,j 3,7
Thread: 1 processing  i,j 3,5
Thread: 0 processing  i,j 3,2
Thread: 0 Writing ...
Time: 56 seconds.
# 4 PIPELINE 2
Thread: 1 Reading ...0
Thread: 1 Reading ...1
Thread: 3 processing  i,j 0,0
Thread: 0 processing  i,j 0,1
Thread: 2 processing  i,j 0,2
Thread: 0 processing  i,j 0,3
Thread: 2 processing  i,j 0,5
Thread: 3 processing  i,j 0,4
Thread: 1 processing  i,j 0,6
Thread: 0 processing  i,j 0,7
Thread: 3 processing  i,j 0,8
Thread: 2 processing  i,j 0,9
Thread: Thread: 1 Writing ...
3 Reading ...2
Thread: 0 processing  i,j 1,0
Thread: 2 processing  i,j 1,1
Thread: 2 processing  i,j 1,2
Thread: 0 processing  i,j 1,3
Thread: 1 processing  i,j 1,4
Thread: 3 processing  i,j 1,5
Thread: 2 processing  i,j 1,6
Thread: 0 processing  i,j 1,7
Thread: 1 processing  i,j 1,8
Thread: 3 processing  i,j 1,9
Thread: 3 Writing ...
Thread: 1 Reading ...3
Thread: 2 processing  i,j 2,0
Thread: 0 processing  i,j 2,1
Thread: 2 processing  i,j 2,2
Thread: 0 processing  i,j 2,3
Thread: 0 processing  i,j 2,4
Thread: 1 processing  i,j 2,7
Thread: 3 processing  i,j 2,6
Thread: 2 processing  i,j 2,5
Thread: 2 processing  i,j 2,9
Thread: 1 processing  i,j 2,8
Thread: 2 Writing ...
Thread: 1 Reading ...4
Thread: 0 processing  i,j 3,0
Thread: 3 processing  i,j 3,1
Thread: 0 processing  i,j 3,2
Thread: 3 processing  i,j 3,3
Thread: 3 processing  i,j 3,4
Thread: 1 processing  i,j 3,6
Thread: 2 processing  i,j 3,7
Thread: 0 processing  i,j 3,5
Thread: 1 processing  i,j 3,8
Thread: 0 processing  i,j 3,9
Thread: 1 Writing ...
Time: 38 seconds.   

# 5 Functional parallelism

# 6 Implemente pipeline 2 with tasks

# 7 Analyze the Quick Sort parallel code