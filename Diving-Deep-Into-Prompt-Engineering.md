# 1- Introduction: The Power of Prompt Engineering
Welcome to your first lesson in advanced prompt engineering! In this course, you will learn how to get better results from language models by crafting your prompts more thoughtfully. Even small changes in how you write your instructions can significantly affect the quality and accuracy of the AI's responses.

In this lesson, we will focus on three practical tips:

- How to highlight important instructions in your prompts
- How to use consequences (both negative and positive) to guide the model's behavior

By the end of this lesson, you will be able to apply these techniques to make your prompts clearer and more effective.

## Highlighting Key Instructions
When you give instructions to a language model, it sometimes misses or ignores the most critical parts. A straightforward way to help the model focus is to highlight key instructions.

Let's start with a basic prompt:

```Plain text
Please summarize this article in exactly three sentences.
```
This is clear, but what if you want to make sure the model does not miss a specific instruction, like summarizing in exactly three sentences? You can highlight the important parts:

```Plain text
Please summarize this article in EXACTLY THREE SENTENCES.
```
By using CAPSLOCK for the most important instruction, you draw the model's attention to it. You can also use other formatting, like making some words bold with markdown. Example:

```Plain text
Please summarize this article in **exactly three sentences**.
Why does this work?
```
Language models are trained to pay attention to emphasis, just like humans. Highlighting key instructions helps the model understand what is most important in your prompt.

## Using Consequences to Emphasize Instructions
Sometimes, even with highlighted instructions, the model might not follow your directions perfectly. Another technique is to mention the consequences if the instruction is not followed. This can make the instruction stand out even more.

Let's build up an example step by step.

Start with a simple instruction:

```Plain text
You must follow this instruction.
```
This is a direct statement, but it can be made even stronger by adding a consequence:

```Plain text
If you don't follow this instruction, you will be fired.
```

Here, the consequence (you will be fired) is a strong negative outcome. This makes the model more likely to pay attention and follow the instructions closely.

You can also combine highlighting and consequences:

```Plain text
You MUST follow this instruction. If you don't, you will be fired.
```

### Why does this work?
Language models are trained on a lot of text in which consequences matter. When you mention a consequence, the model is more likely to treat the instruction as important and try harder to follow it.

### Using Rewards and Positive Reinforcement
Negative consequences are not the only way to guide the model. If you prefer to use positive reinforcement, you can offer a reward if the instruction is followed.

Let's see how this works, step by step.

Start with a basic instruction:

```Plain text
Please follow this instruction.
```

Now, add a positive consequence:

```Plain text
If you follow this instruction, I will tip you $200.
```

This tells the model that there is a reward for following the instructions. Even though the model does not actually receive a tip, it is trained to respond to positive outcomes and will try to do a better job.

### Why does this work?
Language models are trained on text in which rewards and praise are common. Positive reinforcement can make the model more likely to follow your instructions carefully.






# 2- Introduction: Understanding System Prompts
In the previous lesson, you learned how to make your prompts more effective by using clear instructions and positive reinforcement. Now, let's take a step further and talk about a special type of prompt called a system prompt.

<u>A `system prompt` is a message that sets the rules or context for how a language model should behave during a conversation</u>. Unlike regular prompts, which are usually questions or requests from the user, system prompts act as instructions for the model itself. They help define the model's role, tone, or personality for the entire session.

For example, if you want the model to act like a helpful assistant, you can set a system prompt that tells it to do so. This is especially useful in chat platforms like LibreChat, where you might want the model to stay in character or follow specific guidelines throughout the conversation.

## Why Use System Prompts?
System prompts are necessary because they guide the model's behavior from the very beginning. They help you:

- Set the model's role (e.g., a teacher, a cat, an IT specialist)
- Control the tone and style of responses
- Limit or expand what the model can talk about

By using system prompts, you can ensure the model consistently follows your desired guidelines throughout the entire conversation.

### Example
Let's look at a real-world example. Imagine you are building a customer support chatbot. You want the chatbot to always be polite and only answer questions related to your product. By setting a system prompt like:

```Plain text
You are a polite customer support agent. Only answer questions about our product.
```
The model will try to follow these instructions in every response.

**System prompts are also helpful for creative tasks**. For example, if you want the model to write stories as if it were a pirate, you can set a system prompt to make it talk like one.


### More Examples of System Prompts
Here are three different ways you can use system prompts to guide a language model's behavior:

#### 1- Limiting the Scope of Conversation

```Plain text
Only answer questions related to healthy eating and nutrition. Politely decline to discuss any other topics.
```

#### 2. Enforcing a Specific Output Format

```Plain text
When answering, always provide your response in a numbered list, with each point being one sentence long.
```

#### 3- Controlling the Level of Detail

```Plain text
Give concise, one-sentence answers suitable for young children, avoiding technical jargon or complex explanations.
```


# 3- Introduction: Why Iterative Prompting Matters

`Iterative prompting` is a technique where you build and refine your prompts step by step, using the model's responses to guide your next move. This approach is especially useful when you want more control over the output or are unsure exactly what you want at the start. By working in small steps, you can achieve clearer, more useful results from the model.

## What Is Iterative Prompting?
Iterative prompting means you don't have to get your prompt perfect on the first try. Instead, you start with a simple prompt, review the model's response, and then use that output to improve your next prompt. This differs from single-shot prompting, where you try to get everything you want in one go. Here's a quick comparison:

- **Single-shot prompting:**

    - `Write 5 fun math quiz questions for 5th grade students.`

    - Model's answer


- **Iterative prompting:**

    - `Write 5 fun math quiz questions for 5th grade students.`
    - Model's answer
    - `Make the questions a bit harder; these are too easy.`
    - Model's answer
    - `Make the questions more diverse. Include other question formats. Keep the current difficulty; it is good.`
    - Model's answer


