# Principles of Security

## Least Privilege
- A subject should only be given necessary privileges
- Violation example: always running as root
- Good implementation example: each app on Android runs as its own user, with limited permissions

## Separation of Privilege
- Different people with different privileges must work together to achieve a goal
- Ex. two people required to arm and fire a nuclear missile
- Compartamentalization: split programs into trusted and less-trusted parts

## Fail-safe Defaults
- Permission rather than exclusion
- Everything is disallowed, unless explicitly allowed
- Ex. Microsoft Office disables macros by default

## Economy of Mechanism
- Keep code and mechanisms simple; use the simplest solution that works
- Use known secure solutions, e.g. open-source libraries

## Complete Mediation
- Every access must be checked every time a resource is used

## Open Design
- Avoid security only through obscurity
- Kerchoff's principle: a system should be secure even if the entire mechanism is known

## Defense in Depth
- There should be multiple layers of defenses
- Protection, detection, and recovery
- Strike a balance between increasing defense and reducing complexity

## Least Common Mechanism
- Mechanisms to access resources shouldn't be shared
- Reduce side channels, like timing, CPU usage, etc.
    - Example of a side channel: website being able to tell if you've visited a site by rendering and querying the color of an <a\> tag

## Psychological Acceptability
- Security mechanisms should not add to the difficulty of accessing a resource
- Principle of least astonishment: designs should match user's experience and expectations, i.e. follow UI conventions
