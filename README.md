
# Ai Automatic Payslip Workflow

An automated payslip generation workflow built with **n8n**.  
This project reads employee payroll data from **Google Sheets**, generates a branded **HTML payslip**, converts it into **PDF**, sends it to employees through **Gmail**, and updates the processing status in the sheet.

## Features

- Monthly automated payslip generation
- Reads employee salary data from Google Sheets
- Processes only rows marked as `Pending`
- Normalizes payroll fields from multiple column-name formats
- Calculates:
  - Total earnings
  - Total deductions
  - Net salary
  - Net salary in words
- Generates styled HTML payslips
- Converts HTML to PDF using Gotenberg
- Renames PDF files automatically using employee ID and month
- Emails payslips to employees via Gmail
- Marks processed rows as `Sent`

## Workflow Overview

1. **Schedule Trigger**
   - Starts the workflow on a monthly schedule.

2. **Fetch Employee Data**
   - Reads employee records from Google Sheets.
   - Filters only rows where `Status = Pending`.

3. **Loop Through Employees**
   - Processes employees one by one.

4. **Prepare Payload**
   - Maps and cleans employee/payroll data
   - Supports alternate input column names
   - Formats numeric values
   - Converts net salary into words

5. **Build HTML**
   - Creates a branded salary slip template in HTML

6. **Convert HTML to File**
   - Converts HTML content into a file

7. **Generate PDF**
   - Uses Gotenberg to convert the HTML file into a PDF payslip

8. **Rename PDF**
   - Sets the PDF filename using:
     - Employee ID
     - Salary month

9. **Send Salary Slip**
   - Sends the PDF attachment to the employee through Gmail

10. **Update Row in Sheet**
   - Updates the employee row status from `Pending` to `Sent`

11. **Completion**
   - Returns a success message after all emails are sent

## Tech Stack

- **n8n**
- **Google Sheets**
- **Gmail**
- **HTML/CSS**
- **Gotenberg** for PDF generation

## Expected Input Data

The Google Sheet should contain payroll-related columns such as:

- `employee_name`
- `employee_email`
- `employee_id`
- `salary_month`
- `Basic Salary`
- `HRA`
- `Arrear`
- `PF`
- `ESI`
- `Advance`
- `Voluntary PF`
- `Professional Tax`
- `Total Deduction`
- `Net Salary`
- `Status`

Additional employee fields may include:

- Department
- Designation
- DOJ
- UAN
- PAN
- Aadhar
- Bank Name
- Account Number
- Attendance / leave values

## Output

For each employee, the workflow generates:

- A formatted PDF payslip
- An email with the payslip attached
- A status update in the spreadsheet

## Use Case

This project is useful for:

- HR automation
- Monthly payroll operations
- Small and medium business salary slip distribution
- Reducing manual payslip creation and emailing work

## Security Note

Before publishing this workflow publicly:

- Remove or replace sheet IDs
- Remove credential references
- Hide internal company details where needed
- Do not upload employee salary data
- Do not upload personal information or real payroll sheets

## Future Improvements

- Add error handling and retry flow
- Add audit logs
- Store generated PDFs in Google Drive
- Add support for multiple companies/branches
- Add admin notification after payroll completion

## License

This project is for internal payroll automation and can be adapted for business use.

<img width="1917" height="851" alt="image" src="https://github.com/user-attachments/assets/ee10a78d-992a-4323-9cbe-d5629f8654f2" />


![WhatsApp Image 2026-04-11 at 12 06 38 PM](https://github.com/user-attachments/assets/ecc8aefc-5b7d-4102-af71-4db6f2546df8)
