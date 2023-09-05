# Development Phases

The following is an overview of development phases for protocols and products at Blockchain Commons

## Research

Items in the "Research" phase are still being considered and iterated. They represent thought experiments and protocols that we hope to eventually offer to the commons for development. They could include proofs of concept or napkin sketches. They are nowhere near ready for commercial development, only experimentation.

These items primarily exist as Blockchain Commons Research ("BCR") papers in our [Research repo](https://github.com/BlockchainCommons/Research). These papers all feature semantic numbering, and any BCR with a number of less than 1.0 should be considered particularly immature, with the likelihood they will be notably changed. Even BCRs with a full 1.0 release should be considered unsettled into they have been upgraded to a [Wallet Improvement Proposal](https://github.com/BlockchainCommons/wips) ("WIP"). We often will do a full refactor at that point.

Some applications, libraries, data formats, and demos may also be marked as "Research", in which case they should similarly be considered inappropriate for commercial work.

## Release-Path

Once a concept has proven its fundamentals, and we have identified a path for its release (be it an application, a standard, a BIP, or something else) it is placed on the release path. This includes our [WIPs](https://github.com/BlockchainCommons/wips) and most of our repos.

Each WIP or repo should be identified with its level of stability.

***Alpha.*** We are seeking interest and alignment with others, defining additional requirements, and exploring requirements for feature-completeness. There is still no guarantee of backward compatibility. We prefer to have at least two companies interested in implementing a protocol before advancing it from Research to Alpha Release-Path.

***Late Alpha.*** By the time a concept reaches late alpha, we have had some success with the idea, but it is still not feature-complete. By this time, we are trying to limit backward incompatibilities, but they may still occur.

***Community Review.*** Many projects will enter a Community Review stage between Alpha and Beta, when we ask the community for feedback. Obviously, let us know if you find any mistakes or problems. But also let us know if the API/UX meets your needs, if the functionality is easy to use, if the usage of any coding language feels properly standardized, and if the project solves any problems you are encountering when doing this kind of coding. Also let us know how it could be improved and what else you'd need for this to be just right for your usage.

***Beta.*** At this stage, we hope to stabilize the protocols and data formats to maintain compatibility, though there could still be surprises if we discover security issues. We may still be adding features. Security reviews may be in process at this point, or they may not yet have occurred. We prefer to have at least two companies who have implemented an idea before advancing it from Late Alpha to Beta.

***Feature-Complete.*** A product has reached its full feature set and is by now definitely undergoing security reviews if it has not already.

***Final.*** A product's security reviews are complete, and it should be considered entirely ready for usage. In addition, at least two companies must have shipped a product, to have proven any protocols or libraries.

Repos will primarily be identified by these development phases; WIPs will additionally be identified by semantic numbering, with numbers of less than 1.0 being at best alpha.

## Best Practices Standards for Release-Path

We believe in creating and promoting best practices such as the [Core Infrastructure Initiative Best Practices Badge](https://github.com/coreinfrastructure/best-practices-badge). We have begun our own [Best Practices Standards for Blockchain Commons](release-path-standards.md), which we will ultimately use to assess whether each protocol or product meets the criteria for its level of release. We would appreciate your feedback and expansion of this work.
