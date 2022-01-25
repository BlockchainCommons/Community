Topic: High-level machine-assisted multi-party smart contract negotiation framework
===================================================================================

What is the ideal high-level language for a smart contract?  The
high-level source language used to specify a contract needs to be both
readable to the human beings involved in specifying it, and to machine
tools which verify its correctness or illuminate edge cases.  In the
ideal language a typical smart contract is concisely specified,
correct, and easy to understand with minimal training, with features
reflecting the fact that multiple stakeholders are involved in the
creation of any given smart contract.

This is a much higher level than what is typically thought of as
"script" in bitcoin-like blockchains or what ethereum calls "smart
contracts."  What is being specified can be a state machine for
determining ownership of tokens or collateral, for which state
transitions involve interactive signing rounds and/or confirmation of
a transaction on the network.  Or, perhaps, what is specified is
constraints on the set of allowable state machines, and the actual
state machine is materialized as a compilation step.  This would
reflect the fact that multiple parties are involved and the final
state machine must conjunctively satisfy each of the parties'
necessary conditions, the specification of which is under their own
control.

Regardless of the form of the language, it must be possible to make
and/or verify assertions about the behavior of the resulting smart
contract protocol, and it must be possible to deterministically
compile program actors / daemons which satisfy each role of the
protocol with proofs of correctness.  Ideally this compilation step
should make use of generic protocol runners such that specialized code
need not be written on a per-contract basis.

The output of a compilation step from this high-level source language
is a [portable protocol
specification](smart-contract-specification.md) which provably
satisfies each participant's constraints or requirements.

_Originally from https://github.com/BlockchainCommons/ResearchAgenda/blob/master/topics/smart-contract-negotiation.md by maaku._
