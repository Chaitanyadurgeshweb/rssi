CHaitu Rad RSSI - Vercel deployment package

CONTENTS
--------
index.html
    Complete website. This is the file Vercel serves.

vercel.json
    Vercel static-site configuration.

supabase/border_limits_setup.sql
    Creates public.border_limits and imports the 132 border records already in the website.

VERCEL DEPLOY
-------------
1. Extract this ZIP.
2. Open Vercel.
3. Create a new project.
4. If Vercel asks for a framework, choose Other / no framework.
5. Set the project root to this folder.
6. Deploy.

SUPABASE DATABASE
-----------------
1. Open Supabase -> SQL Editor.
2. Open supabase/border_limits_setup.sql.
3. Copy all of it into SQL Editor.
4. Click Run.
5. Check the result of:
   select count(*) from public.border_limits;
   It should be 132 for the supplied border list.

IMPORTANT
---------
The website uses the Supabase project URL and the public anon key already present in index.html.
Do NOT put a Supabase service_role key in index.html or Vercel environment variables for this frontend.

The authentication backend (app-auth) is a Supabase Edge Function, not a Vercel serverless function.
It must remain deployed in Supabase at:
https://irkxndefjtsshoyohpam.supabase.co/functions/v1/app-auth

This package does not overwrite that Edge Function because Vercel cannot deploy a Supabase Edge Function as its backend.

AFTER DEPLOY
------------
1. Open the Vercel URL.
2. Login with the existing Master account.
3. Confirm the Manage Users button appears for Master.
4. Test a non-master login.
5. Test border data.
6. Test adding/editing a border only with Master/Vice Master.
