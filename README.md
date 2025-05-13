# Family Travel Tracker

A web application that allows family members to track countries they've visited around the world on a shared map.

## Features

- Interactive world map highlighting visited countries
- Multi-user support with user-specific country tracking
- Color-coded visualization for each family member
- Add new countries via search functionality
- Add new family members with custom colors

## Technologies Used

- **Backend**: Node.js with Express
- **Database**: PostgreSQL
- **Frontend**: EJS templates, CSS
- **Map Visualization**: SVG world map

## Setup Instructions

### Prerequisites

- Node.js
- PostgreSQL

### Database Setup

1. Create a PostgreSQL database named `world`
2. Set up the following tables:

```sql
-- Countries table
CREATE TABLE countries (
  country_code CHAR(2) PRIMARY KEY,
  country_name VARCHAR(100) NOT NULL
);

-- Users table
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  color VARCHAR(50) NOT NULL
);

-- Visited countries table
CREATE TABLE visited_countries (
  id SERIAL PRIMARY KEY,
  country_code CHAR(2) NOT NULL,
  user_id INT NOT NULL,
  FOREIGN KEY (country_code) REFERENCES countries(country_code),
  FOREIGN KEY (user_id) REFERENCES users(id),
  UNIQUE(country_code, user_id)
);
```

3. Import country data into the countries table

### Installation

1. Clone this repository
2. Install dependencies:
   ```
   npm install
   ```
3. Update the database configuration in `index.js` with your PostgreSQL credentials
4. Start the application:
   ```
   node index.js
   ```
5. Open your browser and navigate to `http://localhost:3000`

## Usage

- Select a user from the dropdown to view their visited countries
- Add a new country by typing its name in the search box
- Add new family members with their name and preferred color 
