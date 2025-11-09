# 1- Introduction: Why Structuring Your Prompts Matters
Welcome to the first lesson of the course! This lesson will teach you why structuring your prompts is essential when working with large language models.

When you write a prompt, you are giving instructions to the LLM. If your instructions are clear and well-organized, the model is much more likely to provide you with a helpful and accurate response. On the other hand, if your prompt is messy or hard to follow, the model might misunderstand what you want.

Structuring your prompts is not just about making them look nice. It helps the LLM:

- Understand the context and the specific question or task.
- Separate different parts of your request, such as background information and the actual question.
- Focus on the most critical details.

Throughout this lesson, you will see how simple structuring choices can make a big difference in the quality of the responses you get.

## What Does It Mean to Structure a Prompt?

`Structuring` a prompt means organizing your prompt in a way that is easy for both you and the LLM to read and understand. This often involves using clear sections, lists, or other visual cues to separate different parts of your request.

For example, you might:

- Use headings or labels to separate context from your main question.
- Break down complex requests into bullet points or numbered lists.
- Highlight important words or phrases using capitalization, symbols, or spacing.

The key is to present your prompt clearly, so the LLM can easily identify what you want.

Let's look at a few examples to see how structuring helps.

### Example 1: Research Summary Request
**Unstructured**:

```Plain text
Summarize the main findings from the following research article and list any open questions.
```

**Structured** (using headings and bullet points):

```Plain text
CONTEXT:
I have a research article and I want to understand its key points.

ASK:
- Summarize the main findings from the article.
- List any open questions or areas for further research.
```

### Example 2: Email Drafting

**Unstructured**:

```Plain text
Write an email to my manager asking for a day off next Friday and mention that I have completed my current project.
```

**Structured** (using different style of headings and a numbered list):

```Plain text
task: Write an email to my manager.

context:
1. Request a day off next Friday.
2. Mention that I have completed my current project.
```

### Example 3: Event Planning Checklist

**Unstructured**:

```Plain text
Help me plan a birthday party for my friend with a guest list, food ideas, and activities
```

**Structured** (using a bulleted list and separating the context from the instructions):

```Plain text
CONTEXT: Friend's Birthday Party

Help me plan by providing the following:
- A guest list (suggested number and types of guests)
- Food ideas (snacks, main course, dessert)
- Activity suggestions (games or entertainment)
```

Please note that we use various structuring styles. Sometimes, headers are written in all caps, other times they appear as plain text.

You are free to use any structuring style you find comfortable—there is no single "best" way. Any clear and organized format is equally effective, as long as it helps both you and the LLM understand the prompt better.

## Using Markdown for Prompt Structuring

One of the most popular ways to structure prompts is by using Markdown. Markdown is a simple way to format text using plain characters and symbols. It's widely used for writing prompts, documentation, and notes because it's easy to read and write.

With Markdown, you can quickly add structure and emphasis to your prompts. Here are a few basics:

Headings: Use # for headings. More # symbols mean smaller headings.

```plain text
# Heading 1
## Heading 2
Bold: Use double asterisks or double underscores.
**bold text** or __bold text__
Italics: Use single asterisks or underscores.
*italic text* or _italic text_
Lists: Use dashes -, asterisks *, or numbers for lists.
- Item 1
- Item 2
1. First item
2. Second item
```
Separation: Use three dashes --- to create a horizontal line

### Example:

```Plain text
# My Heading

**Bold text** and *italic text*

- List item 1
- List item 2
```
Markdown is especially useful because:

- It is easy to learn and use.
- It works well in most LLM interfaces and chat tools.
- It makes your prompts visually clear and organized for both you and the LLM.

However, remember that Markdown is just one option. The most important thing is to structure your prompt in a way that is clear and easy to follow.


# 2- Introduction: Why Model-Specific Formatting?
As you learned in the previous lesson, clear formatting helps language models understand your requests better. Now, let's take this a step further. Some language models, such as Claude, GPT, or Gemini, work best when you use a specific format in your prompt. This is called `model-specific formatting`.

**Why does this matter?** Each model is trained differently and may expect information in a specific structure. If you use the right format, you can get more accurate and helpful responses. In this lesson, I will show you how to adapt your prompts to fit the needs of different models, focusing on `XML` formatting for `Claude` as a key example.

## What Is Model-Specific Formatting?

Model-specific formatting means shaping your prompt to match what a particular language model expects. For example, some models work well with plain text, while others prefer structured formats like XML or JSON.

If you use `Claude`, Anthropic recommends using `XML` tags to structure your prompt. Using the right format is like speaking the model's "native language." It makes your instructions clearer and helps the model give you better answers.

## Basics of XML
`XML (eXtensible Markup Language)` is a way to organize information using custom tags. It looks similar to HTML, but you can create your own tag names to describe your data. Each piece of information is wrapped in a pair of tags: an opening tag (like `<data>`) and a closing tag (like `</data>`). This helps both humans and language models understand the structure and meaning of the information.

For example:

```XML
<question>
What is your favorite color?
</question>
```
You can use any tag names that make sense for your task, such as `<instructions>`, `<data>`, or `<summary>`.

### Example: XML Prompting for Claude

Consider the following case: you have some data and want to summarize key trends and insights from it. Let's build an XML-formatted prompt for Claude to handle this task.

#### Step 1: Start with Your Data

First, you need to provide the data you want the model to analyze. For example, you might have a large CSV file with survey responses. You can wrap this data in a `<data>` tag to make it clear where the data starts and ends.

```XML
<data>
... (your survey data here) ...
</data>
```
Using the `<data>` tag, you tell Claude, "Everything inside here is the data you should look at."

#### Step 2: Add Your Instructions

Next, tell the model what you want it to do with the data. You can use an `<instructions>` tag for this.

```XML
<instructions>
Your goal is to summarize this data's key trends and insights, highlighting any notable patterns or outliers.
</instructions>
```

By structuring your prompt this way, you help Claude understand precisely what information to use and what task to perform. The XML tags act as clear boundaries, reducing confusion and improving the quality of the response.

**Key Point:**
<u>Always check the documentation for the model you are using</u>. Some models, like Claude, perform better with structured formats like XML. Others, like GPT, might be more flexible with markdown.

### Example: Nested XML Tags

XML tags can also be nested, meaning you can put tags inside other tags to show relationships between pieces of information. <u>This is useful when you have complex data or want to clearly organize your instructions</u>.

For example:

```XML
<task>
  <instructions>
    Summarize the survey results.
  </instructions>
  <data>
    <response>
      <name>Alice</name>
      <answer>Blue</answer>
    </response>
    <response>
      <name>Bob</name>
      <answer>Green</answer>
    </response>
  </data>
</task>
```
In this example, the `<task>` tag contains both `<instructions>` and `<data>`, and the `<data>` section contains multiple `<response>` entries. This structure clarifies which instructions go with which data and helps the model process your prompt more accurately.