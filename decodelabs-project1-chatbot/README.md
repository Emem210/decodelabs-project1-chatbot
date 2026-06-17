# Sales Intelligence Chatbot — Rule-Based AI Chatbot

**DecodeLabs Industrial Training Kit — Artificial Intelligence Track — Project 1**

A rule-based AI chatbot built entirely on `if-else` / dictionary logic (no machine learning) that answers natural-language questions about a 1,500-row sales dataset. Built to satisfy the Project 1 specification: continuous input loop, sanitization, a knowledge base with 5+ intents, a fallback response, and a clean exit strategy.

## Features

- Continuous `while True` conversation loop
- Input sanitization (`.lower().strip()`) so casing/whitespace never breaks a match
- Dictionary-based knowledge base (O(1) lookups instead of long if-elif chains)
- 15+ supported intents covering revenue, regions, products, sales reps, returns, payment methods, and promotions
- Graceful fallback response for unrecognized input
- Clean exit on `exit`, `quit`, `bye`, `q`, or `stop`

## Dataset

`Product-Sales-Region.xlsx` — 1,500 orders across:

- **Regions:** East, West, North, South, Central
- **Products:** Laptop, Phone, Desk, Chair, Monitor, Tablet, Printer
- **Sales Reps:** Alice, Bob, Carlos, Diana, Eva, Frank
- **Other fields:** Payment Method, Promotion, Returned, Discount, Shipping Cost, Order/Delivery Dates

## How to run

```bash
pip install pandas openpyxl
python sales_chatbot.py
```

Make sure `Product-Sales-Region.xlsx` is in the same folder as `sales_chatbot.py`.

## Example session

```
You: help
Bot: 📋 WHAT I CAN ANSWER:
  • total revenue / total sales
  • top region / worst region
  • sales by region  (e.g. 'east sales')
  • top product / worst product
  • sales by product (e.g. 'laptop sales')
  • top salesperson / all reps
  • sales by rep     (e.g. 'eva sales')
  • returns          (e.g. 'return rate laptop')
  • most returned product
  • total orders
  • payment methods
  • best promotion
  • exit / quit  → close the chatbot

You: top region
Bot: 🏆 Top Region: North  →  $967,957.98 in sales

You: laptop sales
Bot: 📦 Product: Laptop
   Revenue     : $684,417.24
   Units Sold  : 2,408
   Return Rate : 27.4%

You: exit
Bot: Goodbye! Thanks for exploring the sales data. 👋
```

## Architecture (IPO Model)

| Phase | Implementation |
|---|---|
| **Input** | `input()` inside a continuous `while True` loop |
| **Sanitization** | `raw_input.lower().strip()` |
| **Process** | Dictionary-based intent matching against a pre-aggregated knowledge base (`groupby` stats computed once at startup) |
| **Output** | Formatted response printed to console, loop continues until exit command |

## Skills demonstrated

- Control flow & decision-making logic
- Dictionary-based lookup (`O(1)`) vs. if-elif ladder (`O(n)`)
- Data preprocessing with pandas (`groupby`, aggregation)
- Input sanitization and fallback handling
- Clean, maintainable code structure

## Author

Amin — DecodeLabs AI Track, Batch 2026
