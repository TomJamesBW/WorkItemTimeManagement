# Work Item Time Management

A single-page time management application for tracking work items with visual time allocation, multiple simultaneous timers, and sticky notes.

## Features

### Work Items
- **Visual Time Cards**: Work items displayed as vertical bars with width proportional to allocated time
- **Priority Colors**:
  - 🔴 High Priority (Red)
  - 🟡 Medium Priority (Gold)
  - 🟢 Low Priority (Green)
- **Multiple Timers**: Run multiple timers simultaneously for different work items
- **Timer Controls**: Start, Pause, Resume, and Cancel functionality
- **Completion Tracking**: Lock completed items with a green checkmark
- **Drag & Drop**: Reorder work items by dragging
- **Context Menu**: Right-click to delete work items

### Timer Sidebar
- **Persistent Sidebar**: Always-visible timer sidebar (350px width)
- **Real-time Countdown**: Live countdown with HH:MM:SS display
- **Progress Bar**: Visual progress indicator for each active timer
- **Live Indicator**: Pulsing red dot shows when timer is actively running
- **Individual Controls**: Play/Pause/Cancel buttons for each timer
- **Add Time**: Option to add additional time when timer completes
- **Audio Alert**: Triple-beep alarm sound using Web Audio API (Safari compatible)
- **Auto-save**: Timer progress saved every 60 seconds and persists across page refreshes
- **Restore on Refresh**: Active timers automatically resume after page reload

### Sticky Notes
- **Draggable Notes**: Position notes anywhere in the notes section
- **Color Selection**: 8 color options for note backgrounds
- **Title & Content**: Notes include both title and text content
- **Collapse/Expand**: Minimize notes to show just the title
- **Context Menu**: Right-click to delete notes
- **Auto-save**: All notes persist to localStorage

### Data Management
- **LocalStorage**: Automatic saving of all data including active timer states
- **JSON Export**: Save work items, notes, and active timers to JSON file
- **JSON Import**: Load work items, notes, and active timers from JSON file
- **Clear Work**: Option to clear all work items, notes, and timers with confirmation dialog

## Technical Specifications

### Technology Stack
- **Pure HTML5**: Single-file application
- **CSS3**: Flexbox layout, transforms, transitions
- **Vanilla JavaScript**: No framework dependencies
- **Web Audio API**: Cross-browser audio support
- **LocalStorage API**: Client-side data persistence

### Browser Compatibility
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest) - Full audio support via Web Audio API

### Architecture
- Single HTML file: `index.html`
- Embedded CSS and JavaScript
- No external dependencies
- No build process required

## Version History

### v1.22 (Current)
**Features:**
- Added auto-save for active timers every 60 seconds (previously 10 seconds)
- Live indicator (pulsing red dot) shows when timers are actively running
- Active timers now fully restore on page refresh with correct state
- Import/Export now includes active timer states

**Changes:**
- Timer state persistence improved for page refreshes
- Active timers show visual live indicator in sidebar
- Export JSON now captures running/paused timer states
- Import JSON restores timer states and resumes active timers

---

### v1.21
**Features:**
- Added "Notes" title to notes section
- Work item start buttons moved to bottom of cards
- Clear Work button now clears both work items and notes
- Added confirmation dialog for Clear Work with warning message

**Changes:**
- Section titles aligned to their respective sections (Work Item Time Management, Notes)
- Both section titles use consistent styling (28px, white, shadow effect)
- Clear Work dialog warns users about wiping all data

---

### v1.20
**Changes:**
- Improved word wrapping to break at word boundaries instead of mid-word
- Title now wraps at the last complete word before 20 characters
- Falls back to 20 character break if no space found within first 10 characters

---

### v1.19
**Changes:**
- Removed "Cancel" button from context menus for notes and work items
- Simplified context menus to only show "Delete" option
- Clicking anywhere outside menu already dismisses it

---

### v1.18
**Features:**
- Work item titles now limited to maximum 40 characters
- Titles longer than 20 characters automatically wrap to second line

**Changes:**
- Title wrapping occurs at 20 character mark
- Titles truncated at 40 characters maximum
- Improved readability for long work item titles

---

### v1.17
**Bug Fixes:**
- Fixed text disappearing from work item cards
- Removed overflow constraints that were hiding card text

**Features:**
- JSON export now includes sticky notes
- JSON import now includes sticky notes
- Backward compatibility with old JSON format (work items only)

