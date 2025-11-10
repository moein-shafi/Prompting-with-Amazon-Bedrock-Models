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
