# Golden-Section Search: Assignment Blueprint

## 1. Scope check

- Student: **Jonayed Mohiuddin (2105060)**
- Allocation calculation: `(060 mod 15) + 1 = 1`
- Topic 1: **Golden-Section Search**
- Course-note basis: five handwritten pages in `.local/course_notes/`
- Note convention: maximization of a unimodal function on `[x_L,x_U]`
- Final filenames: `2105060.pdf` and `2105060_LaTeX_Source.zip`

The deck will begin with the lecturer's maximization notation and then state the
minimization version explicitly. This avoids the common mistake of silently
switching the comparison inequalities.

## 2. Staged implementation plan

Each stage is intended to be a separate Git commit.

| Stage | Work product | Main acceptance check |
|---:|---|---|
| 1 | Repository setup and content blueprint | Topic, scope, slide story, and all ten problems are fixed before authoring |
| 2 | Beamer skeleton and visual system | Title/identity, section structure, footer, colors, and fonts compile cleanly |
| 3 | Core teaching slides | Unimodality, bracketing, update logic, pseudocode, and one iteration trace match the course notes |
| 4 | Advanced theory slides | Ratio derivation, evaluation reuse, error bound, convergence, complexity, robust stopping, and failure modes are rigorous |
| 5 | Five pure-mathematics problems and solutions | Exactly five problems, each immediately followed by a complete worked solution |
| 6 | Five real-life problems and solutions | Exactly five applications, each immediately followed by a complete worked solution |
| 7 | Visual polish and references | Original TikZ/PGFPlots figures, consistent notation, citations, and no overcrowded slides |
| 8 | Final validation and packaging | Clean rebuild, visual inspection of every page, correct filenames, and reproducible ZIP |

## 3. Planned slide story

The likely deck length is **35–39 slides**. The count is deliberately flexible
because a dense solution may need two frames; readability is more important
than forcing every calculation onto one slide.

### Opening and motivation (3 slides)

1. Title: topic, course, name, and student ID.
2. Why search without derivatives? A costly black-box objective and a bracket.
3. Learning outcomes and roadmap.

### Core method (7 slides)

4. Unimodality: the assumption that makes interval elimination valid.
5. Two interior probes and the maximization decision table.
6. Why symmetric arbitrary probes waste an evaluation.
7. Derivation of the reusable geometry and
   \(\tau=(\sqrt5-1)/2\approx0.618034\).
8. Golden-section algorithm for maximum and minimum.
9. Pseudocode with one new function evaluation per later iteration.
10. Worked iteration trace on a simple concave quadratic.

### Analysis and “wow factor” (8 slides)

11. Interval invariant and a short correctness argument.
12. Exact contraction: \(L_k=\tau^kL_0\).
13. A priori iteration count and midpoint location error
    \(|\hat x-x^*|\le L_k/2\).
14. What “linear convergence” means here; interval convergence versus
    objective-value convergence.
15. Function-call complexity: two initial calls, then one per iteration.
16. Golden section versus ternary search, Fibonacci search, and Brent's method.
17. Floating-point-safe implementation and a mixed absolute/relative stopping
    rule. Explain why \(2|(x_U-x_L)/(x_U+x_L)|\) is unsafe near zero.
18. Failure gallery: non-unimodality, noisy values, plateaus, wrong bracket,
    NaN/Inf values, and maximization/minimization inequality mix-ups.

### Modern extensions (2 slides)

19. Using the method as a derivative-free line search in several dimensions.
20. Practical adaptation for noisy or expensive simulations: caching,
    repeated samples, budgets, and diagnostic plots.

### Problem set (at least 20 slides)

21 onward. One problem frame followed immediately by its solution frame.
If a solution needs more room, it receives a second clearly labelled frame.

### Closing (2 slides)

- Summary: assumptions, invariant, rate, cost, and safe use.
- References and a compact implementation checklist.

## 4. Pure mathematical problem set

The numbers will be chosen so that hand work is visible and reproducible, not
just copied from program output.

1. **Derive the golden ratio used by the search.** Impose self-similarity after
   discarding one subinterval and solve the resulting quadratic. Reject the
   inadmissible root.
2. **Manual maximization trace.** Apply a fixed number of iterations to a
   concave quadratic, showing `[x_L,x_U]`, the two probes, function values, and
   the retained interval at every step.
