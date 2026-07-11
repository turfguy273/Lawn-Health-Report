# Lawn Health Reports

Turning trouble-spot photos into emailed lawn health reports for Advanced Turf Care customers.

## Where things stand

1. **Report design** — approved. See `templates/report-design-mockup.html` (open in a browser to view).
2. **Issue playbook** — first draft written, wording still needs a pass. See `templates/issue-playbook.html`. This is the "what it means" / "what we'll do" text for each common issue (overwatering, underwatering, shade, crepe myrtle bark scale, whitefly, Pythium blight, mowed too short).
3. **Email template** — built as real, email-safe HTML (tables + inline styles, so it renders correctly in Gmail/Outlook/phones, not just a web browser). See `templates/email-template.html`.

## The plan

- Technicians already photograph every job in Service Autopilot and can pick the issue from a custom dropdown field.
- Service Autopilot can't send different email wording based on that dropdown by itself, so a **Zapier automation** will sit in between: it watches for "job completed," reads which issue was picked, grabs the customer's name/address/email and the photo, drops the matching playbook text into the email template, and sends it straight to the customer.
- Not built yet — next step is setting up that Zap.

## Next steps

- [ ] Reword the issue playbook text (owner's pass)
- [ ] Build the Zapier automation (Service Autopilot → pick wording → send email)
- [ ] Test on one real completed job before trusting it fully
