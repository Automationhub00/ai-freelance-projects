# AI Document Processing with n8n

This project demonstrates an AI-powered invoice processing workflow built with n8n.

## What it does

The workflow accepts an uploaded invoice PDF and automatically:

- extracts text from the PDF
- uses AI to identify structured invoice fields
- validates important fields
- writes successful invoices to Google Sheets
- sends a success email
- sends a manual-review email when required information is missing

## Workflow

Invoice Upload  
→ Extract from PDF  
→ AI Information Extraction  
→ Validation with IF node

### Valid invoice

IF = TRUE  
→ Append row to Google Sheets  
→ Send Success Email

### Missing required information

IF = FALSE  
→ Send Manual Review Email

## Extracted fields

- Vendor Name
- Invoice Number
- Invoice Date
- Due Date
- Customer Name
- Subtotal
- Tax
- Total Amount
- Currency

The AI is instructed not to invent missing values.

## Validation

The workflow checks that these important fields are present:

- Vendor Name
- Invoice Number
- Total Amount

If any of these fields are missing, the invoice is routed to manual review.

## Testing

The workflow was tested with multiple invoice formats and currencies:

- JPY invoice
- USD invoice
- EUR invoice
- invoice with a missing due date
- invoice with a missing invoice number

The missing-invoice-number test correctly triggered the manual-review branch.

During testing, an earlier extraction attempt generated an invoice number that was not present in the document. The extraction instructions were tightened so missing text fields return an empty value instead of being inferred.

## Tools Used

- n8n
- OpenAI
- Google Sheets
- Gmail

## Files

- `Day_3_AI_Document_Processing_n8n.json` — exported n8n workflow
- `workflow-screenshot.png` — final workflow
- `google-sheets-screenshot.png` — processed invoice results
- sample invoice PDF

## Skills Practiced

- AI document processing
- structured data extraction
- workflow automation
- conditional logic
- data validation
- Google Sheets integration
- automated email notifications
- error handling
- workflow testing
