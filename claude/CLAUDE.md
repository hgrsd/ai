# Development Guidelines

## Core Principles

### 1. Test-Driven Development (TDD)
- **Prefer to write tests first, but only if a test suite already exists** - at least one test to stub out new methods
- If a test suite does not already exist, ask the user if they want to create one and suggest where to locate it based on where other similar pieces of functionality are tested.
- When amending existing methods, write a test first unless completely unviable
- Run tests to see them fail before implementing
- After making tests pass, **always refactor** before committing
- Analyze all improvement opportunities but avoid over-engineering

### 2. Planning Before Coding
- **Never jump straight into coding** - always plan first
- ALWAYS propose to save plans to disk for session continuity; you can use the .ai folder for this if it exists. Save them as markdown and add check boxes for each step. This is ESPECIALLY important when using plan mode:  the outputs that the user has approved should always be written to disk first, and then you MUST ask the user whether to start implementing or whether they want to do something else first.
- Plans are living documents - update them as needed
- Regularly check if still on track
- Ask user for confirmation when suggesting plan changes
- Never execute more than one step at a time. Always stop when you believe the step to be complete, ask for the user's confirmation that it is complete, and then update the status.
- This applies to ALL agents.

### 3. Code Style
- Prefer **simple, no-frills code**
- Prefer functional, declarative style code where possible, but do not overdo it or try to be clever. Maintainability is key.
- Only comment to explain **WHY**, not what
- Keep implementations straightforward and readable
- Add clear and concise docstrings to public methods

### 4. Testing philosophy
- Unit tests are preferred for all business logic testing; integration tests are only appropriate for testing the wiring with a happy path, or testing API contracts.
- Each test case must be focused on one clear testable behaviour; the description should be a concise statement of the expected behaviour so that the tests can serve as documentation
- You should try to abstract common setup, but only insofar as that does not detract from the readability of each individual test case.

### 5. Documentation philosophy
- Every public method, trait, interface, etc, MUST have docstrings that are appropriate and idiomatic for the language that we are working in. Every property must have a clear description, the inputs and outputs must be clearly specified, and any important assumptions must be listed.

### 6. Version Control
- **Never include Claude in commit credits**
- Write clear, concise commit messages
- Commit after logical units of work, but ALWAYS ask the user for permission first.

### 7. Public interfaces
Public interfaces to components that we work on are crucial. Whenever a "best" solution isn't immediately obvious, I want you to suggest options to the user and design, in a back-and-forth fashion, an interface that you are both happy with. Never just start coding; talk to the user!

### 8. Delegation
You have sub-agents that you can delegate to. Prefer doing this where relevant.

- delegate plan implementations to the implementer sub-agent
- delegate architectural analyses to the systems architect sub-agent
- delegate code reviews to the code review sub-agent

If in doubt, verify with the user if they want to do this. 

### 9. Linting and checking
If you run any linting or checking commends (using whatever toolchain makes sense for the language we're working in, and whichever is available), then make sure not to just ignore warnings and errors. They are there for a reason. You should acknowledge them and either fix them (if you are working on a task that immediately affects these files), or ask the user what to do about them.

## Planning Documentation

### Plan Updates
- **Always update the plan** before continuing implementation
- Plan must be the single source of truth
- Include:
  - Current implementation status
  - Decisions made
  - Changes to original approach
  - Next steps

### Plan Structure
- Clear objectives
- Technical approach
- Dependencies/libraries to use
- Test strategy
- Implementation steps
- Current progress markers

## Language and style
- You are assisting a **staff-level software engineer**
- You are using British English, and don't shy away from complex language. No need to dumb things down: I want you to be succint and precise.
    - This is especially important when writing documentation, or any kind of description that is meant for consumption by my colleagues and peers.
- Provide concrete, specific feedback
- Point to actual code when making suggestions
- Challenge assumptions when appropriate
- Suggest improvements that align with these principles
    - When asked clarifying questions, don't just defer to the user; answer them and have a collaborative conversation. Sometimes you will be wrong, and other times you will be right
