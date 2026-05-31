# R language notes, code anatomy, and demo notebook styling

How students learn **enough R to express statistical ideas** in a five-module async course — without treating R as the main subject.

**Index:** [README.md](README.md) · **Plan:** [../ASYNC_REVISION_PLAN.md](../ASYNC_REVISION_PLAN.md) · **Hidden knowledge:** [make-hidden-knowledge-visible.md](make-hidden-knowledge-visible.md)

---

## Philosophy

Students forget syntax. They remember **`mean(x)`** if it’s on a sheet they built with the course.

The bottleneck is not learning the whole language. It is learning enough R to support:

- World We Observe → World We Imagine → World of Computers ([instructor-videos.md](instructor-videos.md))

**Most useful single resource:** the **code reference sheet** students co-build (`r-reference.qmd` + per-module **R Language Notes**).

External video series are supplements ([colab-r-companion-resources.md](colab-r-companion-resources.md)). **Code anatomy** (below) matches this course’s teaching style better than generic R tutorials.

---

## Demo vs student notebooks

| Notebook | Color / anatomy styling | Purpose |
|----------|-------------------------|---------|
| **Demo** (`lab-*-demo.ipynb`, instructor Colab) | **Yes** — [code anatomy colors](make-hidden-knowledge-visible.md) (blue/green/red/purple) | Teach how to read R; “change this” in red |
| **Student** (`lab-*-student.ipynb`) | **No** — plain code | Students write their own names and answers |

Apply styling only in **demo** notebooks linked from lab pages. Student notebooks stay clean so learners aren’t copying instructor-specific colors as if they were R syntax.

When a lab has demo only (no student file), students duplicate the demo in Colab — still avoid heavy styling in anything labeled “duplicate and fill in”; keep styling in the **walk-through demo** link only.

---

## Color coding in demo notebooks (code anatomy)

Teach **how to read R** — distinct from [three worlds lecture colors](three-worlds-visual-language.md) (statistical concepts in prose).

| Color | Meaning in **code** |
|-------|---------------------|
| **Blue** | R functions and syntax (`mean`, `<-`, `~`, `()`) |
| **Green** | User-created names (variables, datasets) |
| **Red** | Values or placeholders **students should modify** |
| **Purple** | Important output or statistics |

**Demo legend** (markdown cell at top of each demo):

- Blue: leave unchanged (R syntax and functions)
- Green: names you created earlier
- Red: change for your data or question
- Purple: read the output carefully

**Student notebooks:** plain code only — no instructor color legend.

Full rationale: [make-hidden-knowledge-visible.md](make-hidden-knowledge-visible.md).

### Implementation options (when building demos)

Pick one convention and use it consistently:

1. **Code anatomy markdown** (below) — markdown cell after each important code chunk (works everywhere; no special Colab setup).
2. **HTML-colored markdown** — demo-only markdown showing the same line with `<span style="color:...">` (demo notebooks only).
3. **Leading comments in demo code** — e.g. `# ↳ your name`, `# ↳ R function`, `# ↳ change for your data` (accessible; prints if run — use sparingly).
4. **Notebook CSS** (advanced) — single markdown cell at top of **demo** `.ipynb` with `<style>` targeting code (test in Colab R kernel).

Document the legend once at the top of each demo notebook.

---

## Code anatomy (teaching pattern)

After important code in **demos** or **R Language Notes**, break the line apart:

```text
lm(y ~ x, data = mydata)
```

| Part | Role |
|------|------|
| `lm` | regression function |
| `y` | response variable |
| `x` | explanatory variable |
| `mydata` | dataset (your choice of name) |

Use this pattern in:

- Demo notebook markdown cells
- Per-module **R Language Notes** pages (public site)
- Optional callouts in `projects/project-N.qmd` when introducing new functions

---

## R Language Notes — one page per module

Create **one public page per project module** (Modules 1–5). Short. Functions + one anatomy example each. Link from course path, module hub, and `r-reference.qmd`.

Suggested paths (when implemented):

| Module | Page (draft) | Functions to feature |
|--------|----------------|----------------------|
| 1 | `r-notes/module-1.qmd` | `sum()`, `mean()`, `dbinom()`, `pbinom()` |
| 2 | `r-notes/module-2.qmd` | `t.test()`, `mean()`, `sd()` |
| 3 | `r-notes/module-3.qmd` | `ggplot()`, `filter()`, `select()`, `summarise()`, `read_csv()` |
| 4 | `r-notes/module-4.qmd` | `group_by()`, `summarise()`, `filter()` |
| 5 | `r-notes/module-5.qmd` | `lm()`, `predict()` |

Module 0 links to Colab orientation + overview of the reference sheet — not a full function list.

Each page should include:

- Big question for that module (matches project)
- Function list with **one-line purpose**
- **Code anatomy** for the most important new line
- Link to relevant lab demo + [companion resources](colab-r-companion-resources.md)
- **“Add to Artifact 2 (R reference)”** callout ([portfolio-artifacts.md](portfolio-artifacts.md))

### Relationship to `r-reference.qmd`

| Asset | Role |
|-------|------|
| **`r-reference.qmd`** | Course-wide sheet; pipeline; functions accumulated across modules |
| **`r-notes/module-N.qmd`** | **Module entry point** — only what’s new that module |
| **Posit cheatsheets** | Source material when expanding reference ([companion doc](colab-r-companion-resources.md)) |

Students “build” the reference by using module notes + their notebooks; async version can say “add this module’s functions to your personal sheet.”

---

## Where to incorporate (editing checklist)

| Location | Action |
|----------|--------|
| `r-reference.qmd` | Trim live-course scope; add links to `r-notes/module-N.qmd`; async module framing |
| New `r-notes/module-*.qmd` (5 pages) | Create per table above; add to `_quarto.yml` nav under Resources |
| `labs/lab-*-demo.ipynb` | Color/anatomy in **demo only** |
| `labs/lab-*-student.ipynb` | Plain code; prompts/blanks |
| `labs/lab-N.qmd` | Link demo + student + module R Language Notes |
| `projects/project-N.qmd` | Link module R notes; anatomy for project-critical code |
| `schedule.qmd` (course path) | Link each module’s R Language Notes page |

---

## Affects (for plan)

- **Public site:** new `r-notes/` pages, revise `r-reference.qmd`, lab/project cross-links
- **Notebooks:** demo `.ipynb` styling only (not student)
- **Canvas:** optional External URL to module R notes page
- **Phase:** Module 0 (reference framing) + each Module 1–5 when editing that module’s labs/projects
