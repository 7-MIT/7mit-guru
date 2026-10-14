# Personal 7 MIT — deployment prerequisites

The Personal menu is embedded in the existing portal page (no new page file). Reading and Self-Reflection are stored in `public.personal_entries` and only displayed after a verified Supabase Auth session.

**Backend activation required before production:** apply the SQL in `personal-schema.sql` through the authorized database administrator; provision teacher/student mapping through a trusted server-side process; create a secure `personal_student_roster` view/RPC returning only teacher-authorized students, not all users. Confirm that `window.SUPABASE_ANON_KEY` and proper Supabase Auth sessions are available in all portals, since legacy akun.7mit sessions may not be Supabase Auth sessions. Never use a service-role key in browser JavaScript. Test student isolation, unauthorized access, teacher read access, and consent/notice for personal and religious reflections.

Teacher role in the UI is not a security control: database policies MUST enforce permissions independently. Deployment is deliberately fail-closed until verified backend auth and permissions are ready.
