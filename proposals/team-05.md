# DSAN 6725 Final Project Proposal

<!--
A worked example, not a submission. It shows the level of detail a proposal needs, and
CI validates it alongside the real ones, which proves the rules are satisfiable. Do
not edit this file, and pick your own project idea.
-->

## Team Number

05

## Team Name

Mini_Hermes

## Team Members

| Name        | NetID  |
| ----------- | ------ |
| Jieyu Deng | ??? |
| Renqing Liu | ??? |
| Tianwei Shi | ??? |
| Younghoon Kim | yk816 |

## Project Title

Mini_Self-improving AI agent(mini_hermes)

## Abstract

Personalized AI agents can improve over time by learning from user data and feedback. However, most of these agents depend on external model providers, so private user data leaves the user's device. This project asks: how can we build a personalized AI agent that keeps improving from user data and feedback without sending private data to outside providers? To explore this question, we build mini_hermes, a self-improving AI agent that runs fully on local models. Its task is to clean lecture transcripts by removing irrelevant content and noise.
The system has three parts, all run locally through Ollama. First, a Gemma-based LLM acts as the main controller. It runs the improvement loop, evaluates results, and updates a SKILL.md file that describes how the agent should do its task. Second, a coding model edits the agent's Python files based on the updated SKILL.md. Third, an embedding model builds a vector database from the transcripts. Our data is the text transcript of an audio recording from a Georgetown University course lecture. We evaluate the agent's output in two ways: manual ground-truth labels and an AI-based evaluation through the Jev API.
The project faces several risks. Running multiple local models and repeating the evaluation-and-improvement loop may require more computing power than we have. Measuring output quality is also difficult because poorly cleaned text can still have high cosine similarity with the original transcript, so we need better evaluation methods. Finally, self-improvement may be unreliable: changes the agent makes may not always improve performance and could introduce new errors or regressions.
