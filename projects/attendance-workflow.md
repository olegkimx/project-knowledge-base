# Attendance Workflow

## Overview

The Attendance Workflow project is a check-in tool designed for club events. It helps event organizers search membership records, log attendance for a specific event, and identify whether an attendee has already paid their membership fee.

I built the original version while serving as Treasurer for a student community organization. The club frequently had long check-in queues at events, and the manual process could delay event agendas by roughly 30 minutes. I wanted to apply my operations, logistics, and business analytics background to reduce that bottleneck and create cleaner attendance data for future planning.

The original project was built as a local desktop workflow with Python, Tkinter, Google Forms, Google Sheets, GSpread, and Pandas.

## Problem

Manual event check-in can become slow and error-prone when organizers need to:

- Confirm whether someone is already registered
- Track attendance for each event
- Support non-student or guest attendees
- Identify unpaid members during check-in
- Avoid duplicate attendance entries
- Keep records in a format that non-technical organizers can still use

The workflow also needed to support finance and planning responsibilities. As Treasurer, attendance and membership data helped inform conversations about event expenses, membership fee collection, and the club's financial stability.

## Core Features

### Event Setup

Organizers enter the event name at launch. The workflow either reuses an existing event worksheet or creates a new attendance sheet for that event.

### Membership Intake

Attendees first submit a membership form with their name, email address, and student ID. Form responses flow into a membership spreadsheet that acts as the source of truth for check-in.

### Member Lookup

The check-in form accepts a student ID and compares it against the membership spreadsheet.

### Guest Check-In

If an attendee does not have a student ID, the workflow collects name and email information manually.

### Duplicate Prevention

Before logging a check-in, the workflow checks whether that student ID already exists in the event attendance sheet.

### Payment Status

The workflow displays whether the member has already paid, helping organizers follow up at the event.

If a student ID is found but the membership fee is unpaid, the workflow prompts the organizer to collect or confirm payment manually.

### Spreadsheet Logging

Successful check-ins are appended to the event worksheet with student ID, first name, last name, email, and payment status.

### Reporting Foundation

The generated attendance worksheets can be used later for dashboards in tools such as Tableau or Power BI.

## Feature Map

### Membership Records

Central list of member names, student IDs, emails, and payment status.

### Membership Form

Google Form used to collect member intake data before or during events.

### Event Worksheets

Separate attendance logs for each event, created or reused by event name.

### Check-In Interface

Simple desktop UI for entering student IDs and recording attendance.

### Payment Follow-Up

Visual alerts help organizers distinguish paid members from members who still need to pay.

### Test Data Seeding

Sample records can be generated for testing the workflow without using real member data.

### Analytics Output

Attendance data can be summarized to help evaluate event performance, fee collection, and planning decisions.

## Technical Decisions

### Python

Used for quick automation, spreadsheet access, and local desktop tooling.

### Tkinter

Used to create a simple local interface without requiring a web server.

### Google Sheets

Used as a lightweight database because the target users were already comfortable with spreadsheets.

### Google Forms

Used as the intake layer for collecting member information in a familiar format.

### Service Account Authentication

Used for programmatic access to spreadsheets. In a production-ready version, credentials should be stored outside the repository and loaded through environment variables or a secrets manager.

## Security Notes

This project uses sensitive Google credentials. The public version should never include:

- Service-account JSON files
- Real spreadsheet URLs
- Real student IDs
- Real names or emails
- Screenshots containing private data

For a portfolio demo, the safest version should use synthetic data and a backend/serverless layer if the app needs to access private APIs.

## Portfolio Demo Plan

The public portfolio version can be redesigned as a browser-based demo with fake data:

- Event selector
- Student ID search
- Guest check-in flow
- Attendance table
- Payment status badge
- Duplicate check-in warning
- Analytics snapshot showing attendance, paid members, unpaid members, and guest count

This would let employers interact with the workflow without exposing private code, private spreadsheets, or real credentials.

## Impact

The project translated a recurring operational issue into a structured workflow. It reduced manual lookup during event check-in, made payment follow-up easier, and produced cleaner event data that could support financial and operational analysis.

The broader goal was not only to automate a task, but to leave behind a process future club executives could continue improving.

## Lessons Learned

- Simple tools can solve real operational problems when they match the workflow users already understand.
- Credentials must be treated as secrets from the beginning, even in small projects.
- A spreadsheet can be a practical first data store, but it needs clear validation rules and careful access control.
- Public portfolio demos should use sanitized data and protect private implementation details behind a backend when needed.
- Operational projects are strongest when they improve the live workflow and create useful data for later decisions.
