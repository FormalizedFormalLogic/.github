<h1 align="center">Formalized Formal Logic</h1>

<p align="center">
Formalize formal logic (mathematical logic) in <a href="https://lean-lang.org">Lean Theorem Prover</a>.
</p>

## Summary

Our [Book] provides summaries of formalized concepts, theorems, propositions and brief explainations. (**In progress**)

[Book]: https://formalizedformallogic.github.io/Book

### Main Results

Main results of this project. More results and details on [Book].

#### Classical Propositional Logic

- [Soundness](https://formalizedformallogic.github.io/Foundation/docs/Logic/Propositional/Classical/Basic/Completeness.html#LO.Propositional.Classical.soundness) and [Completeness](https://formalizedformallogic.github.io/Foundation/docs/Logic/Propositional/Classical/Basic/Completeness.html#LO.Propositional.Classical.completeness)

#### Classical First-Order Logic and Arithmetics

- [Completeness][FO-Completeness]
- [Cut-Elimination of First-Order Sequent Calculus _(Gentzen's Hauptsatz)_](https://formalizedformallogic.github.io/Foundation/docs/Logic/FirstOrder/Hauptsatz.html#LO.FirstOrder.Derivation.hauptsatz)
- [Gödel's First Incompleteness Theorem][Goedel-IT1]

[FO-Completeness]: https://formalizedformallogic.github.io/Book/first_order/completeness.html
[Goedel-IT1]: https://formalizedformallogic.github.io/Book/first_order/goedel1.html

#### Basic Modal Logic

- [Completeness of Kripke Semantics][BML-Kripke-Completeness]
- Filteration Methods
- [Gödel-Mckinsey-Tarski Theorem][GMT-Theorem] and [Modal Companion][Modal-Companion]

[BML-Kripke-Completeness]: https://formalizedformallogic.github.io/Book/standard_modal/kripke_completeness.html
[GMT-Theorem]: https://formalizedformallogic.github.io/Book/standard_modal/modal_companion.html#g%C3%B6del-mckensey-tarski-theorem
[Modal-Companion]: https://formalizedformallogic.github.io/Book/standard_modal/modal_companion.html

#### Non-Classical Propositional Logic

- [Completeness of Kripke Semantics][NCP-Kripke-Completeness]
- [Rejection Law of Excluded Middle][Int-Reject-LEM]
- [Disjunctive Property][Int-DP]

[NCP-Kripke-Completeness]: https://formalizedformallogic.github.io/Book/superntuitionistic/kripke_completeness.html
[Int-Reject-LEM]: https://formalizedformallogic.github.io/Book/superntuitionistic/reject_lem.html
[Int-DP]: https://formalizedformallogic.github.io/Book/superntuitionistic/dp.html

## Repositories

### [Foundation](https://github.com/FormalizedFormalLogic/Foundation)

Common Results of Mathematical Logic.

**keyword**: _Propositional Logic_, _Classical First-Order Logic_, _Non-Classical Propositional Logic_, _Basic Modal Logic_

### [Arithmetization](https://github.com/FormalizedFormalLogic/Arithmetization)

Arithmetization of Mathematics/Metamathematics.

**keyword**: $\mathsf I \Sigma_0$, $\mathsf I \Sigma_1$, _Peano Arithmetics_

### [Book](https://github.com/FormalizedFormalLogic/Book)

Summaries of results in this entire project.
See [Book].

## Sponsor

This project is supported by [Proxima Technology].

[![Proxima Technology](./proxima_technology.svg)][Proxima Technology]

[Proxima Technology]: https://proxima-ai-tech.com/
