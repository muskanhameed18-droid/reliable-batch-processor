# Reliable Batch Processor (n8n)

An n8n workflow that processes a batch of records safely: no duplicates, and clean recovery when an API call fails.

> Practice project built to learn reliable automation patterns. Not client work.

## What it does
- Validates records and removes duplicates
- Skips records already marked "done" in Google Sheets
- Marks each record "pending" before the API call
- Retries failed API calls
- Success: logs it and marks the record "done"
- Failure: record stays "pending", error is logged, alert email is sent
- Final summary of every run

## Demo
Walkthrough video (about 3.5 min): https://www.loom.com/share/8c20e567e61440598987471b93aed2fa

## Setup
1. Import `Reliable-batch-processor.json` into n8n.
2. Create a Google Sheet with tabs: Success log, Error log, Mark processed (record_id, status, updated_at), Invalid record.
3. In all 6 Google Sheets nodes, replace YOUR_GOOGLE_SHEET_ID and YOUR_SHEET_TAB_ID.
4. Connect your Google Sheets and Gmail credentials.
5. In Failure Alert, replace your-email@example.com.
6. In Call API (with Retry), replace the demo URL with your own API.

## Limitations
- The demo API (jsonplaceholder) is only for testing.
- If an API finishes but its response times out, a retry may create a duplicate. Use an idempotency key if your API supports one.
- Crashes are not covered. An Error Trigger workflow is the next upgrade.

## Built by
Muskan Hameed, n8n and AI automation builder. Open to small paid projects.

