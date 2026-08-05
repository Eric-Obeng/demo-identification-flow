# Identification Flow Demo

Standalone demo of the identification/authentication redirect flow, isolated from the onboarding app's domain so callback behavior can be tested cleanly.

## Run

```
node server.js
```

Then open http://localhost:3000

## Flow

1. `index.html` shows a button. Clicking it does a full-page redirect to the external auth system, with a `callback` query param pointing back to `/identification-redirect/<assignment_id>` on this app's domain.
2. The auth system is expected to redirect back to that callback URL. `identification-redirect.html` reads the assignment_id from the path and displays any query params the auth system appended.

## Demo-only values (must change before production)

In `index.html`:
- `AUTH_SYSTEM_URL` — placeholder external auth system URL, needs the real one.
- `DEMO_ASSIGNMENT_ID` — hardcoded assignment_id, appended to the callback URL manually for this demo. Once the external team confirms whether the assignment_id can flow through the auth system directly (or a submission URL can be provided instead), this manual append should be removed.

## Moving to staging

Swap `CALLBACK_BASE_URL` in `index.html` from the test domain to the staging domain — no other code changes needed.
