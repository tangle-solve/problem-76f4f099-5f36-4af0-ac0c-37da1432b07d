<!-- solve-problem:76f4f099-5f36-4af0-ac0c-37da1432b07d -->
# Superpolynomial AC⁰[p]-Frege lower bounds

A [Tangle Solve problem](https://solve.tangle.tools/problems/76f4f099-5f36-4af0-ac0c-37da1432b07d).

## What is the problem?

Prove that there exist explicit families of tautologies requiring superpolynomial-size proofs in **AC⁰[p]-Frege** proof systems — bounded-depth Frege systems extended with modular counting gates MOD_p (a gate outputs true iff the number of true inputs is ≡ 0 mod p, for a fixed prime p, typically p = 2).

**Formal setting.** A Frege system is a sound, implicationally complete propositional proof system with finitely many inference rules over formulas (e.g., modus ponens). AC⁰[p]-Frege restricts formulas in proofs to depth-d (constant) formulas over ∧, ∨, ¬, and MOD_p gates, with unbounded fan-in; the size of a proof is total symbol count. The problem: exhibit an explicit family {τ_n} of tautologies (e.g., τ_n ∈ {0,1}^{poly(n)}, constructible in poly time) such that any AC⁰[p]-Frege proof of τ_n has size n^{ω(1)} (ideally 2^{n^{Ω(1)}}), for each fixed depth d and prime p.

The case p absent (ordinary AC⁰-Frege) is solved: Ajtai, and independently Krajíče–Pudlák–Woods, and Pitassi–Beame–Impagliazzo, proved exponential lower bounds for the pigeonhole principle (PHP). With MOD_p gates, no superpolynomial lower bound is known for any natural tautology family. Note the important special case p = 2: AC⁰[2]-Frege (Frege with parity gates) is already open; the case of general prime p is expected to be reducible in difficulty to p = 2 via Razborov–Smolensky-style simulation arguments (verify the exact simulation).

## Why does it matter?

This is arguably the central open problem in proof complexity, blocking the LC-type program of proving lower bounds for increasingly strong proof systems toward NP ≠ coNP. Superpolynomial AC⁰[p]-Frege lower bounds would be the first progress beyond techniques from the 1990s, would separate AC⁰[p]-Frege from any stronger system (e.g., TC⁰-Frege or Frege itself, via witnessing short proofs of the hard tautology in the stronger system), and would settle the proof-complexity status of counting-based reasoning about combinatorial principles like PHP and mod-p counting principles. It also bears on whether modular counting circuits, which are strictly more powerful than AC⁰, require genuinely new lower-bound technology.

## What's already known?

- **AC⁰-Frege:** exponential lower bounds for PHP (Ajtai 1988; Krajíček–Pudlák–Woods; Pitassi–Beame–Impagliazzo), via switching lemmas and adversary/restrictive argument methods. These fail in the presence of MOD_p gates because random restrictions do not simplify MOD_p gates.
- **Circuit lower bounds:** Razborov (1987) and Smolensky (1987) proved exponential lower bounds for AC⁰[p] *circuits* computing MOD_q (q ≠ p prime) via the polynomial method (approximate degree). This gives lower bounds for the corresponding *truth-table complexity*, but circuit lower bounds do not automatically lift to proof-complexity lower bounds: proofs are manipulated by sound inference rules, and standard switching-lemma machinery breaks.
- **Proofs with modular reasoning:** the *counting principle* Count_p ("no partition into p-element blocks of a set whose size is not divisible by p") is the natural candidate hard tautology, since it separates from AC⁰-Frege: Ajtai (1990) and Beame–Pitassi (1995) showed Count_p needs exponential-size AC⁰-Frege proofs — but Count_p has *short* proofs once MOD_p reasoning is native, so it is not the candidate against AC⁰[p]-Frege.
- **Partial progress:** lower bounds for AC⁰[p]-Frege proof systems are known only with further restrictions, e.g., bounded bottom fan-in ("AC⁰[p]-Frege with small bottom fan-in"), constant-depth proofs of the weak pigeonhole principle over counting-mod-q domains, and results of Krajíček (2019) surveying these; Li–Tzameret–Wang (2015) proved lower bounds for a subsystem related to non-commutative/algebraic reasoning (verify exact statement). No tautology family is known superpolynomially hard for unrestricted AC⁰[p]-Frege.

## What would count as solving it?

1. **Full solution:** an explicit tautology family {τ_n} and a proof that any depth-d, size-S AC⁰[2]-Frege proof of τ_n forces S ≥ n^{f(d)} with f(d) → ∞ (superpolynomial for each fixed d), or 2^{n^{Ω(1)}} for exponential strength.
2. **p ≠ 2 case:** the same for AC⁰[p]-Frege, p any fixed prime.
3. **Partial results of real interest:** (a) superpolynomial lower bounds for AC⁰[2]-Frege restricted to some nontrivial subclass beyond bottom-fan-in (e.g., restricted number of modular gates); (b) lifting Razborov–Smolensky circuit lower bounds to proofs of MOD_q-tautologies in any subsystem capturing MOD_q reasoning; (c) a proof that AC⁰[p]-Frege lower bounds follow from some well-stated algebraic or communication-complexity conjecture.
4. Referee criterion: a rigorous induction on proof structure showing every proof of τ_n of depth d has size n^{ω(1)}, handling arbitrary inference schemas of the fixed Frege rule set.

## How to start

1. **Read first:** Krajíček, *Proof Complexity* (2019), the chapters on AC⁰[p]-Frege and the Razborov–Smolensky method; then Beame–Pitassi's survey "Propositional Proof Complexity: Past, Present, and Future" for the AC⁰-Frege PHP proof and where it breaks with MOD gates.
2. **Natural approach:** mimic the PHP lower bound but replace switching lemmas with polynomial approximations. The core obstacle: after approximating each line by a low-degree polynomial over 𝔽_p, inference rules do not preserve approximation — a proof line's approximation error compounds along the proof dag, and there is no known "degree-reduction" analogue of switching lemmas that is sound for proof encodings.
3. **Concrete subgoal:** prove a lower bound for AC⁰[2]-Frege with ≤ n^{ε} parity gates, interpolating between known bounded-bottom-fan-in results and the full problem.
4. Consider candidate tautologies: MOD_q principles over structures, or the "mod-p counting version of PHP" (no injection mod p), i.e., principles expressing counting facts not captured by native MOD_p reasoning.

## Key references

- S. Buss (ed.) / J. Krajíček, *Proof Complexity*, Cambridge University Press, 2019. — Monograph covering AC⁰[p]-Frege, the state of modular-counting proof lower bounds, and known partial results. (No stable URL; check CUP.)
- A. Razborov, "Lower bounds on the size of bounded-depth networks over a complete basis with logical addition," *Mathematical Notes of the Academy of Sciences of the USSR* 41 (1987). — Introduces the approximation/polynomial method giving AC⁰[2] circuit lower bounds for MOD₃.
- R. Smolensky, "Algebraic methods in the theory of lower bounds for Boolean circuit complexity," *STOC 1987*. — Extends Razborov's method to AC⁰[p] circuits vs. MOD_q via polynomial representations over 𝔽_p.
- M. Ajtai, "The complexity of the pigeonhole principle," *Combinatorica* 14 (1994); with Krajíček–Pudlák–Woods and Beame–Pitassi (announced 1988–92). — Exponential AC⁰-Frege lower bound for PHP, the baseline technique.
- P. Beame and T. Pitassi, "Propositional Proof Complexity: Past, Present, and Future," *Bulletin of the EATCS*, 1998. — Survey explaining AC⁰-Frege lower-bound machinery and the open AC⁰[p] case. https://eccc.weizmann.ac.il/eccc-reports/1998/TR98-067/
- Y. Li, I. Tzameret, and G. Wang? — "(verify)": the census cites "Li–Tzameret–Wang (2015)"; the closest known work is Li, Tzameret, and collaborators on non-commutative/algebraic proof systems and their separations; the solver should locate the exact paper before relying on it.
- M. Ajtai, "The independence of the modulo-p counting principles," *COLT/STOC-era papers, ~1990*. — Shows Count_p tautologies are hard for AC⁰-Frege but short-provable with modular reasoning.

## Warnings

- Do not confuse *circuit* lower bounds (solved by Razborov–Smolensky) with *proof* lower bounds (open). A common wasted effort is re-proving MOD_q ∉ AC⁰[p] and expecting it to lift.
- The obvious hard tautology candidates (Count_p, PHP) fail or are unproven candidates: Count_p has short AC⁰[p]-Frege proofs; PHP's status vs. AC⁰[p]-Frege is itself open and may be the right candidate — be precise about which principle you target.
- Random restrictions do not shrink MOD_p gates; any switching-lemma transplantation must be redesigned (e.g., via "modular switching" à la Williams-style ACC circuit analysis — this connection is speculative, verify).
- The exact strength of "p = 2 vs. general p" reductions between systems should be verified before assuming the prime-2 case suffices.
- The census record's citation "Li–Tzameret–Wang (2015)" could not be confidently matched to a specific paper; verify before use.

---
*`ALGO-000064` · flagged for review*

## Acceptance guidance

1. **Full solution:** an explicit tautology family {τ_n} and a proof that any depth-d, size-S AC⁰[2]-Frege proof of τ_n forces S ≥ n^{f(d)} with f(d) → ∞ (superpolynomial for each fixed d), or 2^{n^{Ω(1)}} for exponential strength.
2. **p ≠ 2 case:** the same for AC⁰[p]-Frege, p any fixed prime.
3. **Partial results of real interest:** (a) superpolynomial lower bounds for AC⁰[2]-Frege restricted to some nontrivial subclass beyond bottom-fan-in (e.g., restricted number of modular gates); (b) lifting Razborov–Smolensky circuit lower bounds to proofs of MOD_q-tautologies in any subsystem capturing MOD_q reasoning; (c) a proof that AC⁰[p]-Frege lower bounds follow from some well-stated algebraic or communication-complexity conjecture.
4. Referee criterion: a rigorous induction on proof structure showing every proof of τ_n of depth d has size n^{ω(1)}, handling arbitrary inference schemas of the fixed Frege rule set.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/76f4f099-5f36-4af0-ac0c-37da1432b07d?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000064.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000064)
