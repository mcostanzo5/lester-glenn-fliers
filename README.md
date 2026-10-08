# Lester Glenn Flier Studio

Makes review fliers, sales desk signs, contact cards, and business cards for every Lester Glenn store. It runs entirely in the browser: no server, no sign-in, and nothing anyone types is saved anywhere.

- `index.html`: the public tool everyone uses
- `admin.html`: store settings, which only save with your GitHub key
- `stores.json`: every store's details (names, phones, colors, review links)
- `logos/`, `fonts/`: store logos and brand fonts
- `vendor/`: the QR code and PDF libraries plus the standard font, so the site has no outside dependencies

## 1. Put it on GitHub (one time)

1. Sign in at github.com and click **New repository**.
2. Name it something like `lester-glenn-fliers`. Choose **Public**. (Free GitHub accounts can only publish public repositories. On a paid GitHub plan you can choose Private, but the website itself is public either way.)
3. On the new repository's page, click **uploading an existing file**, drag in **everything inside this folder** (including the `logos`, `fonts`, and `vendor` folders), and click **Commit changes**.
   The `.nojekyll` file is hidden on some computers. If it doesn't upload, that's fine.

## 2. Turn on the website (one time)

1. In the repository, go to **Settings > Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**, the branch to **main**, the folder to **/(root)**, and click **Save**.
3. After a minute or two the page shows your link, like `https://your-account.github.io/lester-glenn-fliers/`. That's the address to share.

### Optional: your own address, like fliers.lesterglenn.com

1. In **Settings > Pages > Custom domain**, type `fliers.lesterglenn.com` and save.
2. Wherever lesterglenn.com's DNS is managed, add a **CNAME** record: name `fliers`, value `your-account.github.io`.
3. Once GitHub shows the domain as verified, check **Enforce HTTPS**.

## 3. Create your settings key (one time)

The settings page saves straight into this repository, so it needs a key that only you have.

1. On GitHub, open your profile picture menu > **Settings > Developer settings > Personal access tokens > Fine-grained tokens > Generate new token**.
2. Name it `Flier Studio settings`. Pick an expiration (one year is reasonable; GitHub emails you before it expires).
3. Under **Repository access**, choose **Only select repositories** and pick `lester-glenn-fliers`.
4. Under **Permissions > Repository permissions**, set **Contents** to **Read and write**. Leave everything else alone.
5. Click **Generate token** and copy it (it starts with `github_pat_`). GitHub only shows it once.

Treat the key like a password. Anyone holding it can change the store settings.

## 4. Change store settings

1. Go to your site address with `/admin.html` on the end, for example `https://fliers.lesterglenn.com/admin.html`. It isn't linked from the public tool.
2. Enter the repository (`your-account/lester-glenn-fliers`), leave the branch as `main`, paste your key, and click **Connect**. Check **Remember on this computer** only on your own computer.
3. Pick a store, make changes, and click **Save store**. The public tool picks up the change in about a minute.

Without the key, anyone who finds the settings page can look but cannot save anything.

## Notes

- **Search engines:** the site asks search engines not to list it, but anyone with the link can open it.
- **Brand fonts:** the files in `fonts/` are publicly downloadable from this site and repository. The Chevy Sans license restricts that, and the other brands' fonts have their own terms. To switch any store back to the standard font, open it in the settings page, click **Use standard font**, and save. You can also delete that store's files from `fonts/`.
- **Updating the tool itself:** replace `index.html` in the repository with a new version. Your store settings live in `stores.json` and aren't affected.
