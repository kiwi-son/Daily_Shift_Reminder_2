# Daily_Shift_Reminder_2
The Daily Shift Reminder App is an automated notification system designed to ensure employees never miss their scheduled shifts. It sends timely email reminders 1–2 hours before the start of a shift, helping teams stay organized and prepared.
📧 Daily Shift Reminder App

An automated shift reminder system that sends email notifications to employees 1–2 hours before their shift starts. This helps ensure proper coordination, reduces missed shifts, and improves operational efficiency.

🚀 Features
⏰ Automated Shift Alerts
Sends email reminders before shift start time.
📋 Detailed Email Content
Each email includes:
Date
Shift name
Shift Engineer (SIC)
Shift Technicians
Contact numbers
🔄 Supports Complex Scheduling
Single shifts
Double shifts
Multiple employees per shift
🗄️ MongoDB Integration
Stores:
Shift timings
Employee details
Daily schedules
📬 Email Automation
Uses Yagmail to send emails.
⚙️ Fully Automated
Runs using GitHub Actions at scheduled intervals.
🛠️ Tech Stack
Python
MongoDB Atlas
Yagmail
GitHub Actions
pytz (Timezone handling)
📌 How It Works
Connects to MongoDB and fetches shift collections.
Extracts shift start times from the database.
Checks if any shift is starting within the next 2 hours.
Retrieves manpower and employee details from the schedule.
Separates:
SIC (Shift Engineer)
Technicians
Builds a formatted message.
Sends emails to all assigned employees.
📂 Project Structure
├── fetching.py            # Core script for shift processing
├── schedule.py        # Email sending function (Yagmail)
├── .github/workflows  # GitHub Actions automation
├── requirements.txt   # Dependencies
⚙️ Setup Instructions
1️⃣ Clone the Repository
git clone https://github.com/kiwi-son/Daily-Shift-Reminder_2.git
cd daily-shift-reminder
2️⃣ Install Dependencies
pip install -r requirements.txt
3️⃣ Configure MongoDB

Update your MongoDB URI in the script:

client = MongoClient("your_mongodb_connection_string")
4️⃣ Configure Email (Yagmail)

Inside schedule.py:

import yagmail

def send_email(to, msg):
    yag = yagmail.SMTP("your_email@gmail.com", "your_app_password")
    yag.send(to=to, subject="Shift Reminder", contents=msg)
5️⃣ Run Locally
python main.py
⚙️ GitHub Actions Automation
Runs automatically on a schedule (cron job)
Checks shifts periodically
Sends reminders without manual execution

Example workflow:

on:
  schedule:
    - cron: "*/30 * * * *"
⚠️ Notes
Timezone handled using Asia/Kolkata (IST)
Old schedule data is automatically cleaned
Handles missing (None) values safely
Supports dynamic collections for shifts and users
🎯 Use Cases
Industrial shift management
IT support teams
Maintenance operations
Any rotating workforce system
