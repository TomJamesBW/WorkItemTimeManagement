# Work Item Time Management

A single-page time management application for tracking work items with a kanban board interface, count-up time tracking, date-based time logging, and sticky notes.

## Features

### Work Items
- **Kanban Board Layout**: Work items organized in 4 columns (High, Medium, Low, No Priority)
- **Priority Colors**:
  - 🔴 High Priority (Red/Pink pastel)
  - 🟡 Medium Priority (Gold/Yellow pastel)
  - 🟢 Low Priority (Green pastel)
  - 🔵 No Priority (Blue pastel)
- **Drag & Drop**: Move work items between priority columns
- **Time Tracking**: Count-up timers track actual time spent on tasks
- **Date-based Logging**: All time recordings include date stamps
- **Work Item Details**: Click any card to view title, description, total logged time, and last 7 days breakdown
- **Context Menu**: Right-click to archive or delete work items
- **Description Field**: Each work item includes an optional description

### Timer Sidebar
- **Persistent Sidebar**: Always-visible timer sidebar (350px width)
- **Count-Up Timers**: Track elapsed time with HH:MM:SS display
- **Drag-to-Start**: Drag work items to timer sidebar to start tracking time
- **Live Indicator**: Pulsing red dot shows when timer is actively running
- **Individual Controls**: Play/Pause/Stop buttons for each timer
- **Time Recording**: Stopping a timer saves the recording with date stamp to the work item
- **Auto-save**: Timer progress saved every 60 seconds and persists across page refreshes
- **Restore on Refresh**: Active timers automatically resume after page reload

### Sticky Notes
- **Draggable Notes**: Position notes anywhere in the notes section
- **Resizable**: Drag bottom-right corner to resize notes (150px-400px width, adjustable height)
- **Color Selection**: 8 color options for note backgrounds
- **Title & Content**: Notes include both title and text content
- **Collapse/Expand**: Minimize notes to show just the title
- **Context Menu**: Right-click to delete notes
- **Auto-save**: All notes persist to localStorage including custom dimensions

### Data Management
- **LocalStorage**: Automatic saving of all data including active timer states
- **JSON Export**: Save work items, notes, archived items, and active timers to JSON file
- **JSON Import**: Load work items, notes, archived items, and active timers from JSON file
- **Archive System**: Archive completed work items to preserve title, description, and priority (time data removed)
- **Archive View**: Browse archived items with restore or permanent delete options
- **Clear Work**: Option to clear all work items, notes, and timers with confirmation dialog

## Technical Specifications

### Technology Stack
- **Pure HTML5**: Single-file application
- **CSS3**: Grid layout (kanban board), flexbox, transitions
- **Vanilla JavaScript**: No framework dependencies
- **Drag and Drop API**: Native HTML5 drag and drop
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

### v2.0 (Current) - Major Redesign
**Breaking Changes:**
- Complete redesign from horizontal scrolling cards to 4-column kanban board
- Changed from countdown timers to count-up time tracking
- Removed time allocation input - work items now track actual time spent
- Removed locked/completed state tracking

**New Features:**
- **Kanban Board**: 4 columns (High, Medium, Low, No Priority) with vertical scrolling
- **Count-Up Timers**: Track elapsed time instead of counting down
- **Drag-to-Timer**: Drag work items to timer sidebar to start tracking
- **Date-based Time Logging**: All time recordings include date stamps (YYYY-MM-DD format)
- **Work Item Details Dialog**: Click any card to view:
  - Title and description
  - Total time logged across all sessions
  - Last 7 days breakdown with daily time totals
- **Description Field**: Work items now include an optional description field
- **Time Recordings Array**: Each work item stores array of time recordings with startTime, endTime, duration, and date

**Layout Changes:**
- Work items section: 60% height with vertical scrolling
- Notes section: 40% height with permanent scroll
- Removed Sort button (no longer needed with kanban columns)
- Increased top padding to 90px for better button spacing

**Data Structure Changes:**
- NEW: `{id, title, description, priority, timeRecordings: [{startTime, endTime, duration, date}]}`
- REMOVED: totalMinutes, originalMinutes, accumulatedMinutes, locked fields
- Added 'none' as default priority option
- Full backward compatibility with v1.x data (automatic migration)

**Technical Improvements:**
- CSS Grid layout for kanban columns
- Pastel color scheme for priority columns
- Horizontal card layout (min 60px, max 80px height)
- Migration functions ensure old data imports correctly

---

### v1.27
**Bug Fixes:**
- Increased Sort button spacing from left: 200px to 230px for better separation from Save/Load button
- Disabled resize handle on collapsed notes (resize: none when collapsed)

**Changes:**
- Sort button now has 30px more spacing to prevent overlap
- Collapsed notes cannot be resized until expanded

---

### v1.26
**Bug Fixes:**
- Fixed font sizing to apply uniformly across all work items based on average card width
- Fonts now only shrink when there are many cards (not individual card basis)
- Fixed note resize functionality - resize handle now works properly in bottom-right corner
- Prevented drag interference with resize by detecting resize area clicks

**Changes:**
- Font sizing uses average card width calculation
- All cards get same font size class (tiny/small/normal) for consistency
- Note resize handle area (15px corner) blocks dragging
- Changed note overflow from `hidden` to `auto` to enable resize

---

### v1.25
**Features:**
- Notes are now resizable by the user (drag resize handle in bottom-right corner)
- Added Sort button to sort work items by time (largest to smallest, left to right)
- Fonts automatically shrink for slim cards or wrapped text for better readability
- Reset Timer now properly restores original time and clears accumulated time

