# Clinical Request Automation with UiPath

A small healthcare automation portfolio project that validates synthetic clinical laboratory requests, separates valid and rejected records, records rejection reasons, and generates traceable CSV outputs.

> This project uses synthetic data only. It does not contain patient data and is not intended for clinical decision-making.

## Why this project

Clinical and laboratory teams often receive structured requests that must be checked before processing. Manual validation is repetitive and can allow incomplete or unsupported requests to continue downstream.

This UiPath workflow demonstrates how robotic process automation can perform an initial rules-based validation and create clear outputs for further review.

## Healthcare automation context

Healthcare organisations commonly handle data and processes such as:

- Patient referrals and registrations
- Appointment and outpatient-clinic requests
- Patient demographic and insurance information
- Clinical findings and relevant comorbidities submitted with referrals
- Patient invoices and insurance billing information
- Requests for discharge reports
- Administrative forms and documents

This portfolio project does not reproduce an existing hospital process. It demonstrates transferable UiPath techniques that could support comparable healthcare workflows.

## What the workflow does

1. Reads clinical requests from `Data/Input/ClinicalRequests.csv`.
2. Checks whether `SampleID` is present.
3. Validates the example test types defined for this synthetic demonstration:
   - WES
   - RNA-Seq
   - Gene Panel
4. Validates the example priorities:
   - Routine
   - Urgent
5. Writes accepted requests to `Data/Processed/ValidRequests.csv`.
6. Writes rejected requests to `Data/Exceptions/RejectedRequests.csv`.
7. Adds a `RejectionReason` for every rejected request.
8. Records processing activity in the UiPath execution log.

The example test types are based on the author's bioinformatics background and are not presented as the service catalogue of any specific hospital.

## Validation results

| Request | Result | Reason |
|---|---|---|
| REQ-1001 | Valid | All required values supported |
| REQ-1002 | Valid | All required values supported |
| REQ-1003 | Rejected | Missing SampleID |
| REQ-1004 | Rejected | Unsupported TestType |
| REQ-1005 | Rejected | Unsupported Priority |

## Project structure

```text
clinical-request-automation-uipath/
├── Main.xaml
├── project.json
├── Data/
│   ├── Input/
│   │   └── ClinicalRequests.csv
│   ├── Processed/
│   │   └── ValidRequests.csv
│   └── Exceptions/
│       └── RejectedRequests.csv
├── Documentation/
│   └── Screenshots/
└── README.md
```

## Technologies

- UiPath Studio Community
- Windows project compatibility
- VB.NET expressions
- CSV and DataTable activities
- Rules-based workflow validation

## How to run

1. Clone or download this repository.
2. Open the project in UiPath Studio.
3. Confirm that `Data/Input/ClinicalRequests.csv` is present.
4. Open `Main.xaml`.
5. Run the workflow.
6. Review the generated files under `Data/Processed` and `Data/Exceptions`.

## Current scope and limitations

- Uses a small synthetic CSV dataset.
- Uses fixed validation rules for demonstration.
- Does not connect to a laboratory information system or hospital information system.
- Does not make medical decisions.
- Production deployment would require security review, access controls, exception handling, testing, monitoring, and compliance with applicable data-protection requirements.

## Possible extensions

- UiPath Orchestrator queues
- Configuration-driven validation rules
- API integration
- Email or Teams notifications
- Audit reports and dashboards
- Document Understanding for unstructured request forms
- Automated tests and exception handling

## Author

**Chukwuma Winner Obiora**  
Bioinformatics specialist developing practical automation solutions for healthcare and laboratory workflows.
