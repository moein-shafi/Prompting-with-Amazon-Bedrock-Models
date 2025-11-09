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