# Flyrank-AI-Capstone
# My Capstone Project[AI-FLUENCY]
**AI Frontend Engineer Capstone · 🚧 Concept / Planning**

# StudyForge

StudyForge is an AI-powered workspace designed for students and self-learners who manage both **coursework** and **skill-building on the side**.

Instead of using separate tools for tracking assignments and tracking the skills/certifications you're building toward your career, StudyForge brings both workflows together.

---

## 📚 Course Mode

AI-assisted academic management:

- Turn a syllabus (or a pasted assignment list) into a task board
- Kanban board for assignments, exams, and projects (`To Do` → `In Progress` → `Review` → `Done`)
- Drag and drop tasks between stages
- AI breaks large assignments into subtasks with time estimates
- Ask an AI tutor to explain concepts from your own notes or slides
- Auto-sort/prioritize tasks as deadlines approach
- Deadline calendar view synced with the board

## 🚀 Growth Mode

AI-assisted skill building:

- Track courses, certifications, and self-study resources (Coursera, YouTube, docs, books)
- Kanban board for learning progress (`Want to Learn` → `Learning` → `Practicing` → `Mastered`)
- Paste a job posting or career goal → AI identifies skill gaps vs. your current progress
- Generate a personalized learning roadmap toward that goal
- Weekly AI-generated summary: what you learned, what to focus on next
- Link specific skills to specific course assignments (e.g., "this project taught me SQL joins")

---

## 🗂️ Data Model

A rough entity sketch to get started:

```
User
 ├── id, email, name, created_at

Course
 ├── id, user_id, title, term, syllabus_raw_text

Assignment (Course Mode task)
 ├── id, course_id, title, description
 ├── status: todo | in_progress | review | done
 ├── due_date, estimated_hours, ai_generated (bool)
 └── parent_assignment_id (nullable, for AI-generated subtasks)

Skill
 ├── id, user_id, name, category (e.g. "language", "framework", "soft skill")

LearningItem (Growth Mode task)
 ├── id, user_id, title, source (url/platform)
 ├── status: want_to_learn | learning | practicing | mastered
 ├── linked_skill_id
 └── linked_assignment_id (nullable — ties coursework to skill growth)

CareerGoal
 ├── id, user_id, title, job_posting_raw_text
 └── generated_roadmap (AI output, JSON)

WeeklySummary
 ├── id, user_id, week_start
 ├── summary_text (AI-generated)
 └── highlights (JSON array)
```

The `linked_assignment_id` on `LearningItem` is the key relationship — it's what lets StudyForge show "your coursework is already building these career skills," which is the core insight tying the two modes together.

---

## 📄 Page Structure

```
/                        Landing page
/login, /signup          Auth (Supabase Auth)

/dashboard               Overview: upcoming deadlines + active learning items + weekly AI summary

/courses                 List of courses
/courses/[id]            Kanban board for one course's assignments
/courses/[id]/tutor      AI tutor chat scoped to that course's notes/materials

/growth                  Kanban board for learning items (Growth Mode)
/growth/roadmap          Paste job posting → generated roadmap view
/growth/skills           Skill inventory + mastery levels

/settings                Profile, connected accounts, AI preferences
```

---

## 🛠️ Suggested Technologies

`Next.js` `React` `TypeScript` `Tailwind CSS` `shadcn/ui`

`Supabase` `PostgreSQL` `Vercel AI SDK` `Groq`

`dnd-kit` `Git` `GitHub` `Vercel`

This mirrors the ALYMERA capstone stack closely — it's a proven, well-documented combo for this kind of AI + Kanban + auth app, which keeps setup friction low and leaves more time for the AI features that differentiate the project.

**Status:** 💡 Concept — not yet started

## 🤝 Contact

SHIRIN KALEHER

- LinkedIn: [linkedin.com/in/your-handle](https://www.linkedin.com/in/shirin-kaleher-3a6a10349/)
