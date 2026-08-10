# Mathematical Dictionary: Quality Review

## Overall result

The dictionary is broad and contains many useful definitions, formulas, and theorem names. Its strongest entries give a short definition, a formula, an example, and a reason the idea matters.

The main quality problem is unevenness. Some entries are clear beginner-level definitions, while others are compressed research-level summaries. A reader may therefore find one idea easy to understand and the next one difficult even when the terms are closely related.

This review combines a complete structural scan with a targeted mathematical review of high-risk claims. The source was not modified.

## Audit facts

- The source contains **1,788 actual dictionary entries** beginning with `\\term{...}`.
- The README claims **1,554 entries**, so that number is out of date.
- There are **seven entries whose entire definition is only a cross-reference** such as `See \\term{...}`.
- There are **296 alphabetical-order violations** when labels are compared within their files after ignoring punctuation and case.
- The source compiles successfully with `latexmk` to a **152-page PDF**.
- `chktex` reports many style warnings, especially dash lengths, quotation marks, parentheses, and one unmatched-bracket warning around the source's long entry list.
- Several entries are much longer than the stated concise dictionary style and read like mini-articles.

## Priority findings

### Critical: `Borel Set` is too broad

**Location:** `chapters/dict_b.tex:82–83`

The entry says that Borel sets are measurable for every measure on the real numbers. This is false as written. A measure is defined on a particular collection of sets, called its sigma-algebra. That collection does not have to contain every Borel set.

**Plain explanation:** Borel sets are the sets made from open intervals using countable unions, countable intersections, and complements. They are measurable for the usual Borel or Lebesgue measure, but a different measure may be defined on a smaller sigma-algebra.

**Suggested wording:**

> A Borel set is a set obtained from open sets by countable unions, countable intersections, and complements. The Borel sets form the smallest sigma-algebra containing all open sets. They are measurable for any measure whose domain contains the Borel sigma-algebra, including Borel and Lebesgue measure.

**Application:** Borel sets provide the standard language for describing events in probability and regions in analysis. For example, intervals such as `[0,1]`, open sets, and countable combinations of them can be assigned probabilities or lengths.

### Critical: the compactness entry contains a false claim

**Location:** `chapters/dict_c.tex:211–212`

The entry says that compact spaces are “Hausdorff exactly when they are normal.” This is not a correct general characterization. Compactness and Hausdorffness are different properties; a compact space need not be Hausdorff, and normality also depends on the convention being used.

**Plain explanation:** A compact space is one where every open cover has a finite subcover. In Euclidean space, this is equivalent to being closed and bounded. A compact Hausdorff space has especially useful properties, such as every continuous real-valued function attaining a maximum and minimum, but Hausdorffness should be stated as an additional assumption.

**Suggested wording:**

> A topological space is compact if every open cover has a finite subcover. In `R^n`, the Heine–Borel theorem says that compactness is equivalent to being closed and bounded. If the space is also Hausdorff, continuous real-valued functions attain their maximum and minimum values, and compact subsets are closed.

**Application:** Compactness is used to prove that an optimization problem has a solution. A continuous cost function on a closed and bounded feasible region in Euclidean space must reach its smallest value.

### Major: `Moment (Statistics)` confuses moments with standardized measures

**Location:** `chapters/dict_m.tex:142–143`

The entry says that the second moment is variance, the third is skewness, and the fourth is kurtosis. This is not generally correct. Variance is the second **central** moment; skewness and kurtosis are standardized versions of the third and fourth central moments.

**Plain explanation:** The raw `k`th moment is usually `E[X^k]`. The central `k`th moment is `E[(X-mu)^k]`. Variance is the second central moment. Skewness divides the third central moment by the standard deviation cubed, and kurtosis divides the fourth central moment by the variance squared.

**Suggested wording:**

> A moment is a numerical summary of a probability distribution. The raw `k`th moment is `E[X^k]`; the `k`th central moment is `E[(X-mu)^k]`. The second central moment is the variance. Standardized third and fourth central moments describe skewness and kurtosis.

**Application:** Moments help compare data sets. The mean describes location, variance describes spread, skewness describes asymmetry, and kurtosis describes the relative weight of the tails.

### Major: `V-statistic` is incorrectly defined

**Location:** `chapters/dict_v.tex:97–98`

The entry calls a V-statistic a “la Place-style statistic” and describes it as a generalization of variance and covariance. That is not the standard meaning.

**Plain explanation:** A V-statistic is an average of a function over all ordered tuples of observations, allowing repeated observations. For a kernel `h` of `m` variables, it has the form `n^{-m} sum h(X_i1,...,X_im)` over all indices. U-statistics are closely related, but they average only over distinct indices.

**Application:** V-statistics are used to estimate quantities such as moments, dependence measures, and goodness-of-fit statistics from data.

### Major: `Modular Group` identifies the wrong object

**Location:** `chapters/dict_m.tex:130–131`

