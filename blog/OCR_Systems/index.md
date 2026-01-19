---
layout: post
title: "Building an OCR Product That People Actually Trust"
subtitle: "Lessons from Automating Claims Processing at Generali Central"
date: 2025-10-15
author: "Jash Vora"
background: '/assets/img/blog-bgd.jpg'
---

# Building an OCR Product That People Actually Trust

### Lessons from Automating Claims Processing at Generali Central

When I first started working on an OCR-based document processing system at Generali Central, the problem sounded deceptively simple:

> “Can we automatically read documents and speed up claims processing?”

From a purely technical lens, this felt like a classic computer vision + NLP task. Train an OCR model, extract fields, validate accuracy, ship.

In reality, building an **AI product inside a live insurance operation** turned out to be far more about **people, trust, and workflow design** than model performance alone.

This post walks through the **entire journey** : from talking to users on the ground, to discovering why high accuracy wasn’t enough, to designing systems that employees actually trusted and adopted.

---

## 1. Starting With the Wrong Assumption

Like most engineers, I began with a bias:

> If the model is accurate enough, adoption will follow.

Early experiments supported this belief.
On historical documents, the OCR pipeline was achieving **high accuracy** across most structured fields.

On paper, it was a success.

But when we piloted the system with operations and claims teams, something strange happened:

* People still **double-checked everything**
* Turnaround time didn’t improve as much as expected
* In some cases, it even got worse

That’s when I realized:
**Accuracy alone does not reduce operational time.**

---

## 2. Talking to the People Who Actually Use the System

Instead of tuning the model further, I stepped away from the code and started doing what I probably should’ve done earlier - **talking to users**.

I scheduled meets with:

* Claims processors
* Underwriting teams
* Operations managers

I asked simple questions:

* “What slows you down the most?”
* “Where do you hesitate to trust the system?”
* “What makes you re-check something?”

The answers were eye-opening.

---

## 3. The Real Bottleneck Was Trust, Not Accuracy

A few consistent themes emerged:

### 1. Uncertainty was expensive

Even if 9 out of 10 fields were correct, **the 1 uncertain field forced a full manual review**.

### 2. Errors weren’t evenly distributed

The OCR struggled with:

* Domain-specific terms
* Policy abbreviations
* Medical and claims-related vocabulary

These were precisely the fields that mattered most.

### 3. Employees had no way to judge confidence

The system gave outputs, but **no indication of how reliable they were**.

So employees played it safe:

> “If I don’t know how confident the system is, I’ll just verify everything.”

From their perspective, this was rational behavior.

---

## 4. Reframing the Problem as a Product Challenge

At this point, the problem was no longer:

> “How do we improve OCR accuracy?”

It became:

> “How do we reduce turnaround time *without increasing risk*?”

This shift changed every design decision that followed.

---

## 5. Introducing a Known Claims Vocabulary (Domain Knowledge Matters)

One of the highest-impact changes we made was deceptively simple.

Instead of treating OCR output as free-form text, we:

* Built a **known database of claims-related terms**
* Included policy-specific vocabulary, common medical phrases, and standardized fields
* Post-processed OCR outputs against this controlled vocabulary

This immediately reduced:

* Spelling-related ambiguity
* Variations that triggered manual review
* Edge cases that didn’t actually matter semantically

This wasn’t a new ML model — it was **product thinking layered on top of AI**.

---

## 6. Confidence Scores: Giving Users a Reason to Trust the System

The next major shift was adding **confidence scores** at the field level.

Instead of:

> “Here is the extracted value.”

The system now said:

> “Here is the value, and here is how confident I am.”

This small change had outsized effects:

* High-confidence fields were accepted without re-checking
* Low-confidence fields were reviewed selectively
* Users felt *in control*, not replaced

Crucially, we **did not hide uncertainty**.
We made it explicit.

That transparency built trust faster than any model improvement could.

---

## 7. Designing for Workflow, Not Just Models

We also mapped the **entire claims workflow**, end to end:

* Where documents enter
* Where human checks are mandatory
* Where automation actually saves time vs adds friction

This helped us:

* Insert AI only where it added net value
* Avoid automating steps that created downstream rework
* Align success metrics with operational reality

Success was no longer “OCR accuracy”.
It was:

* Reduction in manual handling
* Reduction in turnaround time
* Increased confidence among operations teams

---

## 8. The Outcome

With these changes:

* Manual document handling reduced by **~70%**
* Claim processing turnaround time dropped from **3–5 days to under 4 hours**
* Employees trusted the system enough to *actually rely on it*, not just audit it

None of this required chasing the last decimal of model accuracy.

---

## 9. What This Taught Me About Building AI Products

This experience fundamentally changed how I think about AI systems.

### Key lessons I carry forward:

1. **AI accuracy is not the product**
   The product is the workflow improvement it enables.

2. **Trust is a first-class feature**
   Confidence scores, transparency, and explainability are not “nice-to-haves”.

3. **Domain knowledge beats generic intelligence**
   A simple vocabulary database outperformed complex model tweaks.

4. **User behavior defines success, not dashboards**
   If people don’t change how they work, your model hasn’t solved the problem.

---

## 10. Closing Thoughts

Managing this OCR product at Generali Central taught me that **building AI products is less about clever algorithms and more about thoughtful system design**.

The most impactful changes didn’t come from the model — they came from listening to users, understanding their risk, and designing systems that respected how real work gets done.

That mindset now shapes how I approach every AI-driven product I build.
