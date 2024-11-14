# Web_Scraping_TourApp

This Python program checks a specified URL for upcoming events and sends an email notification if new events are found. The program uses web scraping to gather event data from a webpage, stores the data in a local SQLite database, and only sends notifications for unique events that haven't been previously recorded.

## Features
- **Web Scraping**: Uses `requests` and `selectorlib` to extract event information from a webpage.
- **Database Storage**: SQLite stores event data, avoiding duplicate notifications.
- **Email Notifications**: Sends an email alert whenever a new event is found.
- **Automation**: Runs continuously and checks for updates at specified intervals.

## Requirements
- Python 3.x
- `requests`
- `selectorlib`
- `smtplib` (built into Python)
- `sqlite3` (built into Python)

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/event-notifier.git

    Navigate to the project directory:

cd event-notifier

Install required Python packages:

    pip install requests selectorlib

Configuration
1. Email Setup

To use the email notification feature, you need to set up your email account:

    Gmail is used in this example, but any SMTP server will work.
    Enable App Passwords in your Gmail account (recommended) and replace sensitive data with environment variables.

2. Set Up Environment Variables (Optional)

For better security, store your email password as an environment variable:

    EMAIL_PASSWORD: Your email account’s app password.

Example setup:

export EMAIL_PASSWORD="your_app_password"

CSV File Format

    Create a topics.csv file with the following structure:

    Topic, Pages
    Introduction, 3
    Analysis, 2

Usage

    Prepare the Selector YAML File:
        Create an extract.yaml file that defines how to extract information from the webpage. Example:

    tours:
      css: "div.tour"
      type: Text

Run the Program:

    python main.py

    Program Behavior:
        Scrapes the specified URL for event data every hour.
        Extracts event data using CSS selectors defined in extract.yaml.
        If a new event is found, stores it in an SQLite database (data.db) and sends an email notification.

Code Overview
Main Functions:

    scrape(URL): Fetches the webpage content.
    extract(source): Extracts the tour/event data from the page content using selectorlib.
    store(extracted): Stores the new event in the database to avoid duplicates.
    read(extracted): Checks if the event is already in the database.
    send_email(message): Sends an email alert when a new event is found.

Database Structure

    Table: events
    Columns:
        band: Name of the band/performer.
        city: Location of the event.
        date: Date of the event.

Example Output

    When a new event is found, it will output:

    New event found! Sending email notification...
    Email was sent!

Contributing

Feel free to fork the repository and submit a pull request for improvements or additional features.
