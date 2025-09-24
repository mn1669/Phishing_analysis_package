# Phishing Email Analysis — Task 
Author: <M.Soma Niranjan>
Date: 2025-09-19

This repo contains an analysis of the email: "You’re Shortlisted – Cyber Security Internship First Selection Round 🚀" (source `.eml` included).

## Files
- sample-email.eml           -- original email file (raw .eml).
- analysis_report.md         -- the analysis report (this file).
- evidence/                  -- screenshots, raw headers, WHOIS outputs, VirusTotal screenshots (if used).

## How I analysed
1. Viewed raw headers (opened the `.eml` source).  
2. Reviewed `Authentication-Results` for DKIM/SPF/DMARC.  
3. Inspected the `Received` chain to identify originating host and IP.  
4. Hovered/expanded tracked links to reveal redirect targets (do not click before verifying).  
5. Recommended independent verification via the organisation's official website or contact details.

## Quick notes
- Authentication checks in this email passed (dkim/spf/dmarc), indicating the email was sent through the domain's configured mailing provider.
- Still recommended: do not enter credentials on any page opened from tracking links until you confirm the landing host is trustworthy.


