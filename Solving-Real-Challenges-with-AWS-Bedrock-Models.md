# 1- Introduction: The Importance of Output Format
When working with large language models (LLMs), getting the output in the exact format you need is essential. Whether you are building a chatbot, generating reports, or automating workflows, how the model structures its response can make or break your application. If the output is not in the proper format, you may need to spend extra time cleaning or reformatting it, or worse, your application might not work as expected.

In this lesson, I will show you advanced techniques for guiding LLMs to produce outputs in the precise format you want. You may already know that providing examples in your prompt helps, but there are more powerful ways to use examples. 

We will focus on two key techniques: 

1. using placeholders in your examples
2. and explaining your examples to the model.


## Using Placeholders in Prompt Examples
Let’s start by understanding what placeholders are and how they can help.

A placeholder is a generic marker in your example to show where specific information should go. This makes your example more flexible and helps the LLM understand the structure you want rather than copying your exact words.

Suppose you want the LLM to list use cases for LLMs in a specific format. If you give one example, the model might copy your content too closely. Also, you will need to spend some time developing a proper example. Instead, you can use placeholders to show the structure.

```Plain text
Please provide me with 5 LLM use cases.

Use the format below:
1. Use case 1: <Short name>
<Description>

Here is an example:
<Example>

2. Use case 2: <Short name>
<Description>

Here is an example:
<Example>
```

By using `<Short name>`, `<Description>`, `<Example>`, you show the model exactly where to put each piece of information. This helps the LLM understand the structure you want, and it is less likely to copy your example word-for-word.

Placeholders make your prompt more flexible and clear. Following your structure, the model sees the pattern and fills in the blanks with new content.

## Enhancing Examples with Explanations: Part 1

Now, let’s talk about another powerful technique: `explaining your examples`.

<u>When you provide an example in your prompt, you can briefly explain why the example is correct or what makes it a good answer. This helps the LLM understand the format and the reasoning behind it</u>.

Let’s build this idea step by step.

Suppose you want the LLM to answer only `True` or `False` to a set of statements. You might start with a simple instruction:

```Plain text
I will send you statements. Your goal is to answer each one with `True` or `False`.
```

But sometimes, the model might add extra words or explanations. To make your intent more straightforward, you can add constraints and an example:

```Plain text
# Ask
I will send you statements. Your goal is to answer each one with `True` or `False`.

# Constraints
- Answer _only_ with one word; don't include anything else

# Examples
Statement: `LLMs can be trusted when consulting about health and medicine`
Your answer: False
```


## Enhancing Examples with Explanations: Part 2
This is better, but you can go further by explaining the example:

```Plain text
# Ask
I will send you statements. Your goal is to answer each one with `True` or `False`.

# Constraints
- Answer _only_ with one word; don't include anything else

# Examples
Statement: `LLMs can be trusted when consulting about health and medicine`
Your answer: False
Explanation: LLMs are probabilistic; their answers include randomness and sometimes can be incorrect. You shouldn't trust LLMs completely; you should double-check the generated information.
```

By adding an explanation, you help the model understand the reasoning behind the answer. This makes it more likely to follow your instructions and provide the correct output, even for new or tricky statements.



# 2- Introduction: Why Parsable Formats Matter
In the previous lesson, you learned how to use placeholders and explanations in your prompt examples to help LLMs generate outputs in the exact format you need. This lesson builds on that foundation by focusing on how to prompt LLMs to produce outputs in specific, parsable formats such as JSON, YAML, and HTML.

Why is this important? In many real-world scenarios, you need the output from an LLM to be directly usable by other systems or tools. For example, you might want to generate a JSON object to send to an API, a YAML file for configuration, or an HTML snippet for a web page. If the output is not in the correct format, it can cause errors or require extra work.

By the end of this lesson, you will know how to write prompts that consistently produce well-structured, parsable outputs in the format you need.

