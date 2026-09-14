# Fernweh Supply Co. — demo store

A working online store with a product catalog, size/quantity selection,
a cart, and a checkout that collects shipping info — no payment
processing. Orders are saved to Firebase and show up in a separate
admin page you can log into, with a one-click CSV download.

## What's in this folder

| File | What it's for |
|---|---|
| `index.html` | The whole storefront customers see — self-contained |
| `admin.html` | Your private dashboard: orders, products, and checkout fields — self-contained |
| `firestore.rules.txt` | Firestore security rules to paste into the Firebase console |
| `storage.rules.txt` | Storage security rules, for uploading product photos from admin |

Both `index.html` and `admin.html` are single files with everything
built in. You'll only ever need to open them in a plain text editor
(Notepad, TextEdit, or GitHub's own editor) to make the two small edits
described below — everything else is done for you.

## Setup (about 10 minutes, no coding)

1. **Open `index.html`** in a text editor and find the section near
   the top labeled `FIREBASE CONFIG` (search for that phrase). Follow
   the numbered steps written there: create a free Firebase project,
   register a web app, turn on Firestore, paste in the security rules
   from `firestore.rules.txt`, turn on Email/Password sign-in, create
   yourself an admin login, and (optionally) turn on Storage if you
   want to upload product photos instead of pasting image URLs.
2. Firebase will hand you a block of keys. Paste them into the
   `firebaseConfig` object in `index.html`, replacing the `PASTE_...`
   placeholders.
3. **Do the exact same paste into `admin.html`** — find the same
   `FIREBASE CONFIG` section there and paste in the identical keys.
   Both files need to match.
4. That's it — both pages will now save and read real data. Open
   `admin.html`, log in, and go to the **Products** tab to add your
   items (there's a one-click "Add 6 starter products" button if you
   want to try the store with sample items first).

## Publishing it on GitHub Pages

1. Create a new GitHub repository and upload `index.html`,
   `admin.html`, `firestore.rules.txt`, and `storage.rules.txt` to it
   (drag-and-drop on github.com works fine, or use GitHub Desktop).
2. In the repo, go to **Settings > Pages**.
3. Under "Build and deployment", set **Source** to "Deploy from a
   branch", branch `main`, folder `/ (root)`. Save.
4. GitHub will give you a URL like
   `https://yourusername.github.io/your-repo-name/` — that's your
   live store. Add `admin.html` to the end of that URL for your
   dashboard (e.g. `.../your-repo-name/admin.html`). Don't link to it
   from the storefront; just bookmark it for yourself.

## Managing your products

Products are no longer edited in the code — everything happens in
**admin.html**, on the **Products** tab:

- **Add a product** with the "Add product" button: name, price, tag,
  sizes (comma-separated, e.g. `S, M, L, XL`), description, and a
  photo.
- **Change a photo** by opening a product, then either pasting an
  image URL or using the file picker to upload a photo directly (this
  needs the optional Storage setup step above).
- **Edit or delete** any product from its card.
- **Reorder** products with the up/down arrows — that's the order
  they appear in on the storefront.

Changes show up on the storefront within a second or two, no
redeploying needed.

## Changing what you collect at checkout

On the **Checkout fields** tab in `admin.html`, you can:

- Turn any of the standard fields (first/last name, email, phone,
  address, notes) on or off, mark them required or optional, or
  relabel them.
- Add your own custom fields — short text, long text, a dropdown with
  your own options, or a yes/no checkbox (a gift message, a delivery
  date, a T-shirt size, anything).

Click "Save changes" and the storefront's checkout form updates to
match. Orders show any custom answers in the order detail and in the
CSV export.

## Renaming the store

The name "Fernweh Supply Co." appears a few times in both
`index.html` and `admin.html`. Search each file for "Fernweh" and
replace it with your store's name.

## A few honest limitations

- **This is a demo, not a production payment system.** There's no
  payment processor — checkout collects shipping details and saves
  the order, that's all. If you need to actually charge cards, you'd
  need to add a payment processor like Stripe, which is a bigger step.
- **The admin login is basic.** It's a real login (Firebase
  Authentication), but there's no "forgot password" flow built in —
  if you forget your password, reset it from the Firebase console
  under Authentication > Users.
- **The cart is per-browser.** If a customer closes their browser
  mid-shopping and comes back on a different device, their cart won't
  follow them (this is normal for most simple stores too).
- **Firebase's free tier** comfortably covers a small store (tens of
  thousands of reads/writes a month at no cost). If you ever outgrow
  it, Firebase will prompt you to upgrade — it won't quietly charge you.
- **Uploading photos needs the optional Storage step above.** If you
  skip it, you can still add product photos by pasting any image URL
  — the upload button will just tell you Storage isn't set up yet.
