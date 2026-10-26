# Leonis

**Rule-Based Record Quality Assessment for AI-Assisted Pet and Livestock Care**

Final Year Project (BS Information Technology, The Islamia University of Bahawalpur)
Status: Proposal phase. Formerly developed under the name PawPal.

## What is Leonis?

Leonis is a web platform where owners keep their animals' records in one place: profiles, meals, weight, vet visits, reminders and document photos. It supports pets and dairy animals, provides breed and species guidance, includes an AI assistant that answers using the animal's own saved information, and has a listings board where owners can advertise animals such as kittens or calves.

Records entered over time end up incomplete, invalid, duplicated or inconsistent, and most apps never tell the owner. The core technical contribution of the FYP is a rule-based record-quality module. It checks records, explains every finding, lets the owner review it, and generates a quality report. The assistant then works from records the owner has reviewed, so its answers rest on cleaner data.

## Motivation

Many owners struggle when they ask a general AI assistant about their animal. Every conversation starts from zero, so they must repeat the name, breed, age, meal plan, medications and history each time. Leonis stores this context once, so the assistant already knows the animal and can give more personalized answers.

The second problem is scattered records. The author owns a cat and had vet documents, photos and notes spread across a phone gallery, chats and paper. Leonis gives each animal one place for its records and document photos, so they can be found later.

Dairy owners face the same problem at a larger scale: one person may look after many animals, and keeping their health, breeding and milk records correct matters even more. Records are only useful if they are correct, which is why the FYP focuses on checking and explaining record quality.

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
- **AI assistant:** Groq LLM API, called through the backend with the animal's stored records as context
- **Rules engine:** deterministic backend rules, so every finding is reproducible and explainable

## Project Scope

**Core (evaluated):**
- Rule-based record-quality module:
  - Completeness checks, using species and breed expectations (for example, expected vaccinations)
  - Validity checks (for example zero or negative weight)
  - Cross-record consistency checks (for example a follow-up dated before its vet visit)
  - Possible-duplicate detection, flagged for review and never auto-removed
- Explainable findings showing which rule fired and why
- Review workflow: reviewed, resolved or dismissed
- Structured quality report generated from the findings

**Supporting features:**
- Species-aware animal profiles for pets and dairy animals (for example milk yield, breeding and calving records)
- Breed and species knowledge base with expected vaccinations and care information, taken from cited references
- AI assistant that uses the animal's saved profile and reviewed records as context
- Document photos organised per animal

**Extended feature:**
- Listings board where owners advertise animals such as kittens or calves. Buyers contact sellers directly. A listing can include the animal's record-quality summary.

**Already built (baseline application):**
- Authentication and multiple pet profiles
- Meal, weight and vet-visit records, reminders and photos
- Weight charts and dashboard
- Groq-based assistant that uses the pet's saved profile and records as context

## Evaluation Plan

No real veterinary dataset is available, so evaluation uses a labeled synthetic benchmark with known errors and valid-but-unusual cases, covering both pet and dairy records.

- Metrics: precision, recall, F1-score and false-positive rate, overall and per rule
- Baseline comparison: field-level validation alone versus field-level plus cross-record rules
- Error analysis of false positives and false negatives

## Author

Umair Iqbal, [umair-iqbal-61](https://github.com/umair-iqbal-61)
