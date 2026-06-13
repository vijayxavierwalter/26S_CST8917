# Azure Text Analyzer Function

## Overview

This project is an Azure Functions Python application that analyzes text and stores the analysis results in Azure Cosmos DB for later retrieval.

The application provides two HTTP-triggered Azure Functions:

1. **TextAnalyzer** – Analyzes submitted text and stores the results in Cosmos DB.
2. **GetAnalysisHistory** – Retrieves previously stored analysis results from Cosmos DB.

---

## Features

### TextAnalyzer

Analyzes input text and returns:

* Word Count
* Character Count
* Character Count (without spaces)
* Sentence Count
* Paragraph Count
* Average Word Length
* Longest Word
* Estimated Reading Time

Each analysis result is stored in Azure Cosmos DB with a unique identifier.

### GetAnalysisHistory

Retrieves previously stored analysis records from Cosmos DB.

Supports an optional limit parameter:

```text
/api/GetAnalysisHistory?limit=5
```

---

## Technologies Used

* Azure Functions (Python)
* Azure Cosmos DB for NoSQL
* Azure Functions Core Tools
* Python 3.12

---

## Project Files

```text
function_app.py          Main Azure Functions code
requirements.txt         Python dependencies
DATABASE_CHOICE.md       Database selection justification
DEMO.md                  YouTube demonstration video link
README.md                Project documentation
```

---

## Local Setup

### Prerequisites

* Python 3.12+
* Azure Functions Core Tools
* Azure CLI
* Azurite (for local storage emulation)

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Configure Environment Variables

Create a local.settings.json file:

```json
{
  "IsEncrypted": false,
  "Values": {
    "FUNCTIONS_WORKER_RUNTIME": "python",
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "DATABASE_CONNECTION_STRING": "YOUR_COSMOS_DB_CONNECTION_STRING"
  }
}
```

### Run Locally

```bash
func start
```

---

## API Endpoints

### TextAnalyzer

GET Request:

```text
http://localhost:7071/api/TextAnalyzer?text=Hello World
```

Sample Response:

```json
{
  "id": "unique-record-id",
  "analysis": {
    "wordCount": 2,
    "characterCount": 11
  }
}
```

---

### GetAnalysisHistory

GET Request:

```text
http://localhost:7071/api/GetAnalysisHistory
```

Or:

```text
http://localhost:7071/api/GetAnalysisHistory?limit=5
```

---

## Azure Cosmos DB Configuration

Database Name:

```text
TextAnalyzerDB
```

Container Name:

```text
AnalysisResults
```

Partition Key:

```text
/ id
```

---

## Azure Deployment

Deploy the Function App using:

```bash
func azure functionapp publish vijay-textanalyzer-func
```

Azure Function App:

```text
vijay-textanalyzer-func
```

---

## Author

Vijay Xavier Walter

Algonquin College

CST8917 – Serverless Computing
