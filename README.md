# mediroza-penetration-testing
Authorized black-box penetration testing assessment completed during Week 4 of the NetworkWalks internship programme.
# Mediroza General Hospital — Penetration Testing

## Week 4 Internship Project

This repository documents an authorized black-box penetration-testing
assessment conducted as part of the NetworkWalks internship programme.

The assessment was performed within the controlled educational
environment specified by the project brief.

## Target

- Target: `medirozahospital.com`
- Assessment Type: Black-box penetration test
- Duration: 3 days
- Project: Mediroza General Hospital
- Batch: B082
- Week: 4

## Objectives

The assessment focused on:

1. Reconnaissance and identification of exposed entry points.
2. Authentication and input-handling analysis.
3. Initial access to the restricted patient-report area.
4. Recovery of three protected PDF laboratory reports.
5. Analysis of recovered file metadata.
6. Identification of an exposed database backup.
7. Documentation of staff salary and shareholder information exposure.
8. Preparation of a professional penetration-testing report.

## Methodology

The assessment followed a progressive approach:

### M1 — Initial Access

- Performed DNS and connectivity reconnaissance.
- Enumerated HTTP/HTTPS services.
- Identified public application entry points.
- Analysed Staff Login and Patient Portal authentication.
- Observed application input-handling behaviour.
- Performed controlled directory enumeration.
- Identified the restricted patient reports area.
- Demonstrated access to the patient portal.

### M2 — Data Extraction

Three password-protected PDF laboratory reports were recovered.

The first two reports were successfully recovered using the
NetworkWalks password-cracking tool.

For the third report, the initial 100-word list did not produce a
match. An alternative larger wordlist was subsequently used and the
third report was successfully recovered.

### M3 — Critical Data Exposure

Recovered PDF metadata was analysed using ExifTool.

A metadata finding in the third PDF provided a lead concerning an
older database backup location.

Analysis of the exposed SQL backup identified:

- Staff salary information
- Staff employment information
- Staff contact information
- Shareholder information
- Share ownership percentages
- Shares held
- Share classes

Sensitive personal information has been excluded from this repository.

### M4 — Reporting

A professional penetration-testing activity report was prepared
covering:

- Executive Summary
- Scope and Methodology
- Findings and Proof of Exploitation
- Risk Ratings
- Recommendations and Remediation
- Challenges and Lessons Learned

## Tools Used

- Kali Linux
- Firefox
- Browser Developer Tools
- Nmap
- curl
- ping
- nslookup
- FFUF
- NetworkWalks Password Cracking Tool
- RockYou wordlist
- ExifTool
- pdfinfo
- qpdf

## Key Findings

| Finding | Risk |
|---|---|
| SQL error disclosure / unsafe query construction | High* |
| Exposed database backup containing sensitive information | Critical |
| Disclosure of sensitive staff and corporate information | Critical |

\*The SQL error was observed as evidence of unsafe query construction;
successful SQL injection was not established solely from the error response.

## Evidence

Screenshots and command-line evidence are stored in the `evidence/`
and `recon/` directories.

Sensitive information has been redacted where necessary.

## Security and Privacy Notice

This repository intentionally does NOT contain:

- Patient laboratory reports
- PDF passwords
- Database dump files
- National identification numbers
- Personal telephone numbers
- Authentication credentials
- Session cookies
- Other confidential information

The original evidence is retained securely in the authorized project
environment.

## Conclusion

The assessment demonstrated the importance of secure authentication,
input validation, access controls, metadata management and backup
security.

A significant exposure was identified through an improperly exposed
database backup. The backup contained confidential staff and
shareholder information, demonstrating the potential impact of
leaving internal backup resources accessible through a web
application.

Recommendations include removing exposed backups, storing backups
outside the web root, implementing appropriate access controls,
using parameterized database queries, suppressing detailed production
errors, and reviewing legacy files after site migrations.
