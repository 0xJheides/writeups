# picoCTF SSTI 1 Writeup

## Challenge Description
The challenge provided a web application where users could submit announcements. The hint suggested that the website used templating, which hinted at potential **Server-Side Template Injection (SSTI)** vulnerabilities.

## Approach

### Step 1: Identifying the Vulnerability
Since the challenge mentioned templating, I suspected that the application might be using a Python-based templating engine like Jinja2. SSTI vulnerabilities occur when user input is directly evaluated in a server-side template, allowing arbitrary code execution.

To confirm SSTI, I tested by submitting:
```jinja
{{ 7*7 }}
```
If the output displayed `49`, it would confirm that the server was evaluating user input as Jinja2 templates.

### Step 2: Exploiting the Vulnerability
Once confirmed, I proceeded to execute arbitrary system commands using Python's `os` module. The payload I used was:
```jinja
{{ request.application.__globals__.__builtins__.__import__('os').popen('cat flag').read() }}
```
This payload works as follows:
1. `request.application` gives access to the Flask application.
2. `__globals__` accesses the global variables.
3. `__builtins__` provides built-in Python functions.
4. `__import__('os')` imports the `os` module.
5. `popen('cat flag').read()` executes the `cat flag` command, which reads the flag file.

### Step 3: Retrieving the Flag
Upon submitting this payload in the web input field, the server executed the command and returned the flag.

## Lessons Learned
- **Understanding SSTI**: This challenge reinforced how server-side template engines can be exploited if user input is not sanitized.
- **Jinja2 Exploitation**: Learning how to escalate SSTI into Remote Code Execution (RCE) using Python’s built-in functions.
- **Secure Coding Practices**: Always sanitize user input and avoid rendering user-supplied data directly in templates.

## Mitigation Strategies
To prevent SSTI vulnerabilities in Flask applications:
- Use **strict input validation** and sanitize user input.
- Avoid using `{{ user_input }}` directly in templates.
- Disable template auto-escaping where necessary.
- Use Jinja2's **sandboxing** features to restrict execution scope.

This challenge was a great way to understand how SSTI can lead to critical security vulnerabilities!