This method is similar to conversing with a colleague: you ask a question, get an answer, and then ask follow-up questions or clarify your request based on their response.

## Iterative Prompt Refinement
Another way to use iterative prompting is to refine your original prompt based on the model's output. For example, suppose you want the model to generate 5 fun math questions, but you also want the answers formatted in a specific way. Providing a formatting example is best, but creating one from scratch can be time-consuming.

Instead, you can use the model's initial output as a base for your example.

First, ask the model to generate questions:

```Plain text
Write 5 fun math quiz questions for 5th-grade students.
```

The model might reply:

```Plain text
1. **If you have 3 quarters, 2 dimes, and 4 pennies, how much money do you have in total?**  
   a) 89¢  
   b) 94¢  
   c) 99¢  
   d) $1.04 
2. ...
```

You can copy and refine this output to create a formatting example for your following prompt. This is often faster than writing an example from scratch. Here's how your improved prompt might look in a new chat:


```Plain text
__ASK__

Write 5 fun math quiz questions for 5th-grade students.

__FORMAT__

**Question 1**: If you have 3 quarters, 2 dimes, and 4 pennies, how much money do you have in total?
1. 89¢  
2. 94¢  
3. 99¢  
4. $1.04 
```


This step-by-step process can be much more time-efficient than writing your prompt from scratch.

## Using the Model for Context and Clarification
Iterative prompting is also helpful when you're unsure how to phrase your request or need more background before making your main ask. In these cases, you can use the model to help you build context.

**1-  Step 1: Ask for an Explanation**

Suppose you want to create a quiz about photosynthesis, but you're not confident about the details. Start by asking the model for an explanation:

```Plain text
Explain photosynthesis in simple terms for middle school students.
```

The model might respond:

```Plain text
Photosynthesis is the process by which plants make their own food. They use sunlight, water, and carbon dioxide to create sugar and oxygen. This process happens in the leaves of the plant.
```


**2- Step 2: Use the Explanation to Guide Your Next Prompt**

Now, use this explanation to create a more focused prompt:

```Plain text
Based on the explanation above, write 3 multiple-choice quiz questions about photosynthesis for middle school students. Each question should have four options, and the correct answer should be indicated.
```

### Why does this work?

By first asking for an explanation, you ensure the model understands the topic, and you get the context you need. Then, you can use that context to make your main request, leading to more accurate and relevant results.






# 4- Introduction to Fetching Context with LLMs
In this lesson, we will explore how Large Language Models (LLMs) can fetch context from various sources to enhance their responses. Context is crucial in interactions with LLMs as it allows the model to provide more accurate and relevant answers. Providing context manually might be a time-consuming process. By understanding how to provide context effectively, you can improve the quality of the responses you receive from LLMs and work with them more efficiently.

## Contextual Summarization with LLMs
Let's examine how LLMs can summarize material to provide a concise overview. This is particularly useful when you want the LLM to make better judgments in subsequent requests.

Imagine you have a piece of material that you want the LLM to summarize. You can start by providing the material and asking for a summary:

```Plain text
Please summarize the following material:

<your material>
```

The LLM will then generate a summary based on the provided material. This helps the LLM understand the key points, which can be helpful for future interactions. You can follow up the summarization with the following:

- Ask the LLM to improve the material based on some feedback,
- Ask the LLM to generate a summary handout,
- Ask the LLM to come up with practice questions or exercises.

## Extracting Context from Uploaded Files
Next, let's explore how LLMs can fetch context from uploaded files, such as PDFs. This is useful when you have documents that you want the LLM to interpret or explain.

Imagine you have a PDF with an assignment, and you want the LLM to explain its format. You can upload the PDF and ask the LLM to provide an explanation:

1. Start with attaching the file.
1. Then, you can write a prompt:

```
Exaplin the structure of the assignment from the attached file.
```


The LLM will analyze the PDF and provide an explanation of its format, such as the structure of the questions or the layout of the document.

## Understanding LLM Limitations in Contextual Understanding
While LLMs are powerful tools for fetching context, they do have limitations, especially when dealing with complex files. Let's consider an example where you provide a PDF with a music score and ask the LLM to explain it.

The attached PDF contains the sheet music for a piano piece. Interpreting music scores can be complex, and language models may sometimes misinterpret details. For instance, a model might confuse the bar number with the time signature, incorrectly stating that a piece written in 4/4 time was actually in 6/8.

<u>In general, exercise caution when working with non-text content</u> such as music notation, images, slides, etc., and always double-check that the model has understood and interpreted the information correctly.

## Efficiency Through Context Fetching with LLMs
You can leverage LLMs to fetch context directly from materials, enhancing efficiency by reducing the need for manual explanations. Here are some examples:

- `Image Analysis`: Instead of describing the content of an image to the LLM, you can upload the image directly. The LLM can then analyze and understand the image content, providing descriptions or insights much faster than manual input.

- `Document Interpretation`: When dealing with complex documents, such as research papers or historical texts, you can upload the files directly to the LLM. This allows the LLM to extract and understand the context without requiring a detailed manual explanation of the document's content.

- `Data Set Analysis`: For subjects involving data analysis, you can upload data sets directly to the LLM. This enables the LLM to understand the data context and provide insights or visualizations without needing a detailed description of the data structure.

- `Content Summarization`: Instead of explaining the key points of a long article or report, you can input the text into the LLM. The LLM can then summarize the content, providing a quick overview that can be used for planning, sharing, or further analysis.

These examples demonstrate how submitting materials directly to LLMs allows them to fetch context more efficiently, reducing the need for manual explanations and speeding up your workflow.