**Changes:**
- Notes store and restore custom width and height
- Work items track `originalMinutes` for proper reset functionality
- Font sizes adjust dynamically: tiny (<60px width), small (<90px width), normal (≥90px)
- Sort button positioned at left: 200px with purple background

---

### v1.24
**Bug Fixes:**
- Fixed Close Timer (Save Progress) logic to properly calculate remaining time
- Work item now shows remaining time with accumulated time in brackets
- Example: After using 2 minutes of a 30-minute task, displays "28h 2m (0h 2m)"

**Changes:**
- Added `accumulatedMinutes` field to track time already used
- Remaining time is now the primary display value
- Accumulated time shown in brackets after main time
- Timer reopens with correct remaining time
- Backward compatibility maintained for existing work items

---

### v1.23
**Features:**
- Added cancel timer confirmation dialog with two options
- **Close Timer (Save Progress)**: Closes timer and updates work item to reflect time already used
- **Reset Timer**: Closes timer and restores work item to original time allocation

**Changes:**
- Cancel button now shows confirmation dialog instead of immediately canceling
- Time progress can be saved when closing a timer early
- Work item time dynamically updates based on cancel choice

---

### v1.22
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

### Work Items (v2.0)
```javascript
{
  id: timestamp,
  title: string,
  description: string, // Optional description field
  priority: 'high' | 'medium' | 'low' | 'none', // Default: 'none'
  timeRecordings: [ // Array of all time tracking sessions
    {
      startTime: timestamp,
      endTime: timestamp,
      duration: seconds,
      date: 'YYYY-MM-DD' // ISO date string
    }
  ]
}
```

### Archived Items
```javascript
{
  id: timestamp,
  title: string,
  description: string,
  priority: 'high' | 'medium' | 'low' | 'none',
  archivedDate: ISO date string // When item was archived
  // Note: timeRecordings are NOT preserved in archive
}
```

### Active Timers (v2.0)
```javascript
{
  itemId: number,
  elapsedSeconds: number, // Count-up instead of countdown
  paused: boolean,
  startTime: timestamp, // When timer was started
  interval: setInterval reference
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
  collapsed: boolean,
  width: number, // Custom width in pixels
  height: number // Custom height in pixels
}
```

## Usage

### Adding a Work Item
1. Click the green **+** button
2. Enter work item title (required)
3. Enter description (optional)
4. Click **Add** (item appears in "No Priority" column by default)

### Organizing Work Items
1. **Drag work items** between priority columns (High, Medium, Low, No Priority)
2. Items are displayed as horizontal cards within their priority column
3. Each column scrolls independently

### Tracking Time
1. **Drag work item** to the timer sidebar to start tracking time
2. Timer counts up from 00:00:00 showing elapsed time
3. Use **Play/Pause** buttons to pause/resume timer
4. Click **Stop** button to save the time recording
5. Time recording is automatically saved with current date

### Viewing Work Item Details
1. **Click any work item card** to open detail dialog
2. Dialog shows:
   - Full title and description
   - Total time logged across all sessions
   - **Last 7 days breakdown** with date and daily time totals
3. Click **Close** to dismiss dialog

### Managing Notes
1. Click yellow **+** button in notes section
2. Enter title and text
3. Choose a color
4. Click **Add**
5. Drag note to desired position
6. Click **−** button to collapse/expand
7. Right-click to delete

### Archiving Work Items
1. **Archive an item**: Right-click work item and select "Archive"
2. Confirmation dialog warns that time tracking data will be permanently removed
3. Archived items retain only title, description, and priority
4. **View archive**: Click Save/Load button → View Archive
5. **Restore from archive**: Click "Restore" button on archived item (creates new work item with no time data)
6. **Delete archived item**: Click "Delete" button for permanent removal

### Saving/Loading
- **Save to JSON**: Export work items, notes, archived items, and active timers to file
- **Import JSON**: Load work items, notes, archived items, and active timers from file
- **View Archive**: Browse all archived work items with options to restore or permanently delete
- **Clear Work**: Remove all work items, notes, and timers (with confirmation dialog)
- Auto-save to localStorage every 60 seconds for active timers
- Timers automatically restore on page refresh
- Full backward compatibility with v1.x JSON exports (automatic migration)

## Keyboard Shortcuts
- **Right-click** on work item: Archive or delete menu
- **Right-click** on note: Delete menu
- **Drag** work item card: Move between priority columns
- **Drag** work item to sidebar: Start timer
- **Drag** note: Reposition in notes area
- **Click** work item card: View details and time breakdown

## Known Limitations
- Maximum of one timer per work item at a time
- Notes are constrained to notes section boundaries
- No undo functionality for deletions
- No search or filter functionality
- Timer accuracy depends on tab/browser activity (timers may drift if tab is inactive)
- Time breakdown shows last 7 days only (older recordings still stored but not displayed)

## Future Enhancements
- Work item categories/tags
- Search and filter capabilities within active items and archive
- Undo/redo functionality
- Extended time breakdown reports (monthly, yearly)
- Export time recordings to CSV
- Statistics dashboard with charts and analytics
- Multiple timer instances per item
- Dark mode option
- Archive with time data preservation option
- Bulk archive operations

## License
This is a single-page application created for personal time management. Feel free to use and modify as needed.

## Support
For issues or feature requests, please refer to the version history and ensure you're using the latest version (v2.0).

## Migration from v1.x to v2.0
If you have existing v1.x data:
- All v1.x JSON exports are automatically migrated when imported
- Old work items with time allocations are converted to new format with empty timeRecordings array
- Priority levels are preserved (high, medium, low)
- Notes are fully compatible and require no migration
- Active timers from v1.x will not restore (only new v2.0 timers persist)