**Changes:**
- Export format changed to object containing both workItems and stickyNotes
- Import function handles both old array format and new object format
- Notes are now rendered after import

---

### v1.16
**Bug Fixes:**
- Fixed word wrapping for work item titles that exceed card height
- Added proper text overflow handling for vertical rotated text
- Improved card content padding and constraints

**Changes:**
- Card content now has width/height constraints with overflow hidden
- Title text uses `overflow-wrap: anywhere` for aggressive word breaking
- Added 10px padding inside cards for better text spacing
- Title constrained to max-height: 100% to prevent overflow

---

### v1.15
**Features:**
- Timer auto-save functionality - timers persist across page refreshes
- Active timers automatically restored when page reloads
- Running timers resume from saved state

**Bug Fixes:**
- Fixed padding to prevent work items from overlapping with title
- Adjusted top padding to 80px and bottom padding to 40px
- Fixed max-height calculation to prevent overflow

**Changes:**
- Timers save to localStorage every 10 seconds while running
- Timer state saved on pause and cancel operations
- Deserialization restores timer intervals for running timers
- Improved spacing: 80px from title, 40px from notes section

---

### v1.14
**Features:**
- Added application title "Work Item Time Management" centered at top

**Changes:**
- Title styled with white text, shadow effect, and fixed positioning

---

### v1.13
**Features:**
- Added context menu for work items (right-click to delete)

**Changes:**
- Work items can now be deleted via right-click menu
- Deleting a work item automatically cancels any active timer
- Separate context menus for work items and notes

---

### v1.12
**Bug Fixes:**
- Fixed work item spacing to prevent overlap with top buttons (100px top padding)
- Added 20px bottom padding from notes section
- Improved alarm sound for Safari compatibility

**Changes:**
- Changed to Web Audio API as primary audio method
- Triple-beep alarm sound (880 Hz) for better alerting
- Fallback chain: Web Audio API → HTML5 Audio → Alert dialog

---

### v1.11
**Bug Fixes:**
- Fixed vertical centering of work items
- Fixed card width distribution to properly fill 100% of available space
- Fixed cards showing off-screen to the left

**Changes:**
- Work items section uses flexbox centering
- Removed problematic padding calculations
- Cards-container set to 100% width with proper horizontal padding

---

### v1.10
**Features:**
- Timer sidebar made permanent (no collapse functionality)

**Bug Fixes:**
- Fixed work item card width calculation using flexbox grow
- Fixed note collapse to actually change visual size
- Removed timer sidebar collapse button and related code

**Changes:**
- Simplified timer sidebar to always show at 350px width
- Card wrappers use flexGrow based on time proportion

---

### v1.09
**Bug Fixes:**
- Fixed minimized note alignment (title and button vertically centered)
- Fixed work item card width and positioning
- Fixed timer sidebar initial state (now hidden until first timer)

**Changes:**
- Notes use fixed 40px height when collapsed
- Timer sidebar uses display:none when inactive
- Improved flexbox layout for cards

---

### v1.08
**Bug Fixes:**
- Fixed card width calculation to prevent overflow
- Fixed first card showing off-screen
- Prevented timer sidebar from showing on initial load

**Changes:**
- Improved width calculations with proper gap and padding accounting
- Timer sidebar starts with width:0 and no box-shadow

---

### v1.07
**Features:**
- Note title moved to header row with minimize button when collapsed
- Scrollbar hidden when note is minimized

**Bug Fixes:**
- Fixed note layout to show title next to collapse button
- Fixed scrollbar visibility in collapsed state

---

### v1.06
**Features:**
- Timer collapse button positioned on right with dark blue styling
- Timer sidebar loads collapsed by default
- Lock icon changed to green ASCII tick (✓)
- Fixed buttons changed from floating to fixed position

**Bug Fixes:**
- Fixed timer collapse button positioning and styling
- Card width calculation improved to fill available space
- Increased top padding to prevent card overlap with buttons

**Changes:**
- Reduced gap between cards from 15px to 5px
- Collapse button styled: dark blue background, white arrow
- Arrow direction changes based on collapsed state

---

### v1.05
**Features:**
- Added note title field
- Display title when note is minimized

**Bug Fixes:**
- Fixed card height using flex: 1 instead of calc()
- Fixed card width moved to wrapper element
- Added "Untitled" as default for notes without titles

