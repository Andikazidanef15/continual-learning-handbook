---
noteId: "08f95ac0e5a511f19f51d968d1878af2"
tags: []
title: Continual Learning for the Curious
---

% Lines starting with "%" are MyST comments: visible here, hidden on the site.
% Delete each TODO once it's written.

# Continual Learning for the Curious

Suppose you're a data scientist at an online travel agency (OTA). You're asked to build a model that classifies the sentiment of English reviews. You train it on an English review dataset and, voilà, it reaches a 95% F1 score. Your product manager (PM) is happy :)

Then your PM comes back with a new request:

> We also have lots of Indonesian reviews. Could you retrain the model on those? It should work well on both languages, right?

You go for the simplest solution and fine-tune the model on the Indonesian dataset. It does well on Indonesian, but when you test it on English reviews again, the F1 score has dropped to 50%, barely better than a coin flip. Your PM is now sad :(

Ideally, we want a model that performs well on both languages, but that doesn't happen by default. This problem has a name: **catastrophic forgetting** [@mccloskey1989; @french1999], where a model forgets how to perform a task it was trained on before. Looking back at the example: when you train the model on the English dataset, the loss measures "how well it predicts the sentiment of English reviews." When you retrain it on the Indonesian dataset, the loss changes. It no longer measures "how well it predicts the sentiment of English reviews" but "how well it predicts the sentiment of Indonesian reviews," so the model's weights are gradually overwritten as retraining goes on.

So you come up with another plan: combine both datasets and retrain the model. Now the F1 score is much better than before. But then the PM raises another concern:

> If we want to add another language X, does that mean we need to combine the English and Indonesian datasets with the language X dataset and retrain again? Do we have enough compute for this?

Now you're stuck. You could keep adding languages to the dataset and retraining, but you don't have the compute to do that every time. You might want to give up, but fortunately, you've found this handbook.

## Why this handbook?

This handbook is a set of study materials for those of you who are interested in continual learning, one of the hottest research topics in LLMs because of its implications: we could keep LLMs up to date without expensive pretraining from scratch, and make them more personal, learning your preferences and characteristics without needing them in the context window.

In this handbook, we will explore methods for reducing catastrophic forgetting, from the simplest setting (classification tasks) all the way to LLM applications.

## Who it's for

- You're comfortable with Python and have trained a model in PyTorch.
- You know what gradient descent, cross-entropy, and a train/test split are.
- You **don't** need prior knowledge of continual learning.

% TODO: List the maths the later chapters use (e.g. a bit of probability for
% the Bayesian view in the EWC chapter) and link a refresher for each.

## How to read it

Each chapter explains one idea and includes code you can run. Notebook chapters
keep their outputs, so you can read them without running anything. You get
more out of them if you change things and rerun.

% TODO: Keep this map in sync with the toc in myst.yml as chapters land.

| Part | What you'll learn |
|---|---|
| **Foundations** | What forgetting looks like, the three CL scenarios, how CL is evaluated |
| **Regularization** | Protecting important weights: EWC, SI, MAS, the Bayesian view |
| **Replay** | Rehearsing old data, real or generated |
| **Architecture** | Growing or partitioning the network |
| **CL for LLMs** | Continual pretraining, test-time training, memory-based models |
| **Theory** | Why forgetting happens, the stability–plasticity tradeoff |

% TODO: Suggest a path for readers short on time, e.g. ch. 1 -> 2 -> 3.

## Running the code

% TODO: Fill in once the repo has an environment file.

```bash
git clone https://github.com/Andikazidanef15/continual-learning-handbook
cd continual-learning-handbook
pip install -r requirements.txt   # TODO: create this file
jupyter lab
```

% TODO: Note hardware needs. Foundations chapters should run on a laptop CPU in
% a few minutes; say so if a later chapter needs a GPU / Colab.

## Further reading

If you want a map of the whole field, start with the survey by Wang et al.
[@wang2024survey]. A longer, curated list lives in the reading list appendix.

% TODO: Link resources.md once it exists.

## About the author

% TODO: A few lines about you, what you're working on, and how to reach you.

## Feedback

% TODO: Point readers to GitHub issues for corrections and questions.
Found a mistake or something unclear? Please open an issue on the
[GitHub repository](https://github.com/Andikazidanef15/continual-learning-handbook/issues).
