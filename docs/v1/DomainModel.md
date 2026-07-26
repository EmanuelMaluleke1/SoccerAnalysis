# Domain Model
## Soccer Analyst Platform – Version 1 (Football Data Platform)

**Document Version:** 1.0  
**Status:** Draft  
**Project:** Soccer Analyst Platform  
**Release:** Version 1 (MVP)

---

# 1. Purpose

This document describes the main business objects managed by the Soccer Analyst Platform.

It explains what information the platform stores, how the different business objects relate to one another, and the rules that govern them.

The domain model is independent of the application's implementation. It focuses on the football business rather than databases, APIs, or programming languages.

This document provides the foundation for:

- System Architecture
- Database Design
- API Design
- Application Development
- Future Analytics and Machine Learning

---

# 2. Overview

Version 1 of the Soccer Analyst Platform is a football data platform.

The platform imports football data from external data providers and stores it in a structured format.

Users can browse competitions, seasons, teams, players, fixtures, standings, and statistics through the application.

The platform has been designed so that future versions can introduce advanced analytics, machine learning, match predictions, and AI-powered insights without changing the core business model.

---

# 3. Main Business Objects

The Soccer Analyst Platform manages the following business objects.

- Competition
- Season
- Team
- Player
- Venue
- Fixture
- Match Event
- Standing
- Match Statistics
- Team Statistics
- Player Statistics

---

## 3.1 Competition

### Description

A competition is a football tournament where teams compete against one another.

Examples include:

- Premier League
- UEFA Champions League
- La Liga
- Serie A

### Information

- Competition ID
- Name
- Country
- Competition Type
- Logo
- Current Season

### Business Rules

- A competition can have multiple seasons.
- A competition contains many teams.
- A competition contains many fixtures.

---

## 3.2 Season

### Description

A season represents one edition of a competition.

Examples include:

- Premier League 2024/25
- Premier League 2025/26

### Information

- Season ID
- Competition
- Start Date
- End Date
- Current Season

### Business Rules

- A season belongs to one competition.
- A season contains many fixtures.
- A season has one league table.

---

## 3.3 Team

### Description

A team represents a football club or national team that participates in competitions.

Examples include:

- Arsenal
- Liverpool
- Manchester City

### Information

- Team ID
- Name
- Short Name
- Country
- Founded Year
- Stadium
- Club Colours
- Club Logo

### Business Rules

- A team can participate in multiple competitions.
- A team can participate in multiple seasons.
- A team has many players.
- A team plays many fixtures.
- A team has statistics for each season.

---

## 3.4 Player

### Description

A player represents a football player who belongs to a team.

### Information

- Player ID
- Full Name
- Date of Birth
- Nationality
- Position
- Preferred Foot
- Height
- Weight
- Current Team

### Business Rules

- A player belongs to one team at a time.
- A player can participate in many fixtures.
- A player has statistics for each season.
- A player can be involved in many match events.

---

## 3.5 Venue

### Description

A venue is the stadium where a fixture takes place.

### Information

- Venue ID
- Stadium Name
- City
- Country
- Capacity

### Business Rules

- A venue can host many fixtures.
- Every fixture is played at one venue.

---

## 3.6 Fixture

### Description

A fixture represents a football match between two teams.

A fixture may be scheduled, in progress, postponed, cancelled, or completed.

### Information

- Fixture ID
- Competition
- Season
- Home Team
- Away Team
- Venue
- Match Date
- Kick-off Time
- Status
- Home Goals
- Away Goals

### Business Rules

- Every fixture belongs to one competition.
- Every fixture belongs to one season.
- Every fixture has one home team.
- Every fixture has one away team.
- Every fixture has one venue.
- A fixture can contain many match events.
- A completed fixture can have one set of match statistics.

---

## 3.7 Match Event

### Description

A match event represents an important event that occurs during a fixture.

Examples include:

- Goal
- Own Goal
- Penalty
- Yellow Card
- Red Card
- Substitution
- VAR Decision

### Information

- Event ID
- Fixture
- Team
- Player
- Minute
- Event Type

### Business Rules

- Every match event belongs to one fixture.
- A fixture can contain many match events.
- A player can be involved in multiple match events.

---

## 3.8 Standing

### Description

A standing represents a team's position in a competition during a season.

### Information

- Position
- Team
- Played
- Won
- Drawn
- Lost
- Goals For
- Goals Against
- Goal Difference
- Points

### Business Rules

- A standing belongs to one competition.
- A standing belongs to one season.
- Each team has one standing within a competition season.

---

## 3.9 Match Statistics

### Description

Match statistics describe the performance of both teams during a fixture.

Examples include:

- Possession
- Shots
- Shots on Target
- Corners
- Fouls
- Offsides
- Yellow Cards
- Red Cards
- Attendance
- Referee

### Business Rules

- Match statistics belong to one fixture.
- A completed fixture can have one set of match statistics.

---

## 3.10 Team Statistics

### Description

Team statistics measure the performance of a team over a season or competition.

Examples include:

- Matches Played
- Wins
- Draws
- Losses
- Goals Scored
- Goals Conceded
- Pass Accuracy
- Tackles
- Interceptions
- Clean Sheets

### Business Rules

- Team statistics belong to one team.
- Team statistics belong to one season.
- Statistics are updated after every completed fixture.

---

## 3.11 Player Statistics

### Description

Player statistics measure the performance of an individual player.

Examples include:

- Appearances
- Minutes Played
- Goals
- Assists
- Shots
- Passes Completed
- Tackles
- Yellow Cards
- Red Cards

### Business Rules

- Player statistics belong to one player.
- Player statistics belong to one season.
- Statistics are updated after every completed fixture.

---

# 4. Relationships

The main business objects are related as shown below.

```text
Competition
│
├── Seasons
│
├── Teams
│
└── Fixtures
      │
      ├── Home Team
      ├── Away Team
      ├── Venue
      ├── Match Events
      └── Match Statistics

Season
│
├── Standings
├── Team Statistics
└── Player Statistics

Team
│
├── Players
├── Team Statistics
└── Standings

Player
│
├── Player Statistics
└── Match Events
```

---

# 5. Business Rules

The following rules apply across the platform.

- A competition contains one or more seasons.
- A season belongs to one competition.
- A team can participate in multiple competitions.
- A team has many players.
- A player belongs to one team at a time.
- Every fixture has one home team.
- Every fixture has one away team.
- Every fixture belongs to one competition.
- Every fixture belongs to one season.
- Every fixture has one venue.
- Every fixture can contain many match events.
- Every completed fixture can have one set of match statistics.
- Each team has one standing per competition season.
- Team statistics are maintained for each season.
- Player statistics are maintained for each season.

---

# 6. Future Expansion

The Version 1 domain model provides the foundation for future versions of the platform.

Future business objects may include:

- Team Form
- Player Form
- Expected Goals (xG)
- Expected Assists (xA)
- Team Ratings
- Player Ratings
- Elo Ratings
- Prediction Models
- Match Predictions
- Prediction Explanations
- AI Football Analyst

These features will use the football data collected in Version 1 to provide deeper analysis and insights.

---

# 7. Summary

The Version 1 domain model defines the core football concepts managed by the Soccer Analyst Platform.

It provides a clear description of competitions, seasons, teams, players, fixtures, standings, and statistics, creating a solid business foundation for the rest of the platform and supporting future expansion into analytics, machine learning, and artificial intelligence.