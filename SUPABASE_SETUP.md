# QUVIKO Supabase Integration — Setup and Test Guide

This branch contains the first frontend connection to the QUVIKO Supabase project. It is intentionally separate from `main`; GitHub Pages remains on the current stable prototype until the authentication settings and tests are complete.

## Connected features

- Email/password sign-up and sign-in through Supabase Auth.
- Email-confirmation-aware registration flow.
- Password reset and password update flow.
- Profile creation and editing in `public.profiles`.
- Shared published posts in `public.posts`.
- Shared responses in `public.comments`.
- Per-member appreciation records in `public.likes`.
- Member directory based on saved profiles.

The page uses the public Supabase publishable key. Never add a Supabase `service_role` key, `sb_secret_...` key, database password, or personal access token to frontend code or GitHub.

## Required dashboard configuration before production

In Supabase Dashboard → Authentication:

1. **URL Configuration**
   - Set Site URL to `https://javis143.github.io/quviko/`.
   - Add that exact URL to Redirect URLs.
   - Do not use broad wildcard redirects. Add a localhost URL only if local development is actually used.
2. **Email provider**
   - Keep email sign-up enabled.
   - Keep email confirmation enabled. Hosted Supabase projects enable this by default, but verify it.
3. **Password security**
   - Set the server-side minimum password length to 12 characters.
   - Require lowercase, uppercase, a number, and a symbol if the project settings expose those controls.
   - The frontend also checks for 12 characters, but frontend checks alone are not a security boundary.
4. **Attack protection**
   - Keep CAPTCHA disabled until a CAPTCHA provider/widget is integrated into this page. Enabling it before integration will block sign-up/sign-in requests.
   - Review Auth rate limits. Supabase's built-in email sender is limited, so avoid repeated test sign-ups.

## Test plan before merging to `main`

1. Register with a real email address and confirm the email.
2. Sign in, edit the profile, refresh the page, and confirm the profile persists.
3. Publish a post and confirm it appears after refresh.
4. Create a second test account in a separate browser/private session. Confirm it can read the published post and respond.
5. Confirm account B cannot edit account A's profile or delete account A's post. Confirm account A cannot see account B's private like records.
6. Test password reset, choose a new password, and sign in with the new password.
7. Sign out and confirm the account-specific community controls are no longer available.

## Current MVP boundaries

- The `saved` list is stored locally per browser and account; it is not synchronized between devices.
- Like records are private per member. The UI intentionally does not expose a global like count or liker list.
- Project cards and opportunity cards are still illustrative placeholders; they are not yet database-backed.
- Realtime updates, file uploads, direct messaging, project workspaces, and opportunity applications are not implemented in this phase.
- All four database tables retain Row Level Security. Do not grant anonymous access just to make the public homepage show member data.
