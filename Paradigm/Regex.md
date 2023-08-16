## Regex

Regular Expressions are a powerful tool used in programming for searching, manipulating, and editing strings. They provide a concise and flexible means for identifying strings of text that follow a particular pattern or set of rules.

### Structure
A regular expression is a sequence of characters that forms a search pattern. It can be used for various string operations, such as validation, search, replacement, and splitting. Here's a breakdown of some common components:

- Literals: Regular characters like letters or numbers that match themselves exactly.
- Metacharacters: Special characters that have unique meanings, such as ., *, +, ?, ^, $, and others.
- Character Classes: Represented by square brackets [], they can match any character within the class. For example, [a-z] matches any lowercase letter.
- Quantifiers: Indicate how many instances of a character or group must be present for a match. Examples include * (0 or more), + (1 or more), and {n} (exactly n times).
- Groups and Capturing: Parentheses () are used to group parts of the expression and capture the text matched.

### Examples
Here are a few examples to illustrate how regex might be used:

- Email Validation: A simple regex pattern to match email addresses might be \w+@\w+\.\w+.
- Finding Dates: A pattern like \d{2}/\d{2}/\d{4} could match dates in the format MM/DD/YYYY.
- Replacing Text: You can use regex with replacement functions to change specific patterns in a string.

- Languages and Tools
Most modern programming languages, including JavaScript, Python, Java, and others, support regex either natively or through libraries. Many text editors and development tools also provide regex-based search and replace functionality.

### Advantages
- Flexibility: Regex provides a powerful and flexible way to perform complex string manipulations.
- Compactness: Complex patterns and rules can be represented concisely.

### Disadvantages
- Readability: Complex regex patterns can become difficult to read and maintain.
- Performance: Inefficient regex patterns might lead to performance issues in some scenarios.

  Reference: https://jex.im/regulex/#!flags=&re=%5E(a%7Cb)*%3F%24