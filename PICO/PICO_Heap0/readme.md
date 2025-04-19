# Challenge Name: Heap 0

## Challenge Overview

This challenge explores heap-based vulnerabilities, specifically heap overflows, and demonstrates how they can be exploited to manipulate program execution. The objective was to analyze the binary and exploit an input vulnerability to retrieve the flag.

## Steps to Solve

1. **Understanding the Code and Memory Allocation**

   - The program dynamically allocates memory for `input_data` (5 bytes) and `safe_var` (5 bytes) using `malloc()`.
   - `safe_var` is initialized to `"bico"`, and `input_data` is initialized to `"pico"`.
   - The `write_buffer()` function uses `scanf("%s", input_data);`, which does not restrict input length, allowing overflow into adjacent memory.

2. **Identifying the Vulnerability**

   - Since `safe_var` is allocated immediately after `input_data`, an overflow in `input_data` can overwrite `safe_var`.
   - The `check_win()` function checks if `safe_var` is NOT `"bico"`. If modified, it prints the flag.

3. **Exploiting the Overflow**
   - By inputting a long enough string (`AAAAAAAAAAAAAAAAAAAAAAAAAAApico`), I overwrote `safe_var`, causing `check_win()` to succeed and print the flag.

## Conclusion

This challenge demonstrated a classic heap-based overflow vulnerability where an unbounded `scanf()` call allowed modifying adjacent memory. By understanding heap memory allocation and experimenting with input sizes, I successfully manipulated `safe_var` and retrieved the flag.

## Key Takeaways

- Heap overflows occur when dynamically allocated memory is written beyond its boundaries.
- `scanf("%s", input)` is dangerous without length restrictions (`%s` should be avoided in favor of `fgets()` or `%Ns`).
- Memory layout knowledge is crucial in exploiting heap-based vulnerabilities.
- Testing different input sizes and monitoring heap changes can reveal unintended behaviors.
