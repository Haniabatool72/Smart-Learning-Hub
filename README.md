# Smart Learning Hub
Vanilla HTML/CSS/JS + Supabase. No build step.

## Setup
1. Create a Supabase project. In **SQL Editor**, run `supabase/schema.sql` (tables, row-level security, sample Science/Maths/English content).
2. Put your project URL and anon key in `js/config.js`.
3. In Supabase **Auth → URL Configuration**, add your site URL. (Optionally disable email confirmation while testing.)
4. Serve the folder: `npx serve .` or deploy to Netlify / Vercel / GitHub Pages.

## Make a teacher
Sign up normally, then run in the SQL editor:
`update profiles set role='teacher' where id=(select id from auth.users where email='you@school.com');`
Teacher writes are enforced by RLS on the database, not just by hiding buttons.

## AI assistant (optional, off by default)
`supabase functions deploy ask-ai` then `supabase secrets set ANTHROPIC_API_KEY=your_key`, then set `AI_ENABLED: true` in `js/config.js`. Until then the assistant page says it is not connected.

## Notes
- Lessons support image and video URLs; sample lessons ship without them so no unverified links are included. Teachers can add them.
- Local storage is used only for display preferences (large text, friendly font, high contrast).
