# A2. 1D Stencil

Due Date: 10/7 at midnight

## Instructions

Implement the one dimensional stencil code discussed in class (Lecture 2.2)
- use main.cu as skeleton
- the code from the slides is a starting point
- think about and correct for edge cases in the calculation
- include error checking

Test
- How to verify correctness?
- Simple case:
  - input: All 1's [1, 1, ... 1]
  - output: [4, 5, 6, 7, 7, ... 7, 6, 5, 4]

## Tips / Reminders / Hints

CUDA Memory Allocation Calls:
- `cudaMallocManaged`
- `cudaFree`

Use `cudaDeviceSynchronize` to wait for results

Don't forget to set constants  e.g.`#define BLOCK SIZE 256`

Use `stencil_1d<<<blocks, thdsPerBlk>>>(in, out)` to launch the cuda kernel on the GPU

For error checking,
`printf("%s\n", cudaGetErrorString(cudaGetLastError()));`
will return the last CUDA error and print it as a string

You can check to make sure that you code is not accessing unallocated memory
by utilizing NVIDIA's memory sanitizer tool.
You can run it ok `keroppi` using the following line.
```sh
compute-sanitizer --tool memcheck ./your_cuda_executable_not_source
```

Remember to make may small commits as you go.
You can look at the git tutorials on Moodle for help.

## Submission

1. Uploaded code (`main.cu`)

2. Additional test cases/data.
   This could be in the form of a txt file, json, code, etc.

3. Short reflection (text, Markdown, LaTeX, Word/Google Doc, etc)
- Why do we need `__synchtreads()`?
- What went well with this assignment?
- What was difficult?
- How would you approach differently?
- Anything else you want me to know?

## Extras

Benchmark your implementation using `nvprof` (or something similar)
with and without utilizing shared memory.
What is the obsereved difference?

Implement a 2D Stencil (sometimes called Jacobi Stencil)
- 4 pt (N, E, S, W)
- 9 pt (N, NE, E, SE, S, SW, W, NW)
