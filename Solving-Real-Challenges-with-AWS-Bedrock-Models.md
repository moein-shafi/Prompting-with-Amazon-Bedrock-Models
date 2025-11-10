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