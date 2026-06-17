<div align="center">

<img src="https://raw.githubusercontent.com/sigma-loop/.github/main/profile/assets/cover.png" alt="SigmaLoop — Master the Logic behind the Code" width="360" />

# SigmaLoop

### Master the Logic behind the Code

**A personalized AI tutor for programming and mathematics.**
No catalog, no fixed syllabus — SigmaLoop *figures out what you need* and **generates the course, lessons, coding challenges, math problems, and quizzes on demand**, just for you.

<br/>

![React 19](https://img.shields.io/badge/React-19-2dd4bf?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-strict-3178c6?logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Express-6366f1?logo=nodedotjs&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-22c55e?logo=mongodb&logoColor=white)
![Judge0](https://img.shields.io/badge/Judge0-sandbox-f59e0b)
![DeepSeek + Gemini](https://img.shields.io/badge/AI-DeepSeek%20%2B%20Gemini-3b82f6)

</div>

---

## What is SigmaLoop?

Most learning platforms hand you the same content as everyone else. SigmaLoop does the opposite: **every course, lesson, and challenge is manufactured by an AI pipeline for one specific learner, and owned by them.** There is no shared catalog and no instructor-authored content — the *only* way material exists is that the system generated it for *you*.

The atomic experience is a **lesson** — a short teaching body plus **many challenges of mixed kinds**. A lesson is complete only when **all** its challenges pass. A single lesson on recursion might mix a multiple-choice check, a coding challenge, and a math proof.

<div align="center">
<img src="https://raw.githubusercontent.com/sigma-loop/.github/main/profile/assets/landing.png" alt="SigmaLoop landing page" width="85%" />
</div>

---

## Two ways to start

| | |
|---|---|
| **🗣️ Talk to the mentor** — a Socratic, autonomous AI tutor. Tell it what you want to learn; it gauges your level and *acts*: it can read your courses and progress, then create courses, generate lessons, and edit content on your behalf. | **🧭 Guided onboarding** — pick topics from a curated library, then answer AI-tailored follow-up questions. The system deduces your goal and generates a curriculum to match. |

<table>
<tr>
<td width="50%"><img src="https://raw.githubusercontent.com/sigma-loop/.github/main/profile/assets/mentor.png" alt="The autonomous mentor creating a course" /></td>
<td width="50%"><img src="https://raw.githubusercontent.com/sigma-loop/.github/main/profile/assets/onboarding.png" alt="The onboarding topic picker" /></td>
</tr>
<tr>
<td align="center"><em>The mentor creates a personalized curriculum on request.</em></td>
<td align="center"><em>The onboarding wizard — pick what you want to learn.</em></td>
</tr>
</table>

---

## Three kinds of challenge — three graders

The defining engineering opinion of SigmaLoop is **how each kind of challenge is graded.** The product uses exactly as much AI as it must, and not a drop more:

| Kind | What the AI authors | How it's graded |
|---|---|---|
| **PROGRAMMING** | prompt, starter code, reference solution, test cases | **Judge0 sandbox** runs your code against the test cases — *deterministic* |
| **MATH** | problem + canonical solution (LaTeX) + rubric | the active LLM returns a **structured verdict** with a *confidence* score — *AI judgement, confined to where it's genuinely needed* |
| **MCQ** | stem + options (each flagged correct/incorrect) | **server-side set-equality** — *deterministic*; option correctness is never sent to the client until you submit |

<div align="center">
<img src="https://raw.githubusercontent.com/sigma-loop/.github/main/profile/assets/graders.png" alt="Three graders, one progress engine" width="85%" />
</div>

Programming and MCQ grading stay **deterministic** (fast, free, never hallucinate a grade). LLM judgement is **confined to mathematics** — the one place where `x^2 + 2x + 1` and `(x+1)^2` are the same answer in different clothes — and even there a low-confidence verdict is held for review rather than trusted.

<div align="center">
<img src="https://raw.githubusercontent.com/sigma-loop/.github/main/profile/assets/workspace-programming.png" alt="The programming challenge workspace" width="85%" />
<br/><em>The kind-dispatched workspace: Monaco editor, language picker, Run, and a live output panel.</em>
</div>

---

## Architecture

<div align="center">
<img src="https://raw.githubusercontent.com/sigma-loop/.github/main/profile/assets/architecture.png" alt="The four-layer architecture" width="80%" />
</div>

- **Frontend** — React 19 + TypeScript + Vite SPA, Tailwind, a clean Linear/Vercel-style design.
- **Backend** — Node.js + Express + TypeScript REST API (JSend) over MongoDB/Mongoose, JWT auth.
- **AI** — **DeepSeek** primary, **Google Gemini 2.5 Flash** automatic fallback, behind one swappable `AIClient` interface.
- **Code execution** — **Judge0 CE** sandbox runs AI-generated test cases (Python, C++, Java, JS, TS, Go, Rust).
- **Async generation** — a curriculum request enqueues a `CurriculumJob`; a worker writes the `Course` → `Lesson` → `Challenge` documents, so the chat never blocks on generation.
- **Autonomous mentor** — drives the same generation tools through a provider-agnostic `[[ACTION: {…}]]` protocol, so a mid-conversation DeepSeek↔Gemini failover never corrupts the tool transcript.

---

## Repositories

| Repo | What's inside |
|---|---|
| [**SigmaLoop**](https://github.com/sigma-loop/SigmaLoop) | Umbrella repo — full technical book (`docs/`), AWS deployment kit, architecture specs |
| [**Backend**](https://github.com/sigma-loop/Backend) | Node.js + Express + TypeScript API, MongoDB, AI service layer, Judge0 integration |
| [**Frontend**](https://github.com/sigma-loop/Frontend) | React 19 + Vite SPA — mentor chat, challenge workspaces, onboarding |

<div align="center">
<sub>SigmaLoop · Master the Logic behind the Code</sub>
</div>
