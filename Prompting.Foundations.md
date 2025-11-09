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


# Defining Constraints and Requirements for Effective Prompts

When you give an LLM a task, it will try to fulfill your request. However, if your instructions are too broad or vague, the model might produce answers that are off-topic, too lengthy, or not useful. By adding explicit constraints and requirements, you guide the model to deliver precisely the desired output.

In this lesson, you'll learn what `constraints` and `requirements` are, how to write them effectively, and how they can make your prompts much more powerful.

## What Are Constraints and Requirements?
A `constraint` is a rule or limit you set for the LLM's response. A `requirement` is something the response must include or follow. Both help you control the output.

Let's look at a simple example. Imagine you want to create a survey for your customers. Here's a basic prompt:

```Plain text
Suggest five questions I can include in a customer survey.
```

This prompt is clear, but it leaves a lot of room for interpretation. The LLM might suggest questions about anything — pricing, product features, or even personal information.

Now, let's add some `constraints`:

```Plain text
Suggest five questions I can include in a customer survey.
- Each question must be open-ended.
- Do not mention pricing in any question.
- Keep each question under 20 words.
```

Adding these constraints tells the LLM exactly what you want and what to avoid. This makes the output more focused and valuable.

## Best Practices for Writing Constraints

- `Organize constraints as a bulleted list`: This makes them easy for both you and the model to read and follow.
- `Be specific`: Vague constraints are easy to overlook. Spell out exactly what you want or don't want.
- `Limit the number of constraints`: Too many constraints can overwhelm the model, causing it to ignore some. Focus on the most important ones.
- `Be strict and explicit`: Use strong language like "must" to emphasize what is required.

Let's see how these tips work in practice.

### Another Example
Suppose you want the LLM to write a product description but want it to be short and not mention the price. Here's how you might write your prompt:

```Plain text
Write a product description for a new smartwatch.

- The description must be under 50 words.
- Do not mention the price.
- Focus on health and fitness features.
```
Explanation:

- The first constraint sets a word limit, ensuring the answer is concise.
- The second constraint tells the model to avoid discussing price.
- The third constraint directs the content to focus on a specific topic.

By being clear and direct, you help the LLM give you precisely what you need.

### One More Example
Let's say you want the LLM to generate a list of creative team-building activities for a remote team, but you have some specific needs. Here's a prompt with well-defined constraints:

```Plain text
# Context:
I want to brainstorm ideas for a team-building session.

# Ask
Suggest four creative team-building activities for a remote team.

# Constraints
- Each activity must be suitable for video calls.
- Do not suggest any activities that require physical materials.
- Keep each activity description under 30 words.
```

Note:

This prompt also uses formatting to separate context, ask, and constraints.




# Introduction: The Power of Examples in Prompting
Welcome back! In the last lesson, you learned how to use constraints and requirements to make your prompts more effective. Today, I want to show you another powerful tool: **using examples within your prompts**.

When you include a clear example, you give the language model a template to follow. This makes your instructions easier to understand and helps the model produce more consistent and accurate answers. In this lesson, you will see how examples can simplify your prompts and reduce the need for complex constraints.

## What Happens Without Examples?

Let's start by looking at what happens when you give a prompt without examples. Imagine you want to create a set of quiz cards about large language models (LLMs) for your students.

You might write a prompt like this:

```Plain text
# Context

I want to print 10 cards with choose-one questions about LLMs for my students.

# Ask

Come up with 10 questions with three answer options, where one answer is correct.
```

If you give this prompt to an LLM, you might get answers that look like this:

```plain text
1. What does LLM stand for?
   a) Large Language Model
   b) Long List Model
   c) Logical Learning Machine
   Correct answer: a

2. Who created GPT-3?
   a) Google
   b) OpenAI
   c) Microsoft
   Correct answer: b

...
```

At first glance, this looks fine. But if you try this prompt several times, you might notice:

- The format of the questions and answers can change each time.
- Sometimes, the correct answer is not clearly marked.
- The numbering or lettering might be inconsistent.
- The model might include an introduction or extra text you didn't ask for.

This happens because the model is making its best guess about what you want, but you haven't given it enough guidance.

## How Examples Improve LLM Responses

One of the easiest ways to help the model understand your desired format is to provide an example. Let's add a clear example to our prompt:

```Plain text
# Context

I want to print 10 cards with choose-one questions about LLMs for my students.

# Ask

Come up with 10 questions with three answer options, where one answer is correct.

# Example

1. **Question:** Which mechanism, introduced in 2017 by Google Research, was the foundational principle of LLMs?
   1. Transformer Architecture with self-attention mechanism
   2. Reinforcement Learning Principle
   3. Structure-based Architecture with summarization mechanism

   **Correct Answer:** 1.
```

By including this example, you are:

- Showing the exact format you want for each question and answer.
- Making it clear how to mark the correct answer.
- Setting the tone and style for the rest of the questions.
- When you give this prompt to the LLM, the output is much more likely to match your expectations. The model will follow your provided structure, making the results more consistent and easier to use.

## Pro Tip
**Note**: Most modern large language models (LLMs) generate responses using Markdown, a lightweight markup language for formatting text. When you interact with these models through a chat interface, the platform automatically renders the Markdown, so formatting like headings, lists, bold, italics, and code blocks appear as intended.

For example:

- If the model outputs `# Heading`, the chat interface displays it as a large, bold heading.

- Writing `**bold text**` will appear as bold text.

- Lists like:

```Plain text
- Item 1
- Item 2
```
Will be shown as:

- Item 1
- Item 2

Because of this, when you provide examples or prompts in Markdown, you are explicitly showing the model the exact formatting you want in its response. This helps ensure the output matches your expectations in structure and appearance.

## Combining Examples with Constraints
In previous lessons, you learned how to use constraints to control the LLM's output. Sometimes, even with an example, the model might include things you don't want, like repeating your example question or adding an introduction or conclusion. This is where constraints come in.

```Plain text
Constraints:
- Do not include any introduction or conclusion
- Do not repeat the example question
```

With these constraints, your output will be cleaner and more focused, matching your needs.