3. **Worst-case error guarantee.** Given `L_0` and a target location error,
   derive the smallest iteration count using \(L_k=\tau^kL_0\), taking care
   with the sign of \(\log\tau\).
4. **Correctness proof from unimodality.** Prove why one discarded part cannot
   contain the minimizer (or maximizer) after comparing the two interior
   values, including the equality case.
5. **Edge-case analysis.** Diagnose a zero-centered bracket where the
   course-note relative stopping expression divides by zero, then design and
   apply a mixed absolute/relative criterion.

## 5. Real-life application problem set

Each application will reduce a plausible model to one scalar decision and will
state the units, feasible interval, modeling assumptions, and stopping rule.

1. **Economics — profit-maximizing price.** Maximize a nonlinear profit model
   over an admissible price interval and interpret the final bracket in taka.
2. **Chemical processing — reactor temperature.** Maximize a temperature-based
   yield model when derivatives are inconvenient or the yield comes from a
   simulator; include a safe operating bracket.
3. **Renewable energy — solar-panel tilt.** Maximize daily captured energy from
   a one-variable tilt model and discuss how measurement noise changes the
   stopping decision.
4. **Communications — antenna orientation.** Maximize a unimodal received-power
   model using only measured signal values; count physical measurements as
   function evaluations.
5. **Mechanical design — minimum-mass component.** Minimize a one-variable
   design objective with a penalty for violating performance, and explain why
   the chosen bracket must contain only one relevant minimum.

The five applications intentionally span different fields while exercising the
same core algorithm. At least one will be a minimization problem and at least
one will treat an evaluation as expensive, so the examples do not feel like
five cosmetic variations of a quadratic exercise.

## 6. Notation and numerical conventions

- Use \(x_L,x_U\) for interval endpoints and \(x_1<x_2\) for probes, matching
  the handwritten notes.
- Use \(\tau=(\sqrt5-1)/2\) for the contraction factor. Reserve
  \(\varphi=(1+\sqrt5)/2\), if mentioned, for the classical golden ratio, with
  \(\tau=1/\varphi\).
- State whether the current task is minimization or maximization before giving
  the comparison rule.
- Report a bracket and an uncertainty/error bound before rounding the final
  optimizer.
- Distinguish iteration count from function-evaluation count.
- Use enough digits internally; round only reported answers and explain the
  chosen precision.

## 7. Visual and writing direction

- Use a restrained academic theme: warm off-white background, deep navy text,
  and one muted gold accent connected to the topic.
- Draw mathematical figures in TikZ/PGFPlots so they remain editable in the
  submitted source archive.
- Use progressive overlays only for the central interval-elimination diagram;
  avoid animation for decoration.
- Prefer short explanations beside equations. Keep derivations readable over
  several frames instead of shrinking text.
- Include small interpretive remarks such as “what this bound actually tells
  us” and “where this assumption can fail.” These should reflect checked
  reasoning, not generic filler.
- Keep the student voice professional and direct; do not make unsupported
  claims about the method being universally best.

## 8. Source and verification plan

- Treat the supplied course notes as the notation and baseline-method source.
- Use standard numerical-optimization references for convergence and
  comparison claims; cite them on the relevant frames and in the reference
  slide.
- Independently recompute every iteration table and bound used in a solution.
- Compile from a clean tree, render the PDF pages, and visually inspect every
  frame for clipping, unreadable equations, accidental overlaps, and broken
  references.
- Build the ZIP from an explicit inclusion list, then extract it into a fresh
  temporary directory and compile again.

## 9. Final submission checklist

- [ ] The title slide says **Jonayed Mohiuddin** and **2105060**.
- [ ] The topic is Golden-Section Search only; comparisons remain supporting
      material rather than becoming separate topics.
- [ ] There are exactly five pure mathematical and five real-life problems.
- [ ] Every problem is followed immediately by its full solution.
- [ ] The PDF is named `2105060.pdf`.
- [ ] The archive is named `2105060_LaTeX_Source.zip`.
- [ ] The archive contains the main `.tex` file and every required asset.
- [ ] The archived source compiles into the submitted PDF.
- [ ] The two files are uploaded to the Moodle fields matching their visible
      labels; the announcement's link numbering is internally inconsistent, so
      the field labels should be checked at submission time.
