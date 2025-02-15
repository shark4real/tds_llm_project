# README - DataWorks Solutions Automation Agent

## Overview
This project is an **Automation Agent** for DataWorks Solutions, designed to execute **plain-English** tasks, process **log files, reports, and data artifacts**, and provide **structured outputs**. The agent integrates with a **Large Language Model (LLM)** to parse instructions and automate multi-step processes efficiently.

## Features
- **Execute Plain-English Tasks** via an API
- **Read & Verify File Outputs**
- **Perform Operations & Business Tasks** (Sorting, Formatting, Extraction, API Calls, etc.)
- **Ensure Security & Compliance**
- **Containerized Deployment with Docker**

## API Endpoints

### `POST /run?task=<task description>`
Executes a task based on a **plain-English** description.
- **200 OK** - Task executed successfully
- **400 Bad Request** - Task error
- **500 Internal Server Error** - Agent error

### `GET /read?path=<file path>`
Fetches the content of the specified file for **verification**.
- **200 OK** - Returns file content
- **404 Not Found** - File does not exist

## Phase A: Operations Tasks
- **A1:** Install `uv` (if needed) and run `datagen.py`
- **A2:** Format `/data/format.md` with `prettier@3.4.2`
- **A3:** Count **Wednesdays** in `/data/dates.txt`
- **A4:** Sort contacts in `/data/contacts.json`
- **A5:** Extract the **first line** of the **10 most recent** `.log` files
- **A6:** Generate a **Markdown index** from `/data/docs/`
- **A7:** Extract **sender's email** from `/data/email.txt`
- **A8:** Extract **credit card number** from `/data/credit-card.png`
- **A9:** Find the **most similar comments** using embeddings
- **A10:** Calculate **total sales** for “Gold” tickets in SQLite database

## Phase B: Business Tasks
- **B1:** Prevent access/exfiltration of data outside `/data`
- **B2:** Prevent **data deletion**
- **B3:** Fetch and save data from an **API**
- **B4:** Clone a **Git repository** and commit changes
- **B5:** Execute **SQL queries** on SQLite/DuckDB
- **B6:** Extract **webpage data** (scraping)
- **B7:** Compress or resize images
- **B8:** Transcribe audio from MP3
- **B9:** Convert **Markdown to HTML**
- **B10:** Filter a **CSV file** and return JSON

## Installation & Setup
### 1️⃣ Clone the Repository
```sh
git clone https://github.com/your-username/your-repo.git
cd your-repo
```
### 2️⃣ Install Dependencies
```sh
pip install -r requirements.txt
```
### 3️⃣ Run the API Server
```sh
python app.py
```
### 4️⃣ Test the API
```sh
curl -X POST "http://localhost:8000/run?task=Count Wednesdays in /data/dates.txt"
curl -X GET "http://localhost:8000/read?path=/data/dates-wednesdays.txt"
```

## Deployment with Docker
### Build & Push Docker Image
```sh
docker build -t your-username/llmproject .
docker push your-username/llmproject
```
### Run the Docker Container
```sh
podman run -e AIPROXY_TOKEN=$AIPROXY_TOKEN -p 8000:8000 your-username/llmproject
```

## License
This project is licensed under the **MIT License**.