**Changes:**
- Backward compatibility for notes loaded without title field

---

### v1.04
**Features:**
- Timer sidebar collapse button added

**Bug Fixes:**
- Fixed alarm sound not playing due to browser autoplay restrictions
- Added promise handling for audio playback
- Added Web Audio API oscillator as fallback

**Changes:**
- Alarm uses both HTML5 audio and Web Audio API

---

### v1.03
**Features:**
- Notes section increased to 50% height
- Notes scrollbar added with max height limit
- Collapse button for notes section
- Right-click context menu for notes
- Auto-size cards to available height

**Changes:**
- Notes can be deleted via context menu
- Cards dynamically adjust to container height

---

### v1.02
**Features:**
- Save/Load button moved next to + button
- Post-it notes section added (40% height, later 50%)
- Notes with color picker (8 colors)
- Draggable notes with position persistence

**Bug Fixes:**
- Pause button now closes timer and shows time left/recorded
- Control buttons moved above cards
- Cards set to 50% height aligned to top

**Changes:**
- Time entry labels fixed in dialog
- Notes section added at bottom with scrollbar

---

### v1.01
**Features:**
- Timer sidebar instead of overlay (white column on right)
- Multiple simultaneous timers support
- Start/Pause button toggle on cards
- Play/Pause/Cancel buttons on timer cards

**Bug Fixes:**
- Fixed card text layout

**Changes:**
- Timers displayed in sidebar with individual controls
- Multiple timers can run at once

---

### v1.00 (Initial Release)
**Features:**
- Full-page application with gradient background
- Floating + button for adding work items
- Work item cards with priority colors
- Cards with vertical text
- Dynamic width based on allocated time
- Timer functionality with countdown and progress bar
- Save/Load functionality with JSON export/import
- LocalStorage persistence

## Data Structure

### Work Items
```javascript
{
  id: timestamp,
  title: string,
  totalMinutes: number,
  priority: 'high' | 'medium' | 'low',
  locked: boolean
}
```

### Active Timers
```javascript
{
  itemId: number,
  index: number,
  remainingSeconds: number,
  totalSeconds: number,
  paused: boolean,
  interval: setInterval reference,
  timestamp: number (for serialization)
}
```

### Sticky Notes
```javascript
{
  id: timestamp,
  title: string,
  text: string,
  color: string (hex),
  x: number,
  y: number,
  collapsed: boolean
}
```

## Usage

### Adding a Work Item
1. Click the green **+** button
2. Enter work item name
3. Set time required (hours and minutes)
4. Select priority level
5. Click **Add**

### Starting a Timer
1. Click **Start** button on work item card
2. Timer appears in right sidebar
3. Use Play/Pause/Cancel buttons to control

### Completing Work
When timer finishes:
- Audio alarm plays (triple beep)
- Dialog offers options:
  - **Complete Item**: Locks item with green ✓
  - **Add More Time**: Extend the timer

### Managing Notes
1. Click yellow **+** button in notes section
2. Enter title and text
3. Choose a color
4. Click **Add**
5. Drag note to desired position
6. Click **−** button to collapse/expand
7. Right-click to delete

### Saving/Loading
- **Save to JSON**: Export work items, notes, and active timers to file
- **Import JSON**: Load work items, notes, and active timers from file
- **Clear Work**: Remove all work items, notes, and timers (with confirmation dialog)
- Auto-save to localStorage every 60 seconds for active timers
- Timers automatically restore on page refresh

## Keyboard Shortcuts
- **Right-click** on work item: Delete menu
- **Right-click** on note: Delete menu
- **Drag** work item card: Reorder items
- **Drag** note: Reposition in notes area

## Known Limitations
- Maximum of one timer per work item at a time
- Notes are constrained to notes section boundaries
- No undo functionality for deletions
- No search or filter functionality
- Timer accuracy depends on tab/browser activity (timers may drift if tab is inactive)

## Future Enhancements
- Work item categories/tags
- Search and filter capabilities
- Undo/redo functionality
- Keyboard shortcuts
- Export notes separately
- Multiple timer instances per item
- Statistics and reporting
- Dark mode option

## License
This is a single-page application created for personal time management. Feel free to use and modify as needed.

## Support
For issues or feature requests, please refer to the version history and ensure you're using the latest version (v1.22).
