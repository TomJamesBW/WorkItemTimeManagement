# Redesign Implementation Plan

## Major Changes Required:

### 1. Work Items Section
- Change from horizontal scrolling vertical cards to 4-column kanban board
- Columns: High, Medium, Low, No Priority
- Vertical scrolling within each column
- Horizontal fixed-height cards
- Remove start/pause buttons from cards
- Add drag-and-drop between columns
- Drag to timer sidebar to start timing

### 2. Work Item Data Structure
- Remove: totalMinutes, originalMinutes, accumulatedMinutes, locked
- Add: description (string), timeRecordings (array of {startTime, endTime, duration})
- Keep: id, title, priority (with 'none' as default)

### 3. Timer Functionality
- No countdown timers
- Start timer by dragging work item to timer sidebar
- Timer tracks elapsed time (count up)
- On stop/pause, save time recording to work item

### 4. UI Changes
- Work items section: scrollable vertically
- Notes section: double height, permanent scroll
- Click card → show detail dialog (title, description, total time logged)
- Remove sort button (no longer needed)

### 5. Data Persistence
- Update import/export to handle new structure
- Migrate old data format to new format

This is a major refactor. Proceeding with implementation...
