# Introduction: Why Structuring Your Prompts Matters
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