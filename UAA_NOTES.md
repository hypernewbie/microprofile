# Astral Engine - MicroProfile Customisation

This directory contains a fork of MicroProfile tailored for the Astral Engine's Monokai aesthetic.

## UI Overhaul Notes
- **Font:** Switched to a robust monospace stack: `'Cascadia Code', 'Consolas', 'Menlo', 'Monaco', 'Lucida Console', monospace`.
- **Palette:** Monokai Pro (#272822 BG, #f8f8f2 FG).
- **Legibility:** 
    - Default `FontHeight` is set to `12`.
    - `MenuFontHeight` is set to `18` for top-level menus and dropdowns.
- **Detailed View:** Removed linear gradients from thread blocks for a flatter, cleaner look.

## Regeneration Instructions
If you modify `src/microprofile.html` or `src/microprofilelive.html`, you **must** regenerate `microprofile_html.h`. 

The `embed` tool (compiled from `src/embed.c`) uses an append mode, so always delete the existing header first.

### Windows (PowerShell)
```powershell
# From vdeps/microprofile directory
Remove-Item microprofile_html.h
cd src

# Regenerate Standard UI
.\microprofile-win32-embed.exe ..\microprofile_html.h microprofile.html ____embed____ g_MicroProfileHtml MICROPROFILE_EMBED_HTML

# Regenerate Live UI
.\microprofile-win32-embed.exe ..\microprofile_html.h microprofilelive.html ____embed____ g_MicroProfileHtmlLive MICROPROFILE_EMBED_HTML
```

### Linux/MacOS
```bash
# From vdeps/microprofile directory
rm microprofile_html.h
cd src
gcc embed.c -o embed

# Regenerate Standard UI
./embed ../microprofile_html.h microprofile.html ____embed____ g_MicroProfileHtml MICROPROFILE_EMBED_HTML

# Regenerate Live UI
./embed ../microprofile_html.h microprofilelive.html ____embed____ g_MicroProfileHtmlLive MICROPROFILE_EMBED_HTML
```
