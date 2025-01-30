- Use conventional commits.
- In addition to the types provided by the conventional commits specification, you can also use the following types:
  - `helm` - for changes to helm charts.
  - `deps` - for changes to dependencies.
- If the repo is a monorepo, add the package name to the scope of the commit message.
- Prioritize uncommeneted code over comments.
  For example for the following lines getting deleted:
  ```yaml
  # this is a built-in strategy in release-please, see "Action Inputs"
  # for more options
  release-type: node
  ```
  the commit message should be:
  ```
  ci: removed release-type from release-please.yaml workflow
  ```
