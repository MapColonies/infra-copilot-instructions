## Code Style and Quality

- Prefer using builtin functions from node and javascript over external libraries.
- Use `as const` instead of `enum` in typescript.
- Prefer using `const` over `let` when defining variables.
- Avoid deep nesting in code. Prefer using early returns.
- Use meaningful variable and function names.
- Keep functions short (under 20 lines) and focused on a single responsibility. It should not be a hard limit, but a guideline to keep code readable and maintainable.
- Do not use magic numbers. Use constants or variables with clear names. 0 and 1 are allowed as they are commonly used. There is an ESLint rule `@typescript-eslint/no-magic-numbers` that is enabled, and you can check its configuration.
- Prefer interfaces over classes in typescript.
- Ensure file ends with a newline.
- Format code consistently according to established style guides. We use Prettier for formatting, and it has a configuration file in the root of the repository.
- The npm organization for `MapColonies` is called `map-colonies`.
- For complex if conditions (Complex logic involving maths, multiple variables, nested conditions, etc.), create a variable with clear name and use it in the if.

## Documentation and Comments

- Add comments to explain complex logic, assumptions, or non-obvious code sections.
- Use standard documentation formats (JSDoc, TypeDoc) for functions, classes, and modules.

## Code Modification Principles

- Honor the existing system and understand its place in the larger architecture.
- Make the smallest change that fulfills the requirement.
- Preserve working systems and existing patterns.
- Apply surgical precision rather than comprehensive restructuring. Changes should be minimal and focused on the specific request.
- Follow existing patterns and conventions within the project.
- Use the same libraries and frameworks already employed unless there's a strong reason to introduce new ones (Industry best practices, performance improvements, tested solutions, reduce complexity, security reasons). Make sure there are no multiple libraries doing the same thing.
- When in doubt, ask for scope clarification rather than assuming the broadest interpretation.
- If you identify potential improvements beyond the scope of the request, mention them to the user without implementing them.
- Be prepared to revert changes if they don't yield the desired outcome.

## Error Handling and Security

- Implement robust error handling for potential failure points (network requests, file I/O, invalid input). Check the existing code for patterns and follow them.
- Use appropriate error handling mechanisms (try-catch blocks, error codes, specific exception types, using `Result` type to encapsulate success and failure cases).
- Provide informative error messages.
- Sanitize user inputs to prevent injection attacks (SQL, XSS, etc.).
- Avoid hardcoding sensitive information like API keys or passwords. Use environment variables or configuration management tools.
- Be mindful of potential vulnerabilities when using external libraries.

## Testing and Maintainability

- Design functions and modules with testability in mind (dependency injection).
- Write testable code that can be easily verified.

## Logging

- Use the existing logging infrastructure in the project. Do not introduce new logging libraries without justification.
- Use structured logging with consistent field names and formats (JSON format preferred).
- Follow OpenTelemetry semantic conventions for field names where applicable.
- Employ appropriate log levels: `trace`, `debug`, `info`, `warn`, `error`, `fatal`.
- Do not over-log. Avoid redundant logging when middleware already handles it:
  - Skip logging in controllers if HTTP request/response middleware logs requests
  - Skip logging in error handlers if upstream middleware logs errors
  - Skip logging successful operations that are already tracked by instrumentation
- Log at appropriate levels:
  - `error`: Application errors, exceptions, failed operations
  - `warn`: Recoverable errors, deprecated usage, configuration issues
  - `info`: Significant application events, service start/stop, major state changes
  - `debug`: Detailed diagnostic information for troubleshooting
  - `trace`: Fine-grained execution details, typically disabled in production
- Include relevant context in log messages:
  - Request IDs, user IDs, correlation IDs
  - Operation parameters and results (excluding sensitive data)
  - Error details including stack traces for errors
- Use consistent log message formats:
  - Start with a clear action or event description
  - Include relevant context as structured fields
  - Avoid logging sensitive information (passwords, tokens, personal data)
- Log business-critical events and state changes that help with debugging and monitoring.
- Consider log volume and performance impact in high-throughput scenarios.
