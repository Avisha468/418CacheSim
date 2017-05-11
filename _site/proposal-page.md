
## 1. SUMMARY
> We are going to implement a Cache Simulator for analyzing how different Snooping-Based Cache Coherence Protocols
perform under various workloads.

## 2. BACKGROUND
> We have studied about different snooping based Cache Coherence Protocols in class. Whenever a processor wants
to read or write something, it tries to use its own cache to avoid having to go to the slow memory each time.
But, when we have multiple processors, we need to synchronize the caches, so that all processors have a coherent
view of memory. For this, one approach is to use a snooping cache, where each cache monitors the memory reads and
writes done by other caches and takes some action based on those requests. MSI is one simple choice but there
are other protocols too which offer different kinds of benefits under specific workloads.

## 3. THE CHALLENGE
> It would be interesting to implement various snooping cache based protocols and measure their performance
under different kinds of workloads. We wish to be able provide memory traces to our analyzer and by simulating
the various protocols, we will be able to determine the behavior of each protocol under varying circumstances.
This will help us gain a better understanding of how each protocol might have been implemented, and also what
the strong and weak points of each are.

## 4. RESOURCES
> We will be writing the code from scratch. And since this is an analysis project, we don’t need any additional
hardware. We will be able to run it our own laptops.
We still need to figure out how to obtain/generate the memory traces. Currently, we are thinking that we might
generate our own memory traces.

## 5. GOALS AND DELIVERABLES
> ### 5.1 Plan to achieve
> Cache Coherence Protocols <br>
> We plan to do the analysis based on comparisons between the following 4 protocols: <br>
> 1\. MSI <br>
> 2\. MESI <br>
> 3\. MOSI <br>
> 4\. MOESI <br>
>  <br> If time permits we will try to add a few more protocols to our analysis results: <br>
> 1\. Dragon <br>
> 2\. MESIF <br>
> 3\. Firefly <br>
>  <br> We will try to analyse how these protocols respond to various work loads. We will first begin with a fixed
system configuration (fixed cache size, set associativity, LRU replacement policy, number of processors) to
study the effects of different protocols. And further expand it to make the system configurable for better
analysis. <br>
>### 5.2 Memory Traces
> As mentioned earlier, we are still unsure of the kind of memory traces we will be using to compare the
various protocols. Generating manual traces seems favorable because we will be able to control the workload
properties. For example, are the accesses primarily reads, or is it write oriented, is just one of the cores
modifying or are all of them trying to modify. Generating workloads that mimic such different properties will
lead to more interesting comparisons between the protocols  <br>
>### 5.3 Metrics
> To compare the performance of the various protocols, we can think of two metrics.
Number of memory accesses - This includes all memory writebacks, flushes and reads. Memory accesses are slow,
hence a system that requires lower number of memory requests as compared to cache should give better performance.
This of course assumes that the interconnect used for cache coherence has much lower latency as compared to
memory. <br>
> Number of bus transactions - The total number of bus transactions that are needed for executing the memory
trace. The bus messages used in snooping cache coherence protocols have to be broadcasted so that every cache
controller can see them. This generates a lot of traffic on the interconnect. Depending on the the size of the
system and the available bandwidth, there is some latency associated with each bus transaction. We would prefer
a system that minimizes the number of bus transactions. <br>

## 6. PLATFORM CHOICE
> We will be using C++ as the programming language, as this project mainly involves being able to read the
memory traces from input files and dumping them into an output file. This can be easily done in C++.

## 7. SCHEDULE
> Apr 11 - Apr 17 - Implement a simple LRU cache for a single processor <br>
> Apr 18 - Apr 24 - Add support for cache coherence protocols - MSI, MESI <br>
> Apr 25 - May 01 - Add additional protocols - MOSI, MOESI, Dragon, Firefly, etc. <br>
> May 02 - May 07 - Generate different types of memory workloads and Perform Analysis <br>
> May 09 - May 11 - Project Presentation Preparation <br>
