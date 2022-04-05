# OpenMP Exercises

## Exercise 1

Wasn't working.

## Exercise 2

*pragma_omp_critical* identifies section of code that must be executed by a single thread at a time.

## Exercise 3

57 seconds.

## Exercise 4

Took only 38 seconds, which is faster than pipeline1.

We need private (i) so that each thread on a team of threas has its own local copy of the private variable. We don't put NOWAIT in (1) because we need to wait for the file to continue working.

NOWAIT means that we avoid the implied barrier at the end of the loop construct. 

Dynamic is used to give tasks to different threads dynamically; once one ends, you give it another.

*dynamic* = 38 seconds | *static* = 46 seconds.

## Exercise 5

### a)

Time = 16 seconds, e = 31. Needs taskwait, without taskwait, e = 0.

### b)

Time of 16 seconds. e = 31. Doesn't need taskwait.

### c)

Time is 18 seconds. e = 31.
