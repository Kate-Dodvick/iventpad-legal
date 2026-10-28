Phase 1: Backend (Supabase) Migration & Hardening
□ Create new Prod Supabase project (iventpad-prod).
□ Run all SQL migrations in Prod (Tables, RPCs, Policies, Storage Buckets).
□ Realtime: Run alter publication supabase_realtime add table messages, chats, chat_participants, profiles, notifications;
□ Realtime: Run alter table messages, chats, chat_participants, profiles, notifications replica identity full;
□ Auth Triggers: Ensure the trigger that creates a public.profiles row on auth.users insert exists.
□ Edge Functions: Deploy push-worker to Prod.
□ Edge Functions: Add SERVICE_ROLE_KEY and PUSH_WORKER_SECRET to Prod Edge Function secrets.
□ Vault & Cron: Add push_worker_url and push_worker_secret to vault.decrypted_secrets. Re-create the 5-minute fallback cron job.
□ Auth URLs: Add iventpad://sign-in and iventpad://reset-password to Auth → URL Configuration → Redirect URLs.
□ Admin Setup: Manually update your production account in the DB: update profiles set is_admin = true where id = '<your-prod-user-id>';
Phase 2: Environment & API Restrictions
□ Maps API: Restrict the Google Maps API key in Google Cloud Console (see Part 2 above).
□ Environment: Update your .env or eas.json production profile to point to the Prod Supabase URL, Anon Key, and Google Maps key.
□ App Config: Ensure app.config.js production variant has com.iventpad.app (no .dev or .preview).
Phase 3: Google Play Console Setup ($25)
□ Pay $25 fee & verify identity.
□ Create app (Default language, Free app).
□ Store Listing: Upload App Icon (512x512), Feature Graphic (1024x500), and 4+ Screenshots.
□ Store Listing: Write Short description (80 chars) and Full description (4000 chars).
□ App Content:
□ Fill Privacy Policy URL (use your GitHub pages link).
□ Fill Data Safety form (Declare Email, Name, Photos, Messages, Location. Mention in-app account deletion).
□ Fill Content Rating (Target: 18+ due to user-generated chat content).
□ Set Target Audience (18+).
□ App Access: Create a test user (e.g., reviewer@iventpad.com). Provide the login credentials and instructions. Populate this account with a few friends, chats, and events so the reviewer sees a working app immediately.
□ Closed Testing: Create a new release, upload your production .aab, and add 15–20 testers' emails to the track.
Phase 4: The 14-Day Closed Test
□ Build Prod AAB: eas build --profile production --platform android
□ Download the AAB and upload it to Play Console (Closed Testing).
□ Send the opt-in URL to your testers.
□ Crucial Test: Send a real push notification while the app is killed. Confirm it lands. Send a message and confirm Realtime ticks work.
□ Monitor Android Vitals (Play Console) daily for crashes/ANRs.
□ Wait 14 continuous days with at least 12 active testers.
Phase 5: Production Launch
□ Apply for Production Access in Play Console (Day 15).
□ Answer the Google questionnaire (explain why you need production access).
□ Wait for Google's review (usually 1–7 days).
□ Once approved, create a Production release.
□ Staged Rollout: 10% → 50% → 100% (over a few days).
