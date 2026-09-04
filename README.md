# Repository 3 — Quispe & Xu (2026)

Repository: https://github.com/wbgradost/ai-03-quispe

Paper: Alexander Quispe and Kevin Xu, *Agentic Delegation and the Language Frontier of Software Developers: A Model and Evidence from Claude Code on GitHub*, arXiv:2605.25438v2 (v1: 25 May 2026; v2: 7 July 2026).

## Question, agent and mechanism

The paper asks whether agentic coding assistance expands the programming-language set in which a developer can produce. This is a **production frontier**, not a skill frontier: shipping Rust through delegation does not imply writing Rust unassisted.

For each developer-language-month, the developer chooses the mode with highest certainty-equivalent surplus and activates the language if that surplus is nonnegative. Before adoption, $\mathcal M_1=\{S,C\}$ (solo, conversational); afterward, $\mathcal M_2=\{S,C,D\}$ adds delegation. For an unfamiliar language, Assumption 1 makes conversational assistance leave the solo threshold unchanged. Define

$$B=T^S-T^D=\lambda[az(A)-s\mu]-\kappa(a,s)-r_D+\frac{\rho}{2}\left[\frac{(2\lambda-\lambda^2)s^2}{\pi}-\sigma_D^2(a,s,A)\right].$$

If $B>0$, opportunities in $[T^D,T^S)$ become feasible only with delegation. Agent capability affects execution, verification costs and error risk; the developer supplies general specification-and-verification ability.

## Results and independent check

Menu inclusion gives $Z^2\ge Z^1$ and $N^2\ge N^1$ path by path. For an unfamiliar language satisfying Assumption 1 and $B>0$,

$$Z^2-Z^1=\mathbf 1\{T^D\le\omega<T^S\}.$$

With continuous $F$, activation probability is $F(T^S)-F(T^D)$. Proposition 3 gives

$$\Delta C_i(s)=\sum_{k\in\mathcal U_i}[(1-p^1_{ik})^{s+1}-(1-p^2_{ik})^{s+1}]\ge0$$

when $0\le p^1_{ik}\le p^2_{ik}\le1$. Our independent endpoint check finds that the paper's strict-growth/strict-concavity claim under $p^1=0<p^2$ fails at $p^2=1$: then $\Delta(s)=1$ for every $s\ge0$. Strictness requires $0<p^2<1$ and a nonempty relevant candidate set.

## Evidence, identification and comparison

The panel has 5,346 developers and 149,688 developer-months, built from 3.15 million commits and 57.2 million changed files. Doubly robust staggered-adoption event studies find at adoption: active languages $+2.53$, newly used $+1.19$, entropy $+0.382$, cumulative breadth $+1.604$. Robustness checks address mechanical counting and activity composition. These are event-time associations, not definitive causal effects: voluntary adoption may coincide with an unobserved new-project shock.

Quispe–Xu model AI as a delegated-execution option lowering language-specific entry thresholds. Aouad–Lykouris–Zhong model AI, skill and effort as perfectly substitutable inputs, allowing AI to crowd out effort and generate deskilling. The opposite predictions reflect extensive-margin menu expansion versus intensive-margin substitution.

## Lean status — PARTIAL / scaffold not created

**Initial blocker.** In the first delivery, Elan, Lean and Lake were unavailable and native Windows Python failed on the Unix-only `fcntl` dependency.

**Final Lean run (our execution).** The second phase ran from `/home/william/EconCSLib` under WSL. `paper_contribution.py doctor` verified Python 3.14.4, Git, Lake 5.0.0 and Lean 4.30.0-rc2; only optional `pdftotext` and `latexmk` were missing. The exact arXiv v2 TeX archive was kept outside both public repositories and pinned by SHA-256. A private statement spec inventoried Propositions 1--5, splitting Proposition 3 into its weak and printed-strict clauses.

The official `new` command then failed during Spec validation because the root `EconCSLib` module had not yet been built. The generator rolled back `papers/QX26AgenticDelegation/`. A base-library build made substantial progress but was stopped on instruction before completion. Consequently the immediate fast check returned exactly:

```text
error: could not read papers/QX26AgenticDelegation/status.json: [Errno 2] No such file or directory: '/home/william/EconCSLib/papers/QX26AgenticDelegation/status.json'
```

There is therefore no generated paper folder to copy into `lean/`. No Lean theorem proof was completed, no PASS is claimed, and nothing came from the worked example. The source archive and statement spec remain private.

## Proposition 3 fidelity verdict

The printed weak inequality is valid for hazards satisfying $0\le p^1\le p^2\le1$. In the closed-frontier case $p^1=0$, the increment is

$$\Delta C(s+1)-\Delta C(s)=p^2(1-p^2)^{s+1}.$$

Thus strict growth holds for $0<p^2<1$, but fails at the source-permitted endpoint $p^2=1$. Strict concavity has the same endpoint problem. Aggregated strictness also needs a nonempty unfamiliar-language set with at least one interior hazard. This is an independent mathematical/fidelity finding, not a compiled Lean result.

The handwritten derivation is included at `hand/prop3-endpoint.jpg`. `presentation.pdf` was generated from `presentation.tex` with MiKTeX `pdflatex` in two passes; the PDF contains nine slides, including the handwritten derivation. The separate `latexmk` command was unavailable because its Perl engine was missing, but this did not block direct PDF generation or the Lean checks.
