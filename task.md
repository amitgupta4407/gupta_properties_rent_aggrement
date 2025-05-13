# Rent Agreement Generator - Task List

## Template Fields and Validation Requirements

This document outlines all input fields needed for the rent agreement generator, their validation rules, and default values based on the `agreement_template.docx` file.

### Basic Information Fields

| Field | Type | Validation | Default Value | Notes |
|-------|------|------------|--------------|-------|
| landlord_name | Text | Required | Empty | Full legal name of the property owner |
| tenant_name | Text | Required | Empty | Full legal name of the tenant |
| property_address | Text | Required | Empty | Complete address with pin code |
| start_date | Date | Required | Current date | Format: DD-MM-YYYY |
| end_date | Date | Required | Start date + 11 months | Format: DD-MM-YYYY (typical lease period in India) |
| signing_date | Date | Required | Current date | Format: DD-MM-YYYY |
| max_occupants | Number | Min: 1 | 2 | Maximum number of people allowed to live in the property |

### Financial Details Fields

| Field | Type | Validation | Default Value | Notes |
|-------|------|------------|--------------|-------|
| rent_amount | Currency | Min: 0 | ₹45,000 | Monthly rent with ₹ symbol and thousands separator |
| security_deposit | Currency | Min: 0 | 2x rent_amount | Typically 2-3 months' rent in India |
| payment_due_day | Number | Min: 1, Max: 31 | 5 | Day of month when rent is due |
| late_fee | Currency | Min: 0 | ₹500 | Penalty for late payment |
| pets_allowed | Boolean | N/A | No | Whether pets are allowed in the property |
| pet_deposit | Currency | Min: 0 | ₹5,000 | Only required if pets_allowed is Yes |

### Terms & Conditions Fields

| Field | Type | Validation | Default Value | Notes |
|-------|------|------------|--------------|-------|
| utilities_included | Text | Optional | "Water, Electricity" | Comma-separated list of included utilities |
| maintenance_contact | Text | Required | Empty | Name and phone number for maintenance issues |
| notice_period | Number | Min: 0 | 30 | Days of notice required before terminating lease |

## Implementation Requirements

1. **Field Extraction**:
   - Scan the `agreement_template.docx` file for all placeholders in the format `[[field_name]]`
   - Create appropriate input fields for each placeholder found

2. **Input Validation**:
   - Implement validation for each field type (text, date, number, currency, boolean)
   - Ensure required fields cannot be left empty
   - Validate numeric ranges where applicable

3. **User Interface**:
   - Organize fields into logical tabs (Basic Information, Financial Details, Terms & Conditions)
   - Provide clear labels and hints for each field
   - Show helpful tooltips or examples where appropriate

4. **Document Generation**:
   - Replace all placeholders in the template with user-provided values
   - Format currency values with ₹ symbol and thousands separators
   - Format dates in DD-MM-YYYY format
   - Handle both paragraphs and tables in the document

5. **Error Handling**:
   - Provide clear error messages if template file is missing
   - Validate all inputs before generating document
   - Handle exceptions during document generation

## Final Deliverable

The final application should:
1. Run as a Streamlit web application
2. Extract fields from the template document
3. Present a user-friendly form with appropriate validation
4. Generate a completed agreement document
5. Provide a download link for the generated document

The template file `agreement_template.docx` must remain unchanged - the application should only fill in the placeholders without modifying the structure or formatting of the document.