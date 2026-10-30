# Revision Desk for Word

This is a personal Word add-in. It turns peer-review comments into colour-coded tasks and adds each one as a Word comment on the passage it refers to.

| Square | Task type |
|---|---|
| 🟦 | Journal & admin |
| 🟧 | Figures & tables |
| 🟥 | Methods & data |
| 🟩 | Results & discussion |
| 🟨 | Clarity & language |
| 🟪 | References |

## What it does

- Adds one Word comment per task, on the exact words it's about. Each comment starts with its coloured square and ID, for example `🟥 R2.3 · Why sample at ~1 cm?`.
- Opens a side panel with the colour-coded task tiles, Focus mode and the response letter. Clicking a tile jumps to its comment in the document.
- **Mark done** resolves the Word comment and adds your "What I changed" note as a reply. If you resolve a comment in Word, the panel ticks the task off too.
- Turns on Track Changes, so you get the marked-up copy that journals ask for.
- **Remove task comments** clears all task comments before you submit. Your own comments stay.
- **Start round 2** keeps your round-1 responses, so Claude can link comments that come back.

There are two ways to create the tasks:

1. **From Revision Desk in Claude.** This uses your Claude plan, so you don't need a key. In Revision Desk, open the revision, add the manuscript and click **Copy for Word**. Then paste it into the add-in.
2. **Inside Word, with your own Anthropic API key.** Drop or paste the reviews and Claude reads the open document directly. You can create a key at console.anthropic.com. It's billed separately from your Claude plan.

## Install (Mac, one time)

The panel is a web page that Word loads from `https://antonkout.github.io/revision-desk/`. The `manifest.xml` file tells Word where to find it.

1. **Host the files.** These files need to be in the public GitHub repo `antonkout/revision-desk`, with GitHub Pages turned on (Settings › Pages › Deploy from a branch › `main` / root). Then check that https://antonkout.github.io/revision-desk/ opens.
2. **Give Word the manifest.** Quit Word. Then open Finder, press ⌘⇧G and go to
   `~/Library/Containers/com.microsoft.Word/Data/Documents/`
   Create a folder called `wef` if it isn't there, and copy `manifest.xml` into it.
3. **Open the add-in.** Start Word and open your manuscript. On the **Home** tab, click **Add-ins** and find **Revision Desk** under *Developer Add-ins*. After the first time, a **Revision Desk** button appears on the Home tab.

## Privacy

- The GitHub site only holds the app's code. Your manuscript, the reviews and your notes stay in Word on your Mac.
- If you build tasks inside Word, the text goes from your Mac straight to Anthropic's API.
- Your API key is stored only inside the add-in on this Mac.
- The task list is kept in the add-in's local storage. If that storage is ever cleared, the add-in rebuilds the list from the task comments in the document.

## Update or remove

- **To update:** replace the files in the GitHub repo. Word picks up the new version the next time the panel opens. To force it, quit Word and empty `~/Library/Containers/com.microsoft.Word/Data/Library/Caches/`.
- **To remove:** delete `manifest.xml` from the `wef` folder.