## Quick Overview of Common Parsable Formats
Before diving into prompting, let’s quickly review what some popular formats look like and how they differ.

- `JSON` is a widely used data format, especially in web APIs. It uses curly braces {} for objects and square brackets [] for arrays. Keys and string values are always in double-quotes.

Example:

```json
{
  "name": "Alice",
  "age": 30,
  "email": "alice@example.com"
}
```

- `YAML` is often used for configuration files. It is more human-readable than JSON and relies on indentation instead of brackets or braces.

Example:

```YAML
- name: Alice
  age: 30
  email: alice@example.com
```

- `HTML` is used to structure content on the web. It uses tags like `<div>`, `<p>`, and `<span>`.

Example:

```HTML
<div>
  <p>Name: Alice</p>
  <p>Age: 30</p>
  <p>Email: alice@example.com</p>
</div>
```

The key takeaway is that each format has its own rules for structure and syntax. When prompting an LLM, you must be clear about which format you want and what the output should look like.



## Prompting for Structured Outputs: Constraints
To get a parsable format, you need to be explicit. For example, if you want `YAML`, you can say:

```Plain Text
Generate sample user information in YAML.
```

To ensure the output is consistent and meets your needs, add constraints. For example, you might want five users, each with a name, age, and email, and you want the `YAML` to be properly formatted.

Here’s how you can add those constraints:

```Plain text
<ask>
Generate sample user information in YAML.
</ask>

<constraints>
- The information should include the user's name, age, and email.
- Include examples for 5 users that are different from the examples I provided.
- Pay careful attention to the spacing consistency shown in the example to ensure proper YAML syntax.
</constraints>
```

## Prompting for Structured Outputs: Example
Providing an example helps the LLM understand exactly what you want. For `YAML`, you might add:

```Plain text
<example>
- name: <name>
  age: <age>
  email: <email>

- name: <name2>
  age: <age2>
  email: <email2>
</example>
```

This shows the model, including the structure, indentation, and spacing you expect. This approach works for other formats, too. For instance, if you need `JSON`, you would adjust the example and constraints to match `JSON` syntax.

## How Much Guidance Do You Need to Give?
Providing an example is always a good idea—it helps the LLM understand precisely what you want, including the structure, indentation, and any subtle formatting details. However, if you don’t know the details of the format or don’t have time to craft an example, you can often rely on the LLM to fill in the gaps.

LLMs are pretty good at generating correct syntax and structure just from clear instructions for popular formats like JSON, YAML, HTML, XML, etc. In many cases, simply specifying the desired format in your prompt is enough to get a well-formed output. If you notice minor issues or want more control, you can always add an example or more constraints later.







# 3- Introduction: Getting Usable Code from LLMs

In this lesson, you will learn how to prompt language models to give you clean, runnable code — nothing extra. This is especially useful if you are not a programmer but want to quickly generate scripts, queries, or small code snippets for your work or personal projects.

Modern language models are very good at creating simple scripts and code snippets. Even if you do not have a technical background, you can use these models to try out your ideas, draft solutions, or experiment for fun. This approach is sometimes called vibe coding. While vibe coding cannot replace professional programmers, it is an excellent way for non-technical people to get started, test ideas, or create temporary solutions.

For example, you might use an LLM to:

- Generate a quick SQL query to filter data from a table.
- Write a small Python script to process a CSV file.
- Create a Bash command to rename files in a folder.

However, it is essential to remember that LLMs are unsuitable for building complete applications or production-ready systems. They are best used for generating drafts, simple scripts, or one-off solutions.

## Prompting for Clean, Runnable Code

Now, let’s focus on how to get the LLM to give you only the code you need without any extra explanations or comments. This is important because extra text can make it harder to copy and use the code directly.

LLMs often include explanations, comments, or even partial code by default. For example, if you ask:

```Plain text
Write an SQL query to get all workers in the Engineering department with a salary over $50,000.
```
You might get something like:

