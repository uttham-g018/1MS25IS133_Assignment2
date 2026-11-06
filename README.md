# 1MS25IS133_Assignment2

# Coastal Karnataka Recipe Agent (ReAct + Gemini)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR-USERNAME/YOUR-REPO/blob/main/karnataka_recipe_agent_gemini.ipynb)

A ReAct agent built with the Gemini API. It reasons about a question, decides when to call a search tool, reads the result, and then writes an answer. All of this happens in a loop.

## What it does

The agent acts as a chef at a coastal Karnataka (Mangalore/Udupi) restaurant. It searches a small recipe database and answers only from what it finds.

**Recipes in the database:**
- Neer Dosa
- Chicken Ghee Roast
- Mangalorean Fish Curry
- Kori Rotti
- Masala Dosa

## How it works

1. The user asks a question.
2. Gemini decides whether it needs to call the `search_recipes` tool.
3. The tool searches the recipes by keyword and returns the best matches.
4. The result goes back to Gemini, which reasons again.
5. The loop repeats until Gemini has a final answer (maximum 8 steps).

If the recipes don't contain the answer, the agent says so.

## Setup

1. Get a free API key from [Google AI Studio](https://aistudio.google.com/) (Get API key → Create API key).
2. Open the notebook in Colab using the badge above.
3. Add the key under **Secrets** (the 🔑 icon) with the name `GOOGLE_API_KEY`.
   If no secret is found, the notebook asks you to paste the key.
4. Run all cells (Runtime → Run all).

> The free tier allows 10 requests per minute and 250 per day. The notebook retries automatically on rate-limit errors (429).

## Example questions

| Type | Question |
|------|----------|
| From the recipes | Which dish on our menu uses fish and how long is the fish cooked? |
| From the recipes | Does the neer dosa batter need fermentation? |
| From the recipes | How much ghee does the chicken ghee roast need? |
| From the recipes | How do we keep the kori rotti crisp when serving? |
| Not in the recipes | How many customers order our fish curry everyday? |
| General knowledge | What is the most famous street food in Mumbai? |

## Tech stack

- Python 3
- Google Colab
- `google-genai` and `google-generativeai` (Gemini API)

## Files

| File | Description |
|------|-------------|
| `karnataka_recipe_agent_gemini.ipynb` | The Colab notebook with the agent |
| `README.md` | This file |

## Security note

Never commit your API key. The notebook reads it from Colab Secrets or a hidden prompt, so it is not stored in the code.

## Next steps

- Add a tool that suggests ingredient substitutions.
- Add more Karnataka recipes to the database.

## References

- [Gemini function calling and thought signatures](https://ai.google.dev/gemini-api/docs/thinking#signatures)
- [Gemini text generation docs](https://ai.google.dev/gemini-api/docs/text-generation)
- [Google agent loop demo](https://github.com/xiaosuhu/midas-ai-in-research/blob/v1.0-dev/docs/notebooks/agent_loop_demo.ipynb)
