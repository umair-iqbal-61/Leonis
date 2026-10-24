# Leonis

**An Explainable Pet-Care Record Quality Assessment and Reporting System**

Final Year Project (BS Information Technology, The Islamia University of Bahawalpur)
Status: Proposal phase. Formerly developed under the name PawPal.

## What is Leonis?

Leonis is a pet-care web application where owners keep their pets' records: profiles, meals, weight, vet visits, reminders and photos. It also includes an AI assistant that answers questions using the pet's own saved information.

Records entered over time end up incomplete, invalid, duplicated or inconsistent, and most apps never tell the owner. The FYP adds a rule-based record-quality module on top of the existing application. It checks records, explains every finding, lets the owner review it, and generates a structured quality report. The assistant then works from records the owner has reviewed, so its answers rest on cleaner data.

## Motivation

Many pet owners struggle when they ask a general AI assistant about their pet. Every conversation starts from zero, so they must repeat the pet's name, breed, age, meal plan, medications and history each time. Leonis stores this context once, so the assistant already knows the pet and can give more personalized answers.

The second problem is scattered records. The author owns a cat and had vet documents, photos and notes spread across a phone gallery, chats and paper. Leonis gives each pet one place for its records and document photos, so they can be found later.

Records are only useful if they are correct, which is why the FYP focuses on checking and explaining record quality.

## Repositories

This repository is the project hub. The code lives in two repositories:

| Part | Repository | Live deployment |
|---|---|---|
| Frontend | [leonis-frontend](https://github.com/umair-iqbal-61/leonis-frontend) | [pawpal.umairiqbal.tech](https://pawpal.umairiqbal.tech) |
| Backend | [leonis-backend](https://github.com/umair-iqbal-61/leonis-backend)

## Tech Stack

- **Frontend:** React, Vite, Tailwind CSS v4, Framer Motion, Recharts (Vercel)
- **Backend:** Node.js, Express (Render)
- **Database:** PostgreSQL on Neon, accessed through Prisma ORM
- **Authentication:** JWT and bcrypt
- **Image storage:** Cloudinary
- **AI assistant:** Groq LLM API, called through the backend with the pet's stored records as context
- **Rules engine:** deterministic backend rules, so every finding is reproducible and explainable

## Project Scope

**Already built (baseline application):**
- Authentication and multiple pet profiles
- Meal, weight and vet-visit records, reminders and photos
- Weight charts and dashboard
- AI assistant that uses the pet's saved profile and records as context

**Planned for the FYP:**
- Completeness checks (missing required fields per record type)
- Validity checks (for example zero or negative weight)
- Cross-record consistency checks (for example a follow-up dated before its vet visit)
- Possible-duplicate detection, flagged for review and never auto-removed
- Explainable findings showing which rule fired and why
- Review workflow: reviewed, resolved or dismissed
- Structured quality report generated from the findings
- Assistant context built from reviewed records, with flagged records marked so the assistant does not treat them as reliable facts

**Out of scope:** veterinary diagnosis or treatment advice (the assistant gives general guidance only), disease prediction, training custom machine-learning models, real veterinary datasets, payments and social features.

## Evaluation Plan

No real veterinary dataset is available, so evaluation uses a labeled synthetic benchmark with known errors and valid-but-unusual cases.

- Metrics: precision, recall, F1-score and false-positive rate, overall and per rule
- Baseline comparison: field-level validation alone versus field-level plus cross-record rules
- Error analysis of false positives and false negatives

The AI assistant is a supporting feature. It is demonstrated with example conversations (with and without the pet's context) and is not a primary evaluation target.

Synthetic results do not prove performance on real pet-owner data. This limitation will be stated in the final report.

## Author

Umair Iqbal, [umair-iqbal-61](https://github.com/umair-iqbal-61)
