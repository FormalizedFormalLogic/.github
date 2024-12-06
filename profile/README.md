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
- [Cut-Elimination of First-Order Sequent Calculus _(Gentzen's Hauptsatz)_](https://github.com/FormalizedFormalLogic/Foundation/blob/b343bbf25929a9c6877cd72437269fe859556dc6/Logic/FirstOrder/Hauptsatz.lean#L422)
  - _Note that this is an old result, not the latest._
- [Gödel's First Incompleteness Theorem][Goedel-IT1]
- [Gödel's Second Incompleteness Theorem][Goedel-IT2]

[FO-Completeness]: https://formalizedformallogic.github.io/Book/first_order/completeness.html
[Goedel-IT1]: https://formalizedformallogic.github.io/Book/first_order/goedel1.html
[Goedel-IT2]: https://formalizedformallogic.github.io/Book/first_order/goedel2.html

#### Intuitionistic First-Order Logic
- [Gödel-Gentzen translation][Goedel-Gentzen-translation]

[Goedel-Gentzen-translation]: https://formalizedformallogic.github.io/Book/intuitionistic_first_order/goedel-gentzen-translation.html

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

### [Incompleteness](https://github.com/FormalizedFormalLogic/Incompleteness)

Incompleness Theorem Related Results

**keyword**: _Gödel's Incompleteness Theorem_, _Provability Logic_

### [Book](https://github.com/FormalizedFormalLogic/Book)

Summaries of results in this entire project.
See [Book].

## Sponsor

This project is supported by [Proxima Technology].

[<img height="60" src="./proxima_technology.svg">][Proxima Technology]

[Proxima Technology]: https://proxima-ai-tech.com/
