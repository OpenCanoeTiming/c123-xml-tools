# Participant Adder CZ

Adds late-registered competitors directly into a Canoe123 XML file during a race event.

## What it does

When a competitor needs to be added after the startlist has been published, this tool:

1. Opens the C123 XML file directly on disk (via File System Access API)
2. Searches the Czech canoe registry (CSV) by name, surname, or RGC code
3. Auto-fills competitor data (name, club, ranking, birth year, category)
4. Adds the competitor to both **Participants** and **Results** (startlist) sections
5. Saves the modified XML back to the same file

**Important:** Canoe123 must be stopped before editing the XML. Restart it after saving to re-read the file.

## Usage

1. Open `participant-adder-cz.html` in Chrome or Edge
2. Click **Open XML file** to select the C123 XML file
3. Optionally load a Czech canoe registry CSV (cached in browser for future use)
4. Search for the competitor, select their class, assign a bib number
5. Select which races to add them to
6. Click **ADD Competitor**
7. Click **Save** to write changes to disk

## Registry CSV Format

The tool expects a CSV export from the Czech Canoe Federation registry:
- **Encoding:** Windows-1250
- **Separator:** Semicolon (`;`)
- **Required columns:** `RGC`, `Prijmeni`, `Jmeno`, `Datum Narozeni`, `Pohlavi`, `Oddil`, `Odd_nazev`
- **Optional columns:** `VK`, `KS`, `C1S`, `C2S`, `KW`, `C1W`, `C2W` (boat rankings)

The registry is stored in the browser's localStorage after first load.

## Browser Support

- **Chrome / Edge 86+** — Full support (direct file save)
- **Firefox / Safari** — Fallback mode (download modified file)

## Features

- Auto-calculated category from birth year
- Bib suggestion (max+1 in class)
- Participant ID generation (`RGC.ClassId`)
- Duplicate detection (ID, bib, RGC+class)
- Auto-backup before first save
- Revert from backup
- Multiple adds per session
- Add same competitor to multiple classes

## Technical Notes

- Uses string-based XML insertion (not DOM serialization) to preserve original file formatting
- All values are XML-escaped before insertion
- Results template is extracted from existing entries in the same race
- Hardcoded fallback template for races with no existing results
