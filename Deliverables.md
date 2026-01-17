# Vibe
https://www.canva.com/design/DAG-snR183U/d31fZcxLdKfA_OkbTMznRQ/edit?ui=e30
https://supabase.com/dashboard/project/dgooflchvietrrkbbket

# Steps 
0. User  **Softr**
- Ask the user questions
- Create account for the user (database of users/google account/apple account/)
- User authentication 
- UI/UX/Frontend graphs and charts 
- how many cards do you have, visa statement date, prefer at every statement or at the end of the month
**Supabase**
Supabase database 1:
- user data (id, name, email, **ai_insight**)
- id: UUID Primary Key
Supabase database 2:
- transactions (id, created_at, amount, description, category, source, user_id)
- user_id: UUID Foreign Key linked to users.id

1. Collect data 
**Apple Shortcut**
- Apple pay shortcut*
- Categorize information in a specific*
- Bank statement pdf processing**
**Gumloop Flows**
* Receive data from Apple Shortcuts via webhook → categorize with AI → store in database: 
A - The trigger is the iOS Shortcut 
B - Webhook Trigger (accepts etc)
C - Ask AI : put info (categorize) on Supabase
D - Postgres - execute query (SQL)
** Process uploaded PDFs → extract transactions → categorize → store 
A - The user on Softr uploads their file if they want to 
B - Webhook Trigger: set to accept a file (pdf)
C - PDF to Text Node: Extract raw text
D - Ask Ai: extract all transactions
E - Loop NodeL iterate through the list
F - Compare with existing list and add new items (Maybe a separate flow)

2. Analyze data***
- update graphs and charts
- insights/advice based on income and spendings
*** Analyze spending patterns → generate insights with AI → create reports
A - Trigger: Scheduled weekly or their choice or button click -> update ai_insight 
B - Postgres query (take from transactions where user_id = ... and created_at > now() - interval)
C - Ask AI: analyze this spending data. write a friendly 2 - sentence 
D - Postgres query (UPDATE users SET ai_insight = '{{ai_summary}}' WHERE id = ...)
E - Maybe this sends smtg to the user as an email to update them 

3. Connect to frontend
**** Weekly/monthly automated summaries sent to users