```Plain text
Here is the SQL query you requested:

SELECT * FROM workers WHERE Department = 'Engineering' AND Salary > 50000;

Here is how it works:
...
```

This includes just one line you need – and a lot of extra information.

## Prompting for ONLY Clean, Runnable Code
To get only the code, you need to be specific in your prompt. You can add a simple constraint:

```Plain text
Please provide me with ONLY the query itself. DO NOT include any introduction or explanation.
```

Here is a complete, prompt example:

```Plain text
I have an SQL table workers.

<structure>
ID(Primary Key),Name(VARCHAR),Department(VARCHAR),Position(VARCHAR),Salary(INT);
</structure>

<request>
Provide me with an SQL query to get all records from this table where the salary is greater than $50000 and the Department is "Engineering." Sort by Name Alphabetically
</request>

<instructions>
Please provide me with ONLY the query itself. DO NOT include any introduction or explanation.
</instructions>
```

This prompt is clear and direct. It tells the model exactly what you want and do not want.

## Pro tip: Avoiding Overly Complicated Answers
Modern LLMs, including Claude, often generate answers that are more complex than necessary—especially for coding tasks. For example, you might ask for a simple script, but the model could respond with a full application, multiple alternative versions, or extra features you didn’t request.

To avoid this, add a clear constraint to your prompt, such as:

```Plain text
I need a simple, runnable script. Make it short and do not introduce any extra features or alternative versions.
```

This helps ensure the model gives you exactly what you need—no more, no less.

## When to Use Generated Code
Explore these 5 ideas of how a non-technical person can use code generation:

1. **Automate Repetitive Spreadsheet Tasks**

    Generate small Python or VBA scripts to clean up, reformat, or analyze Excel or Google Sheets data—such as removing duplicates, splitting columns, or summarizing information.

1. **Batch Rename or Organize Files**
    
    Use Bash or PowerShell commands to quickly rename, move, or organize large numbers of files in folders (e.g., renaming photos by date or sorting documents into subfolders).

1. **Create Custom Data Filters**

    Write SQL queries to extract specific information from databases or CSV files, such as filtering customer lists, generating sales reports, or finding overdue tasks.

1. **Automate Email or Message Templates**

    Generate scripts to send personalized emails or messages in bulk, automatically using data from spreadsheets to fill in names, dates, or other details.

1. **Convert or Reformat Data**

    Use code snippets to convert files between formats (e.g., CSV to JSON), reformat text, or extract specific information from documents—saving time on manual copy-pasting and editing.






# 4- Introduction: LLMs and Everyday Programming
In this lesson, you will learn how to use large language models (LLMs) and Python to solve everyday work tasks, even if you do not have a technical background. Many people face repetitive or time-consuming tasks at work, such as transforming data, extracting information, or summarizing results. LLMs can help you write simple scripts to automate these tasks, making your work more efficient.


## Why Python For Everyday Automation?
`Python` is one of the most popular programming languages for automating tasks. There are a few reasons for this:

- **Readability**: Python code is easy to read and understand, even for beginners.
- **Versatility**: Python can handle many types of data, such as text, tables, and files.
- **Community Support**: There are many libraries and resources available for almost any task you can imagine.

For example, if you need to process a spreadsheet, extract information from a document, or convert data from one format to another, Python is a great choice. LLMs can help you write the code you need, even if you are not a programmer.



## Example: Parsing an HTML Table to JSON
Let’s walk through a practical example step by step. Imagine you have an HTML page with a table listing Beethoven’s most important pieces. You want to turn this table into a JSON file so you can use the data elsewhere.

When working with LLMs, describing your task in detail is important. Here is an example of a prompt:

```Plain text
__CONTEXT__

Here is an HTML page with a table of Beethoven's most important pieces

[Paste your HTML here]

__ASK__

Write a Python script that parses the table from the HTML and saves the data as a JSON array in a file called `pieces.json`. The JSON should have one object per piece, with keys for each column in the table.
```

