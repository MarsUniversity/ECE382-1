# L21 Assignment - Moving Average

## Moving Average

- Write a function that computes the "moving average" for a stream of data points it is receiving.
    - A moving average computes the average of the most recent `N_AVG_SAMPLES` points.
    - Initialize values in the samples array to be 0.
    - For example: (`N_AVG_SAMPLES` = 2), sample stream = (2, 4, 6, 8).
        - Starting point: average [0, 0]
            - Average is 0
        - First sample: average [0, 2]
            - Average is 1
        - Second sample: average [2, 4]
            - Average is 3
        - Third sample: average [4, 6]
            - Average is 5
        - Fourth sample: average [6, 8]
            - Average is 7
    - Use the following data streams to test your moving average function:
        - Test these streams with (`N_AVG_SAMPLES` = 2) and (`N_AVG_SAMPLES` = 4).
        - (45, 42, 41, 40, 43, 45, 46, 47, 49, 45)
        - (174, 162, 149, 85, 130, 149, 153, 164, 169, 173)
        - Note: you can store the "moving average" values into an array to make your simulation and verification stages simpler.
        - Additional Note:
            - You should treat the stream values as coming in one at a time
            - You don't know the value of future samples in advance!
            - That means your implementation shouldn't be dependent on passing in an array of samples!
            - Look at [my header file](moving_average_h.html) if you're having trouble visualizing an interface
- Write two other functions that compute the maximum and minimum values in a given array.  You can "terminate" (last element is some predefined constant to simplify your loop) or pass in the length of the array as a parameter.
- Write another function that computes the range of values in an array.
- You *may* use the following function to generate a new pseudo random number each time it is called.  You can use this as your input stream to test your other functions.  This is based on the method described in "The C Programming Language" by Kernighan and Ritchie.
```
unsigned long int rand(void)
{
    static unsigned long int random_seed = INITIAL_RANDOM_SEED;     \\ You need to define INITIAL_RANDOM_SEED!
    random_seed = random_seed * 1103515245 + 12345;
    return (unsigned long int)(random_seed / 65536) % 32768;
}
```

## Turn-In Requirements (Bitbucket)

- Source code files (`main.c`, header, and implementation).
- Simulator screenshots.
- Answers to the following questions in readme.md file:
    - What data type did you choose for your arrays?  Why?
    - How did you test each of your functions to verify they were functioning correctly?

## Hints

**[Here is my moving_average.h!](moving_average_h.html)**
