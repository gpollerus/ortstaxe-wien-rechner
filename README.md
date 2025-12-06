# Vienna Tourist Tax (Ortstaxe) Calculator

An unofficial, browser-based calculator for the **Vienna local tourist tax (Ortstaxe)** – with scenario simulation for the planned increases and a focus on **hotel practice, margins and pricing decisions**.

This project was built as a small side tool for hotel management, revenue, and reservations teams in Vienna who want to understand **what the tax really does to net room revenue and margins**.

> ⚠️ **Unofficial tool**  
> This calculator is **not** an official product of the City of Vienna or any public authority.  
> It is a best-effort implementation based on publicly available information and typical Vienna hotel practice.

---

## Features

- **Status quo vs. future scenarios**
  - Default scenarios for 3.2 %, 5.0 % and 8.0 % tourist tax
  - Optional **custom tax rate** for testing “what-if” cases

- **Two calculation modes**
  - **Inclusive**: Guest pays a fixed *gross* price (Ortstaxe included)  
  - **Exclusive**: Room rate + tourist tax added on top

- **Realistic hotel logic**
  - Separate **breakfast amount** (not subject to tourist tax)
  - Optional **11 % flat deduction** on net room revenue (typical Vienna approach)
  - Handles number of **nights** and **rooms** (per night & total)

- **Scenario comparison matrix**
  - Net room revenue per night
  - Tourist tax per night
  - Difference vs. status quo (loss of net revenue in inclusive mode)
  - Highlighting of the currently selected scenario

- **Margin protection (“keep margin”)**
  - Calculates how much you would need to **increase the gross price per night** in higher tax scenarios
  - Shows:
    - Lost net revenue *per room night* and *in total*
    - Suggested new gross rate per night to keep the same net room margin as in the status quo

- **Fully client-side**
  - Single `index.html` file
  - No backend, no data storage, no tracking

---

## How it works (short version)

The calculator takes a few simple inputs:

- Gross room price per night (with or without tax included)
- Breakfast amount per night (if applicable)
- Number of nights
- Number of rooms
- Tourist tax scenario (3.2 / 5 / 8 % or custom)
- Whether the 11 % deduction on net logis is applied

From there it:

1. Splits **Logis vs. breakfast**.
2. Converts to **net amounts** (removing VAT).
3. Applies the **11 % deduction** (if enabled) to get the taxable base.
4. Calculates the **tourist tax** as a percentage of this base.
5. Reconstructs:
   - Net room revenue (logis)
   - VAT on logis & breakfast
   - Tourist tax
   - Total amount paid by the guest
6. Compares the scenarios and (optionally) computes which **new gross price per night** would be needed to keep the same net logis as in the status quo.

All calculations happen locally in the browser using plain JavaScript.

---

## Usage

### Online (GitHub Pages)

If this repository is published via GitHub Pages, you can simply open the public URL, for example:

```text
https://gpollerus.github.io/ortstaxe-wien-rechner/
