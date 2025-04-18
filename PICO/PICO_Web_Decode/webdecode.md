# Challenge Name: WebDecode

## Challenge Overview

This challenge tests the ability to inspect web elements and decode hidden information embedded in a webpage. By using web inspection tools, the goal was to find and decode a hidden flag.

## Steps to Solve

1. **Inspecting the Webpage**

   - Opened the browser’s Developer Tools (Inspect Element) to analyze the webpage source.
   - Searched for any suspicious elements or hidden attributes.

2. **Finding the Hidden Data**

   - Found a suspicious line in the HTML:
     ```html
     <section
       class="about"
       notify_true="cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMDJjZGNiNTl9"
     ></section>
     ```
   - The `notify_true` attribute contained an encoded string.

3. **Decoding the String**
   - Copied the encoded value and used CyberChef to test different decoding methods.
   - Found that it was Base64 encoded.
   - Decoded the string to reveal the flag: `picoCTF{web_succ3ssfully_d3c0ded_02cdcb59}`.

## Conclusion

This challenge demonstrated the importance of web inspection tools in security challenges. By analyzing HTML attributes and decoding encoded strings, I successfully retrieved the flag.

## Key Takeaways

- Web inspection tools can reveal hidden data within webpages.
- Suspicious attributes in HTML elements can often store encoded or obfuscated information.
- CyberChef is a powerful tool for testing and decoding various encoding algorithms.
- Base64 encoding is commonly used to obscure data, but it is easily reversible.
