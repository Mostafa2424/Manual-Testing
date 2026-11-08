# OrangeHRM MyInfo: Manual Test Scenarios and Test Cases

Manual functional test documentation for the **MyInfo** module of OrangeHRM, written from the point of view of an **Employee Self-Service (ESS) user**.

The project takes the module from requirement to executed test: scenarios, detailed test cases, expected and actual results, and pass/fail status for every case.

## At a glance

|                            |                                                                         |
| -------------------------- | ----------------------------------------------------------------------- |
| **Application under test** | OrangeHRM open-source demo, <https://opensource-demo.orangehrmlive.com> |
| **Module**                 | MyInfo (ESS user)                                                       |
| **Test type**              | Manual, black-box functional testing                                    |
| **Requirements covered**   | 11 (3.1.1 to 3.1.11)                                                    |
| **Test scenarios**         | 42                                                                      |
| **Test cases**             | 59                                                                      |
| **Executed**               | 59                                                                      |
| **Passed / Failed**        | 59 / 0                                                                  |

## Repository contents

```
.
├── README.md
└── test_scenarios.xlsx
    ├── test scenarios   (42 scenarios mapped to requirement IDs)
    └── Test Cases       (59 detailed test cases with execution results)
```

### Sheet: `test scenarios`

| Column   | Description                                        |
| -------- | -------------------------------------------------- |
| SNO      | Scenario number                                    |
| Req#ID   | Requirement the scenario belongs to (e.g. `3.1.4`) |
| Scenario | High-level condition to be verified                |

### Sheet: `Test Cases`

| Column             | Description                             |
| ------------------ | --------------------------------------- |
| TC#ID              | Unique ID in the format `TC_MyInfo_###` |
| Project/ModuleName | `Orange HRM-MyInfo`                     |
| Req#ID             | Requirement covered (traceability link) |
| Scenario           | Parent scenario                         |
| Test Case Title    | What the test verifies                  |
| Steps              | Numbered steps to reproduce             |
| Test Data          | Inputs used (sample values)             |
| Expected Result    | Behaviour required by the requirement   |
| Actual Result      | What was observed during execution      |
| Status             | Pass / Fail                             |

## Coverage and results (traceability)

| Req#ID    | Feature area                                                                | Scenarios | Test cases | Test case IDs              |      Result      |
| --------- | --------------------------------------------------------------------------- | :-------: | :--------: | -------------------------- | :--------------: |
| 3.1.1     | Login, personal details: view, edit, restricted fields                      |     4     |     8      | TC_MyInfo_001–004, 006–009 |    8 / 8 Pass    |
| 3.1.2     | Profile photograph                                                          |     1     |     3      | TC_MyInfo_005, 010–011     |    3 / 3 Pass    |
| 3.1.3     | Contact details                                                             |     2     |     3      | TC_MyInfo_012–014          |    3 / 3 Pass    |
| 3.1.4     | Emergency contacts                                                          |     3     |     4      | TC_MyInfo_015–018          |    4 / 4 Pass    |
| 3.1.5     | Dependants                                                                  |     3     |     4      | TC_MyInfo_019–022          |    4 / 4 Pass    |
| 3.1.6     | Immigration information and attachments                                     |     4     |     5      | TC_MyInfo_023–027          |    5 / 5 Pass    |
| 3.1.7     | Job details (view only)                                                     |     1     |     1      | TC_MyInfo_028              |    1 / 1 Pass    |
| 3.1.8     | Salary details (view only)                                                  |     1     |     1      | TC_MyInfo_029              |    1 / 1 Pass    |
| 3.1.9     | Supervisors list (view only)                                                |     1     |     1      | TC_MyInfo_030              |    1 / 1 Pass    |
| 3.1.10    | Qualifications: work, education, skills, languages, certificates, documents |    18     |     24     | TC_MyInfo_031–054          |   24 / 24 Pass   |
| 3.1.11    | Memberships and attachments                                                 |     4     |     5      | TC_MyInfo_055–059          |    5 / 5 Pass    |
| **Total** |                                                                             |  **42**   |   **59**   |                            | **59 / 59 Pass** |

## Test design approach

Every scenario has at least one test case, and most data entry features are tested from more than one angle.

| Type                  | Count | Examples                                                                                                                                     |
| --------------------- | :---: | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Positive (valid flow) |  38   | Add, edit, add multiple, delete, attach a document                                                                                           |
| Negative / validation |  17   | Invalid login, blank mandatory fields, invalid email, unsupported or oversized file, end date before start date, duplicate skill or language |
| Access restriction    |   4   | ESS user cannot edit restricted fields, job details or salary details, and can only view supervisors                                         |

Techniques used:

- **Equivalence partitioning**: valid and invalid credentials, valid and invalid data formats.
- **Boundary and rule checks**: date ranges, file type and file size limits, mandatory fields.
- **Role-based access checks**: confirming what an ESS user must not be able to change.
- **CRUD coverage**: add, add multiple and delete for each repeating section (emergency contacts, dependants, immigration, qualifications, memberships).

## How to use

1. Download `test_scenarios.xlsx` and open it in Excel, LibreOffice or Google Sheets.
2. Start with **test scenarios** for the overall scope.
3. Open **Test Cases** and use the filters to find cases by requirement, scenario or status.
4. To re-run a test, follow the **Steps** column with the **Test Data** shown and compare the result with **Expected Result**.

## What this project demonstrates

- Turning requirements into scenarios and then into detailed, repeatable test cases
- Positive, negative and access-control test design
- Recording expected and actual results and tracking execution status