The entry calls `PSL(2,Z)` the group of all determinant-one integer matrices. The determinant-one matrices form `SL(2,Z)`. `PSL(2,Z)` is the quotient of `SL(2,Z)` by the subgroup `{I,-I}`.

**Plain explanation:** Two matrices that differ only by a sign act in the same way on the upper half-plane by a fractional-linear transformation. The quotient identifies these two matrices, which is why the projective group is written `PSL`.

**Suggested wording:**

> The modular group is `PSL(2,Z) = SL(2,Z)/{I,-I}`, where `SL(2,Z)` consists of the two-by-two integer matrices with determinant 1. It acts on the upper half-plane by `z -> (az+b)/(cz+d)` and is central in the theory of modular forms and hyperbolic surfaces.

**Application:** Modular forms use this group’s symmetries to study functions with strong arithmetic structure. These ideas appear in elliptic curves, number theory, and some cryptographic constructions.

### Major: `Modular Form` omits the transformation law

**Location:** `chapters/dict_m.tex:127–128`

The definition says that a modular form transforms “in a specific way” but does not state that way. This makes the central property impossible to check.

**Plain explanation:** A modular form of weight `k` satisfies `f((az+b)/(cz+d)) = (cz+d)^k f(z)` for matrices in the relevant modular group, and it must also be holomorphic at the cusps. The weight is part of the definition.

**Application:** Fourier coefficients of modular forms encode arithmetic information, including information about elliptic curves and solutions to counting problems.

### Major: `Fibrant Object` makes a false general claim

**Location:** `chapters/dict_f.tex:37–38`

The entry says that weak equivalences between fibrant objects are homotopy equivalences. In a general model category, cofibrancy is also needed for the usual conclusion that a weak equivalence has a homotopy inverse.

**Plain explanation:** Fibrant objects have good lifting properties toward the terminal object. To turn a weak equivalence into an actual homotopy equivalence, one normally works with objects that are both fibrant and cofibrant, or adds suitable hypotheses.

**Application:** Fibrant and cofibrant replacements allow homotopy theory to work with complicated objects by replacing them with better-behaved ones without changing their essential homotopy information.

### Major: `Flat Module` says every flat module over a local ring is free

**Location:** `chapters/dict_f.tex:97–98`

The statement is too strong for arbitrary modules. A finitely presented flat module over a local ring is free; an arbitrary flat module need not be free.

**Plain explanation:** Flatness means that tensoring with the module preserves exact relationships. It is a weaker condition than being free. Freeness follows under additional finiteness assumptions.

**Application:** Flat modules are useful in algebraic geometry because flat families have fibers that behave consistently as parameters change. They are also used to transport equations and exact sequences between rings.

### Major: `Phase Space` contains corrupted text

**Location:** `chapters/dict_p.tex:101`

The phrase “with plot coordinates asCanadian position and momentum” is visibly corrupted and makes the sentence unusable.

**Suggested wording:**

> Phase space is the space of all possible states of a physical system. In classical mechanics, a point usually records both position and momentum. As the system evolves, the point moves through phase space. Hamiltonian motion preserves phase-space volume, a fact known as Liouville’s theorem.

**Application:** Phase space lets physicists study the motion of a system as a geometric path. It is used for planetary motion, gases, control systems, and statistical mechanics.

### Major: `Cauchy Integral Theorem` is duplicated under several names

**Location:** `chapters/dict_c.tex:52–66`

`Cauchy Integral Theorem`, `Cauchy's Integral Theorem`, and `Cauchy's Theorem` repeat essentially the same result. This creates inconsistent cross-referencing and wastes space.

**Plain explanation:** Keep one main entry with the standard name and use short cross-references for the alternatives. The main entry should state the needed condition that the curve is null-homotopic in the domain, or use the standard simply connected-domain version.

**Application:** The theorem says that integrating a holomorphic function around a suitable closed loop gives zero. It is the basis for contour integration, Cauchy’s integral formula, residue calculations, and many results in complex analysis.

### Major: `Poincaré Recurrence Theorem` should state its measure assumptions

**Location:** `chapters/dict_p.tex:160–161`

The theorem’s definition should make clear that it applies to a measure-preserving transformation on a finite-measure space, or to a finite invariant measure. Without this condition, recurrence is not guaranteed.

**Application:** The theorem explains why an isolated physical system with finite accessible volume can return arbitrarily close to an earlier state, at least in the mathematical idealization.

### Moderate: `Schwarz Space` is a spelling error and duplicates `Schwartz Space`

**Location:** `chapters/dict_s.tex:55–56 and 58–59`

The standard name is **Schwartz space**, after Laurent Schwartz. The misspelled entry should redirect to the correctly spelled entry. The corrected entry should define the decay condition using seminorms or a plain-language description.

**Application:** Schwartz space is the natural setting for Fourier transforms because both a function and its Fourier transform remain smooth and rapidly decreasing. It is used in signal processing and distribution theory.

