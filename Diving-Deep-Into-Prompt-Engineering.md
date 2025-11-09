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

