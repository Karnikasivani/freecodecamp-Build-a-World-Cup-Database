# World Cup Database ⚽

A relational database project built as part of the freeCodeCamp Relational Database Certification. This project models a database containing historical World Cup tournament data (since 2014) and includes automated scripts for data ingestion and report querying.

## Project Structure

- **`worldcup.sql`**: PostgreSQL database dump containing the complete database schema (`teams` and `games` tables) and populated records.
- **`insert_data.sh`**: Bash script that parses `games.csv` and safely inserts team names and game details into the database while avoiding duplicate entries.
- **`queries.sh`**: Bash script executing complex SQL queries to extract statistics, match histories, and tournament summaries matching expected outputs.
- **`games.csv`**: Source dataset containing match years, rounds, winners, opponents, and goals scored.

## Database Schema

The PostgreSQL database consists of two related tables:
1. **`teams`**: Stores unique team names.
   - `team_id` (PK)
   - `name` (Unique)
2. **`games`**: Stores match details and references team IDs.
   - `game_id` (PK)
   - `year`
   - `round`
   - `winner_id` (FK referencing `teams`)
   - `opponent_id` (FK referencing `teams`)
   - `winner_goals`
   - `opponent_goals`

## How to Run

1. **Restore the database:**
   ```bash
   psql -U postgres < worldcup.sql
