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

### Task 001-01: Create Admin Report View Structure
- [x] Create new admin view for search tracking report
- [x] Add URL routing for the report
- [x] Create basic HTML template with date range filter
- [x] Add navigation link in admin menu

**Status**: Done
**Assigned**: 2025-06-13
**Completed**: 2025-06-13

### Task 001-02: Implement Date Range Filtering
- [x] Add date range picker to template
- [x] Implement backend logic to filter by date range
- [x] Add form validation for date inputs
- [x] Test date filtering functionality

**Status**: Done
**Assigned**: 2025-06-13
**Completed**: 2025-06-13

### Task 001-03: Calculate Search Tracking Aggregates
- [x] Create database queries for Total Searches by day
- [x] Create database queries for DDG Clicks by day
- [x] Create database queries for AI Box Loads by day
- [x] Create database queries for AI Box Expands by day
- [x] Create database queries for AI Box Clicks by day
- [x] Calculate percentage of total for each metric

**Status**: Done
**Assigned**: 2025-06-13
**Completed**: 2025-06-13

### Task 001-04: Add Tracking Metrics Chart
- [x] Research Chart.js documentation for line charts with multiple series
- [x] Add Chart.js library to the page
- [x] Create chart container below the existing table
- [x] Add dropdown with checkboxes for data series selection:
  - [x] DDG Clicks, AI Box Loads, AI Box Expands, AI Box Clicks
- [x] Extract data from existing table to populate chart
- [x] Render line chart with selected metrics over time
- [x] Connect dropdown changes to chart updates
- [x] Style chart to match admin theme

**Status**: Done
**Assigned**: 2025-06-13
**Completed**: 2025-06-13

### Task 001-05: Add Total Searches Chart
- [x] Create second chart container below the tracking metrics chart
- [x] Extract Total Searches data from existing table
- [x] Render simple line chart showing search volume over time
- [x] Use different color/styling than tracking metrics chart
- [x] Add chart title "Total Searches per Day"
- [x] Ensure both charts update when date filter is applied

**Status**: Done
**Assigned**: 2025-06-13
**Completed**: 2025-06-13

### Task 001-06: Refactoring of the tracking metrics chart
- [x] Convert tracking metrics chart from line chart to stacked bar chart
- [x] Add new metrics to track:
  - [x] AI Box Clicks (existing)
  - [x] AI Box No-Clicks (total_searches - ai_box_clicks)
  - [x] Calculate and display percentages for both metrics
- [x] Update chart styling:
  - [x] Use distinct colors for clicks vs no-clicks
  - [x] Add legend showing both metrics
  - [x] Ensure proper stacking of bars
- [x] Update tooltips to show:
  - [x] Raw numbers for each metric
  - [x] Percentage of total searches
  - [x] Clear labels for clicks vs no-clicks
- [x] Add summary statistics below chart:
  - [x] Overall percentage of users who use AI (clicks/total)
  - [x] Overall percentage of users who don't use AI (no-clicks/total)
  - [x] Format percentages to one decimal place
- [x] Update chart title and axis labels to reflect new metrics
- [x] Ensure chart updates properly with date filter changes

**Status**: Done
**Assigned**: 2025-06-13
**Completed**: 2025-06-13

### Task 001-07: Restore and Fix Top AI Box Usage Metrics Chart
- [x] Restore the top AI Box Usage Metrics chart as a stacked bar chart (AI Clicks, DDG Clicks, No Clicks)
- [x] Add summary boxes above the chart for each metric (showing count and percent)
- [x] Ensure chart and boxes use correct, independent data and DOM IDs
- [x] Confirm both top and bottom charts work independently

**Status**: Done
**Assigned**: 2025-06-13
**Completed**: 2025-06-13

## Notes
- Consider using Chart.js or similar for visualization
- Ensure proper indexing on timestamp field for performance
