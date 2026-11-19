# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: HMS_04.3.spec.js >> DOCTOR AUTHENTICATED SCRIPTS >> HMS_TS_14 - Verify that medical history can be added for a patient
- Location: tests\HMS_04.3.spec.js:404:9

# Error details

```
Error: locator.click: Target page, context or browser has been closed
Call log:
  - waiting for getByRole('row').filter({ hasText: 'Ethyl Schroeder' }).first().getByRole('link', { name: /View|/ })

```

```
Error: apiRequestContext._wrapApiCall: Target page, context or browser has been closed
```