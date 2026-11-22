# Nexa Health

A mobile-first Progressive Web App for a private symptom journal and general wellbeing information.

## Included
- Supabase email/password authentication
- Per-user symptom check-ins stored in \`public.symptom_checkins\`
- Recent history and basic language toggle
- Installable PWA shell with service worker
- Clear medical-safety messaging; no diagnosis, prescriptions, or individualized treatment

## Backend
Supabase project: \`uvtlvbooesvqykzdkrww\`

The frontend uses only the project's publishable key. Never add a Supabase service-role or secret key to browser code.

Expected table columns are checked against the connected project:
- \`profiles(user_id, display_name, preferred_language, created_at, updated_at)\`
- \`symptom_checkins(id, user_id, symptom_label, body_region, severity, duration_label, notes, created_at)\`
- \`saved_guidance(id, user_id, checkin_id, title, guidance_text, source_name, source_url, created_at)\`

RLS must remain enabled and policies must restrict each row to \`auth.uid() = user_id\`.

## Deploy
Enable GitHub Pages for this repository:
1. Repository Settings → Pages.
2. Build and deployment → Deploy from a branch.
3. Branch: \`main\`, folder: \`/ (root)\`, then Save.
4. Add the final Pages URL to Supabase Authentication → URL Configuration → Site URL and Redirect URLs.

The live URL is not active until Pages is enabled and the deployment succeeds.

## Important limitations
This is a web/PWA app, not a native Android APK. The app records symptoms but does not infer causes or diagnose conditions. The service worker caches the app shell only; private journal data is not cached offline.
