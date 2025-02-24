# Implementing Multithreaded Merge Sort

Usually, when we think of sorting algorithms, we operate with O(nlogn) time 
complexity as the first sorting methods come to mind are **Quick Sort** and 
**Merge Sort**. Both of these take a recursive approach towards handling things. 

**Thought** : Can we mix recursion with multithreading and make things faster ?

**Preliminary Ideas**
1. As merge sort takes a divide and conquer approach, the sub-arrays which 
are to be further sorted individually during the divide step are not a shared 
resource.
2. Here, we can offload the execution to different threads without the 
requirement of any form of Mutex lock.
3. One problem that can arise is the resource constraint of the host machine 
one which this algorithm is being executed. We might run out of threads that 
the OS can offer if we are to carry out the algorithm for a huge array.
4. A potential solution to this is maintaining a [thread pool](https://www.youtube.com/watch?v=NgYS6mIUYmA&pp=ygULdGhyZWFkIHBvb2w%3D) of say 1000 threads.
5. If our thread pool is exhausted then we will not spin up more threads but fall 
back to recursion.

> [!NOTE]
> Implemented thread pools in Go to understand their working. Check [here](https://github.com/IAmRiteshKoushik/concurrency-in-depth/)

## Aim of the Experiment
Explore Merge Sort of 10 to the power 7 elements through merge-sort in 
non-parallel and parallel environments. 

## Results of the Experiment

#### 1. C++ Implementation Results by [Ritesh Koushik](https://github.com/IAmRiteshKoushik)
The following results were achieved
| Input Size | Single-Threaded (t1) | Multi-Threaded (t2) | Better Approach | Multi vs Single |
|------------|----------------------|---------------------|-----------------|-----------------|
| 1000       | 0.00113438s          | 0.00130357s         | Single-Threaded | 13% slower      |
| 10000      | 0.0136581s           | 0.0055255s          | Multi-Threaded  | 147% faster     |
| 100000     | 0.159913s            | 0.037813s           | Multi-Threaded  | 222% faster     |
| 1000000    | 1.62113s             | 0.310363s           | Multi-Threaded  | 422% faster     |
| 10000000   | 18.2698s             | 2.87343s            | Multi-Threaded  | 535% faster     |

> [!NOTE]
> *System specifications:* 2.1 GHz Clock Speed, 16GB RAM, AMD-Ryzen 5 processor,
Thread-cap at 35k, Arch Linux OS

#### 2. C Implementation Results by [Shreyas Jenner]()
Results incoming :construction:

#### 3. Java Implementation Results by [Kiran Rajeev]()
Results incoming :construction:

#### 4. Rust Implementation Results by [Praneeth V]()
Results incoming :construction:

#### 5. Go Implementation Results by [Unknown]()
Results incoming :construction:

#### 6. Haskell Implementation Results by [Unknown]()
Results incoming :construction:

#### 7. Scala Implementation Results by [Unknown]()
Results incoming :construction:
