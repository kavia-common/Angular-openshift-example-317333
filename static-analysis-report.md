# Static Analysis Report (Angular-openshift-example-317333)

This report captures a static-analysis pass (type-check, Angular build checks, and linting) using the project's configured tooling and minimal direct invocations.

## Environment

- Node: `v18.20.8`
- npm: `10.8.2`

## Commands executed

From `Angular-openshift-example-317333/`:

1. Install dependencies
   - `npm ci`

2. TypeScript type-check (no emit)
   - `npx tsc -p tsconfig.app.json --noEmit`

3. Angular build checks (AOT dev build)
   - `npm run build -- --configuration development --aot --build-optimizer=false`

4. Lint attempts (as-configured / conventional)
   - `npm run lint`
   - `npx ng lint`
   - `npx eslint "src/**/*.ts" "src/**/*.html"`

## Results

### TypeScript type-check (tsc)
- ✅ PASS: `npx tsc -p tsconfig.app.json --noEmit`
- No TypeScript errors were reported.

### Angular build (AOT, development configuration)
- ✅ PASS: `npm run build -- --configuration development --aot --build-optimizer=false`
- No Angular template/type errors were reported.

### Linting
Linting could not be executed because the project does not have lint tooling configured.

- ❌ `npm run lint`
  - Error: `Missing script: "lint"`
  - Meaning: `package.json` has no `lint` script.

- ❌ `npx ng lint`
  - Error: `Cannot find "lint" target for the specified project.`
  - Meaning: `angular.json` does not define an `architect.lint` target.

- ❌ `npx eslint ...`
  - Error: `ESLint couldn't find a configuration file.`
  - Meaning: there is no `.eslintrc.*` or `eslint.config.*` present in the repository.

Because lint did not run, there are no file/line-number lint findings to report at this time.

## Additional install-time findings (informational)

During `npm ci`, npm reported vulnerabilities:
- `65 vulnerabilities (10 low, 13 moderate, 40 high, 2 critical)`

(These are not lint/type-check findings, but surfaced during dependency installation.)

## Recommended next step (if lint is required)

To enable linting with minimal impact:
- Add an ESLint configuration (`.eslintrc.json` for ESLint v8, or `eslint.config.js` for ESLint v9).
- Add a `lint` script in `package.json` and/or an `architect.lint` target in `angular.json` (e.g., via `@angular-eslint`).

No code changes were made to application logic as part of this static analysis run.
