# cpu-intro homework answers

## Q1
Command: `python3 process-run.py -l 5:10,5:10 -c`
Trace: P0 runs CPU, then issues I/O and blocks; system switches to P1. When I/O completes, switch back. I/O operations overlap.
Stats: Total Time 31, CPU Busy 10 (32.26%), IO Busy 20 (64.52%)
CPU utilization: 32.26%

## Q2
Command: `python3 process-run.py -l 5:10,5:10 --switch=SWITCH_ON_END -c`
Trace: System will NOT switch on I/O. Must finish P0 completely before starting P1. I/O cannot overlap.
Stats: Total Time 41, CPU Busy 10 (24.39%), IO Busy 20 (48.78%)
CPU utilization: 24.39%

## Q3
Command: `python3 process-run.py -l 5:10,5:10 --iodone=IO_RUN_IMMEDIATE -c`
Trace: When I/O finishes, the process immediately grabs CPU. Faster preemption than IO_RUN_LATER.
Stats: Total Time 21, CPU Busy 10 (47.62%), IO Busy 20 (95.24%)
CPU utilization: 47.62%

## Q4
Command: `python3 process-run.py -l 1:100,1:100 -c`
Trace: Two processes with tiny CPU burst and long I/O. I/O overlaps heavily.
Stats: Total Time 102, CPU Busy 2 (1.96%), IO Busy 100 (98.04%)
CPU utilization: 1.96%

## Q5
Command: `python3 process-run.py -l 1:100,1:100,1:100 -c`
Trace: Three processes with short CPU and long I/O. I/O operations overlap.
Stats: Total Time 103, CPU Busy 3 (2.91%), IO Busy 100 (97.09%)
CPU utilization: 2.91%

## Q6
Command: `python3 process-run.py -l 100:1,100:1 -c`
Trace: Two CPU-heavy jobs with minimal I/O. CPU rarely idle.
Stats: Total Time 202, CPU Busy 200 (99.01%), IO Busy 2 (0.99%)
CPU utilization: 99.01%
Conclusion: Use CPU-bound workloads (many CPU instructions, few I/O) to keep CPU nearly 100% busy.