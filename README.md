# matchStability
A combination of Java and Javascript projects working with data structures and algorithms.
This program tests the proper matching of two inputs. The program matches a matrix of companies to a matrix of candidates that are a proper fit to those companies.
The result is hires, an array of objects matching a company to a candidate.

More about the algorithm:

We assume the following non-standard variant: At any step, any unmatched
company or candidate may propose. Every party always proposes to the next potential partner
on their preference list, starting with the top choice. Proposals are not repeated. Any unmatched
party that receives a proposal accepts unconditionally. If the receiving party is already matched,
but they receive a better offer (higher in their preference list), they accept, and their current
partner becomes unmatched; otherwise, the offer is rejected. The algorithm ends when all
parties are either matched or have made offers to the entire preference list. The algorithm is
underspecified/nondeterministic: it doesn’t state whether a company or a candidate proposes
at a given step, nor which one does, as long as the given rules are observed.
