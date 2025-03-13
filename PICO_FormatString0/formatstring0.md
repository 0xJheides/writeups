# Challenge Name: Format String 0

## Challenge Overview

This challenge focuses on format string vulnerabilities, which occur when user input is improperly handled in formatted output functions like `printf()`. The goal was to exploit this vulnerability to retrieve the flag.

## Steps to Solve

1. **Analyzing the Code**

   - The program serves two customers, Patrick and Bob, and takes user input for burger recommendations.
   - `printf(choice1);` and `printf(choice2);` are used without format specifiers, making them vulnerable to format string attacks.
   - If the output length for Patrick’s input exceeds a threshold, the program moves to Bob.
   - Bob’s input is directly printed using `printf(choice2);`, making it exploitable.

2. **Exploiting the Vulnerability**
   - Entering `Gr%114d_Cheese` for Patrick’s order allowed progression to Bob.
   - Entering `Cla%sic_Che%s%steak` triggered a format string vulnerability, causing unintended behavior and leaking the flag.

## Conclusion

This challenge demonstrated how improperly formatted output functions can lead to format string vulnerabilities. By exploiting these vulnerabilities, I was able to manipulate the program's behavior and retrieve the flag.

## Key Takeaways

- Format string vulnerabilities occur when `printf()` is used with user input directly.
- `%s`, `%x`, and other format specifiers can be used to leak memory or manipulate execution.
- Proper input validation and using `printf("%s", input)` instead of `printf(input)` can prevent such vulnerabilities.
- Sometimes, even accidental inputs can lead to successful exploits.
