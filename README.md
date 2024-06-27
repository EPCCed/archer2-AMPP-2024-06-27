<img src="./images/Archer2_logo.png" width="355" height="100"
align="left"> <img src="./images/epcc_logo.jpg" align="right"
width="133" height="100">

<br /><br /><br /><br /><br />

# ARCHER2 Advanced MPI course (June 2024)

[![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

<h3>David Henty EPCC: 27-28 June 2024 09:30 - 17:00 BST, online</h3>

This course is aimed at programmers seeking to deepen their
understanding of MPI and explore some of its more recent and advanced
features. We cover topics including exploiting shared-memory access
from MPI programs, communicator management and advanced use of
collectives. We also look at performance aspects such as which MPI
routines to use for scalability, MPI internal implementation issues
and overlapping communication and calculation.  Intended learning
outcomes

*  Understanding of how internal MPI implementation details affect performance
*  Techniques for overlapping communications and calculation
*  Familiarity with neighbourhood collective operations in MPI
*  Understanding of best practice for MPI+OpenMP programming
*  Knowledge of MPI memory models for RMA operations

<h3>Prerequisites</h3>

Attendees should be familiar with MPI programming in C, C++ or
Fortran, e.g. have attended the ARCHER2 MPI course.

<h3>Requirements</h3>

Participants must bring a laptop with a Mac, Linux, or Windows
operating system (not a tablet, Chromebook, etc.) that they have
administrative privileges on.

They are also required to abide by the [ARCHER2 Code of Conduct](https://www.archer2.ac.uk/about/policies/code-of-conduct.html).

<h3>Timetable (all times are in British Summer Time)</h3>

<p><blockquote>Although the start and end times will be as indicated below, this is a draft timetable based on
a previous run of the course and the details may change for this run.
</blockquote></p>

<p><blockquote>Unless otherwise indicated all material is Copyright
&copy; EPCC, The University of Edinburgh, and is only made available
for private study. </blockquote></p>

<h4>Day 1: Thursday 27th June</h4>

 *   09:30 - 09:40 <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/slides/L00-ARCHER2-Intro.pdf">ARCHER2 training</a>
 *   09:40 - 10:15 <a href="https://b.socrative.com/login/student/">MPI Quiz</a> ("Room Name" is: **HPCQUIZ**)
 *   10:15 - 11:00 <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/slides/MPI-Evolution.pdf">MPI History</a>
 *   11:00 - 11:30 Coffee
 *   11:30 - 13:00 <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/slides/MPI-Internals.pdf">Point-to-point Performance</a>
 *   13:00 - 14:00 Lunch
 *   14:00 - 15:30 <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/slides/MPI-Optimisation-ARCHER2.pdf">MPI Optimisations</a>
 *   15:30 - 16:00 Coffee
 *   16:00 - 17:00 <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/slides/AMPP_Neighbourhood.pdf">Neighbourhood Collectives</a>
 *   17:00 CLOSE

<h4>Day 2: Friday 28th June</h4>

 *   09:30 - 11:00 <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/slides/L06-MPIandOpenMP.pdf">MPI + OpenMP (i)<a>
 *   11:00 - 11:30 Coffee
 *   11:30 - 13:00 MPI + OpenMP (ii) - *same slide deck as above*
 *   13:00 - 14:00 Lunch
 *   14:00 - 14:30 <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/slides/IntroRMA.pdf">RMA Access in MPI</a>
 *   14:30 - 15:30 <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/slides/SharedMemoryRMA.pdf">New MPI shared-memory model</a>
 *   15:30 - 16:00 Coffee
 *   16:00 - 17:00 Finish Exercises
 *   17:00 CLOSE

<h3>Exercise Material</h3>

<p><blockquote>Unless otherwise indicated all material is Copyright &copy; EPCC, The University of Edinburgh, and is only made available for private study. </blockquote></p>

<h4>Day 1</h4>

SLURM batch scripts are set to run in the short queue and should work any time. However, on days when the course is running, we have
special reserved queues to guarantee fast turnaround.

The reserved queue for today is called `ta161_1261863`. To use this queue, change the `--qos` and `--reservation` lines to:
````
#SBATCH --qos=reservation
#SBATCH --reservation=ta161_1261863
````

 * <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/exercises/ARCHER2-pingpong.pdf">Ping-pong exercise sheet</a>
 * <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/exercises/pingpong.tar">Ping-pong source code</a>
   
 * Description of 3D halo-swapping benchmark is in this <a href="https://github.com/davidhenty/halobench/">README</a>
 * Download the code directly to ARCHER2 using: `git clone https://github.com/davidhenty/halobench`
   - compile with `Make -f makefile-archer2`
   - submit with `sbatch archer2.job`
 * Other things you could do with the halo swapping benchmark:
   - change the buffer size to be very small ( a few tens of bytes) or very large (bigger than the eager limit) to see if that affects the results;
   - run on different numbers of nodes.
 * Note that you will need to change the number of repetitions to get reasonable runtimes: many more for smaller messages, many fewer for larger messages. Each test needs to run for at least a few seconds to give reliable results.
   
 * The `halobench` program contains an example of using
   `MPI_Neighbor_alltoall()` to do pairwise swaps of data between neighbouring processes in a regular 3D grd
 * Tomorrows traffic modelling problem sheet also contains a final MPI exercise
  in Section 3 to replace point-to-point boundary swapping with neighbourhood collectives.
 
<h4>Day 2</h4>

The reserved queue for today is called `ta161_1261866`. To use this queue, change the `--qos` and `--reservation` lines to:
````
#SBATCH --qos=reservation
#SBATCH --reservation=ta161_1261866
````

 * <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/exercises/traffic-advmpi.pdf">Traffic modeling exercise sheet</a>
 * <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/exercises/traffic.tar">Traffic model source code and solutions (MPI / OpenMP)</a>
  * <a href="https://github.com/EPCCed/archer2-AMPP-2024-06-27/raw/main/exercises/traffic-RMA.tar">Traffic model source code and solutions (MPI RMA)</a>

---

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

