# Uninstall FC

Football tournament and fixture scheduler. Create a tournament, share the 6-character code,
add players with kits, set matches per player, shuffle-draw the fixtures, enter scores,
and the top 2 in the table play the final. Everyone who joins with the code sees updates live.

- `docs/index.html` is the whole web app (one file). It also gets bundled into the APK.
- `app/` is a small Android WebView wrapper (no extra libraries).

## Get the APK
Push this folder to a GitHub repo. The **Build APK** workflow runs on every push to `main`
and attaches `UninstallFC.apk` to a new GitHub Release (also under Actions > run > Artifacts).

Or locally with Android Studio: open the folder, then Build > Build APK(s).

## Host the web app
GitHub: Settings > Pages > Deploy from branch > `main` / `/docs`.
Or drag `docs/index.html` onto Netlify Drop or any static host. It also works opened as a local file.

## How live sync works
Tournaments sync through the free public relay ntfy.sh (topic `uninstallfc_v1_<code>`),
so no account or server is needed. Each device also keeps a copy locally.
ntfy.sh keeps messages about 12 hours; opening the tournament on any device
that has it saved re-uploads it, so a quiet tournament isn't lost.
The relay is public: anyone who knows a code can see or edit that tournament, so keep the host PIN private
and treat it as a casual tool. For a private backend, swap the `Sync` object in index.html for Firebase or Supabase.