### Moderate: `Borel Measure` overstates regularity

**Location:** `chapters/dict_b.tex:79–80`

The regularity claims need hypotheses and more careful terminology. Not every finite Borel measure on every stated space has all the listed regularity properties in the same form.

**Application:** Regularity is what lets a measure be approximated by open or compact sets, which is essential when proving integration and approximation results.

### Moderate: `Zygmund Class` is incomplete

**Location:** `chapters/dict_z.tex:31–32`

The displayed condition should specify the domain, the range of `h`, and the constant `C`; the missing scale factor and precise convention can change the class being described.

**Plain explanation:** A Zygmund condition controls the second difference `f(x+h)+f(x-h)-2f(x)`. It measures a form of smoothness that is close to, but not identical with, Lipschitz continuity.

**Application:** Zygmund classes are used to study how well functions can be approximated by Fourier series and how singularities behave in harmonic analysis.

### Moderate: `Maximum Modulus Principle` is imprecise

**Location:** `chapters/dict_m.tex:58–59`

“Attains its maximum modulus only on the boundary” is not the best statement. A nonconstant holomorphic function has no interior local maximum of its modulus. A maximum on a compact closure, when one exists, occurs on the boundary.

**Application:** This principle is used to prove uniqueness of analytic functions, estimate solutions of complex equations, and establish the Schwarz lemma.

### Moderate: `Eccentricity` combines two unrelated definitions

**Location:** `chapters/dict_e.tex:4–5`

The conic-section meaning and graph-theory meaning should be separated or explicitly labeled. The current entry can make a reader think that the two quantities are related.

**Application:** Conic eccentricity classifies circles, ellipses, parabolas, and hyperbolas. Graph eccentricity measures how far a vertex is from the most distant vertex and is used in network analysis.

### Moderate: `Cayley's Theorem` has a misleading motivation sentence

**Location:** `chapters/dict_c.tex:67–68`

The theorem correctly embeds every group into a permutation group, but the sentence saying this “justifies the study of permutation groups as the primary tool for understanding all groups” is a broad historical claim rather than part of the theorem. It should be removed or labeled as context.

**Application:** The result lets abstract group calculations be represented as permutations, making concrete examples and computer computations possible.

### Moderate: `Runge's Theorem` needs the connected-complement condition

**Location:** `chapters/dict_r.tex:70–71`

The rational approximation statement depends on the geometry of the compact set and on where poles are allowed. The entry should state the relevant connected-complement condition for polynomial approximation, or clearly state the rational-function version with its hypotheses.

**Application:** Runge approximation is used to replace complicated analytic functions by rational functions that are easier to compute and manipulate.

### Moderate: `Elliptic Curve` omits the discriminant condition

**Location:** `chapters/dict_e.tex:76–77`

The equation `y^2 = x^3 + ax + b` describes an elliptic curve only when the cubic has no repeated root, equivalently when `4a^3+27b^2 != 0` over the usual characteristic assumptions. The curve also needs a specified base field and a chosen point at infinity.

**Application:** Elliptic curves are used in public-key cryptography, integer factorization, and the study of rational solutions to equations.

### Minor: `Z-module` and `Abelian Group` should cross-reference consistently

These ideas are equivalent: a module over the integers is exactly an abelian group. The dictionary should make this equivalence explicit in both directions and avoid treating them as unrelated entries.

### Minor: prose and LaTeX consistency

The source has recurring issues that do not usually change the mathematics but reduce polish:

- `Schwarz` should be `Schwartz`.
- Use consistent `--` or `---` dash conventions.
- Replace straight quotation marks with LaTeX quotation marks.
- Review unmatched or confusing parentheses and brackets reported by `chktex`.
- Correct grammatical fragments such as “Theorem that...” where a complete sentence would be clearer.
- Choose one spelling convention for terms such as “optimization/optimisation” and “characterize/characterise.”
- Avoid unexplained research-level names in a beginner-facing definition unless the named result is explained or linked.

## Structural recommendations

1. Update the README count to 1,788, or generate the count automatically during the build.
2. Keep one main definition for each concept and make alternative names short cross-references.
3. Reorder entries alphabetically within every chapter. The current 296 violations make lookup harder.
4. Add a consistent optional final sentence beginning with “Application:” for important terms.
5. Use a three-level entry style:
   - one-sentence definition;
   - formula or simple example;
   - application or connection to a related idea.
6. Review very long entries for splitting into a definition plus a separate theorem or application entry.
7. Add automated checks for duplicate labels, cross-reference targets, alphabetical order, malformed LaTeX, and stale entry counts.

## Validation performed

- `latexmk -pdf -interaction=nonstopmode -halt-on-error math_dictionary.tex`: passed.
- Output: 152-page PDF generated in a temporary directory.
- `chktex`: completed and reported style warnings, including dash usage, quotation marks, parentheses, and bracket matching.
- No dictionary source files were modified by this review.