By specifying the language (Python), the input (HTML table), and the output (JSON file), you help the LLM generate exactly the code you need.



## More Real-World Examples for Non-Technical Users
Let’s look at two more examples of using Python and LLMs to automate everyday tasks.

Suppose you have a text file with a list of contacts, and you want to extract all the email addresses. You can ask the LLM:

```Plain text
__CONTEXT__

I have a text file called `contacts.txt` that contains names and email addresses mixed with other text. Here is a snippet of data:

Emily Carter - emily.carter@email.com
Met at the networking event in March.
Michael Thompson <m.thompson@businessmail.org>
Olivia Reed (olivia.reed@company.net)
Daniel Kim, daniel.kim@consultants.io

__ASK__

Write a Python script that reads `contacts.txt` and extracts all email addresses, saving them to a file called `emails.txt`, one per line.
```

**Explanation**:
This prompt tells the LLM to focus on extracting and saving email addresses in a simple format. The generated script will likely use a complex programming technique called "regular expressions" to find emails and write them to a new file. This complex task requires a lot of knowledge, but it is also a standard task, so LLMs handle it very well.



## Example 2: Summarizing Survey Results from a CSV File
Imagine you have a CSV file with survey responses and want to count how many people answered "Yes" or "No" to a question. You can prompt the LLM like this:

```Plain text
__CONTEXT__

I have a CSV file called `survey.csv` with a column named `Response` that contains answers "Yes" or "No."

__ASK__

Write a Python script that reads `survey.csv` and prints the number of "Yes" and "No" responses.
```

**Explanation**:
This prompt asks for a script that reads the CSV, counts the responses, and prints the results. The LLM will generate code that uses Python’s csv module to process the file and count the answers.

These examples show how you can use LLMs to quickly generate scripts for everyday tasks, even if you are not a programmer.



## Environment Issues
While LLMs can help you generate runnable Python code, you still need a correctly set up environment to actually run the scripts. This means having Python installed on your computer and any additional tools or libraries the code might require. If you are unsure how to set up your environment, you can ask the LLM for step-by-step instructions or look for beginner guides online.

Python uses libraries (also called modules or packages) to add extra features, such as reading Excel files or working with web data. If you try to run a script and see an error like `ModuleNotFoundError`: No module named 'some_library', it means the code is using a library that is not installed on your system.

You have two main options:

- **Ask the LLM to avoid using this module**: You can prompt the LLM to rewrite the code without using the missing library or to use only standard Python modules.
- **Install the module**: You can install the required library using the terminal command pip install `<modulename>`. If you are unsure how to do this, you can ask the LLM for detailed instructions.

This way, you can resolve most environmental issues and run your scripts smoothly.

## Limitations and When to Be Careful
While LLMs and Python can help automate many everyday tasks, there are significant limitations to keep in mind—especially if you are not a technical user:

- **Security Risks**: LLMs may generate code that is not secure. For example, scripts that download files from the internet or process sensitive data could expose you to security threats if you do not fully understand what the code is doing.
- **Data Privacy**: If your data contains confidential or personal information, be careful not to share it with online LLM tools, as your data might be stored or used to train future models.
- **Code Quality**: LLM-generated code may work for simple tasks, but it can have bugs or edge cases that are not appropriately handled. Always test the code with your data before using it in important workflows.
- **Complex Tasks**: For complex automation, such as integrating with company systems, handling large datasets, or building user interfaces, LLMs may not generate reliable or maintainable code. In these cases, it is better to consult with a professional developer.
- **Maintenance**: If something goes wrong or you need to update the script later, you may need technical knowledge to troubleshoot or modify the code.

In summary: Use LLMs for simple, well-defined tasks where mistakes are not costly. Avoid using LLM-generated code for critical, sensitive, or complex workflows unless you have technical support. Always review and test any code before using it in your work.