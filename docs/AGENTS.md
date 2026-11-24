# Use ViceGoblin Studio with AI agents

From version 1.3.0, an AI agent on your PC (Claude Code, Claude Desktop or any other tool that speaks MCP) can use ViceGoblin Studio for you: make clips from a video, read what it found, edit the clips, and save the ones you approve. Everything runs on your PC. **An agent can never publish, delete projects, read your keys or change your settings. Only you publish.**

## Connect an agent (2 minutes)

1. Install and open ViceGoblin Studio once. (After that an agent can start it without a window.)
2. Open **Settings, then Use with AI agents**. It shows the exact lines for your PC, each with a Copy button.
3. **Claude Code:** run the `claude mcp add vicegoblin ...` line once in a terminal.
   **Claude Desktop:** paste the JSON into `claude_desktop_config.json` and restart Claude Desktop.
   **Anything else:** use the command-line tool shown there.
4. Ask your agent, for example:

   > Use ViceGoblin to make 5 clips of about 30 seconds from `C:\Videos\stream.mp4`. Look at why each was picked, reject any that start in the middle of a thought, approve the best two, and save the approved ones to `C:\Users\me\Videos\clips`.

5. Open ViceGoblin Studio to check the clips and publish the ones you want yourself.

## What the agent can do (10 tools)

| Tool | What it does |
|---|---|
| `vicegoblin_status` | Checks the app is running (starts it without a window if not) and ready |
| `vicegoblin_list_projects` | Lists projects, newest first |
| `vicegoblin_get_project` | Every clip with title, hook, times, score, **why it was picked**, review state, layout, captions and the file path |
| `vicegoblin_make_clips` | Makes clips from a video file on this PC (read where it is, never changed or moved) or from a link you own. Returns progress if it takes long: call `get_project` again |
| `vicegoblin_edit_clip` | Trim, title, hook, description, layout, caption style, size and position; re-renders the clip |
| `vicegoblin_fix_captions` | Replace the caption words of a clip and re-render |
| `vicegoblin_review_clip` | Mark a clip approved, rejected or pending, with a short note |
| `vicegoblin_ask_editor` | Edit a clip from a plain-English request, using the AI engine you set up in the app |
| `vicegoblin_export_clips` | Save download packs (video, cover, title, description, captions) of chosen or approved clips into a folder; never overwrites a file |
| `vicegoblin_diagnose_project` | Explains why a project failed, in plain words |

## What the agent cannot do

There are no tools for these, so no prompt can make them happen: publish to YouTube, delete projects or files, read or change your keys, sign-ins or settings, or quit the app. Saving packs only writes new zip files into a folder you name, and refuses folders that belong to Windows or installed programs.

## Privacy

The connection never leaves your PC: the agent program talks to the app over `127.0.0.1`. It signs in the same way a second launch of the app does (the access key file only your Windows user can read, a one-time ticket, a session cookie). Your videos are not sent anywhere by ViceGoblin. The company behind your agent sees what the agent reads and writes in your conversation (project names, clip titles, file paths), as it would for any tool you connect.

## Command line

The same abilities, for scripts and for agents that can run commands (run `... vgctl.py --help` for all options):

```
vgctl.py status
vgctl.py clip "C:\Videos\stream.mp4" --count 5 --length 30
vgctl.py show <project>
vgctl.py review <project> 1 approved --note "strong hook"
vgctl.py export <project> --clips approved --to "C:\Users\me\Videos\clips"
```

Output is JSON; the exit code is 0 when it worked and 1 with a plain sentence on stderr when it did not.

## In the app: why a clip was picked, review, and Ask the editor

- Every clip says **why it was picked** in one or two honest sentences (you pressed F8 there, chat got busy, one of the loudest parts, it opens with a question, the AI chose it). If nothing stood out it says so rather than inventing a reason.
- Every clip has **Approve** and **Reject** buttons. Agents and people use the same marks.
- In the editor, **Ask the editor** takes a plain-English request ("make the captions bigger and start two seconds later") and applies only allowed edits to that one clip. It needs a Gemini key (free) or Claude Code set up in Settings, and says so if it is missing. What the AI replies is read as data: anything outside the allowed edits is ignored.

## Troubleshooting

- *"Could not read the app's access token file"*: open ViceGoblin Studio once, as the same Windows user that runs the agent.
- *The agent says the app did not start*: open it from the Start menu once, then try again.
- *A long video is still running*: that is normal; `vicegoblin_get_project` shows progress. A one-hour video can take about half an hour on a laptop.
