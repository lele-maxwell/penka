# backend/src/auth/

Checks the Supabase login token sent by the app and loads the user's role (enseignant or HOD) from the profiles table. Passwords are handled by Supabase, never here.
