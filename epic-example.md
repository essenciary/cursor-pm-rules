<!-- add to epics/epic-<epic_number>-<epic_description>.md -- ex: epic-001-report-for-search-tracking-data.md -->
# Epic 001: Report for Search Tracking Data

## Overview
Implement report in admin for visualizing aggregate stats for search tracking data.
Search objects are defined in messages.py.

Search tracking is provided via the following fields:
- tracking_loaded
- tracking_expanded
- tracking_clicked_item_index
- tracking_clicked_ddg_item_index

Other relevant fields:
- timestamp
- input
- result
- rating
- redirection

## Requirements
- Create a report in admin for visualizing aggregate stats for search tracking data
- The report should be able to filter by date range
- The report should show aggregates by day plus percentages of total for:
  - Total Searches
  - DDG Clicks (tracking_clicked_ddg_item_index > -1)
  - AI Box Loads (tracking_loaded)
  - AI Box Expands (tracking_expanded)
  - AI Box Clicks (tracking_clicked_item_index > -1)

## Tasks

### Task 001-01: First task TBD
- [ ] First item TBD
- [ ] Second item TBD
- [ ] ...

### Task 001-02: Second task TBD
- [ ] First item TBD
- [ ] Second item TBD
- [ ] ...

## Notes
- Consider using Chart.js or similar for visualization
- Ensure proper indexing on timestamp field for performance




