# Pikkah Investor Room

Prototype and Engineering reference for:

https://www.pikkah.com/investor

## Investor flow

1. Founder sends the one pager personally
2. Interested prospect receives the investor room link and access code
3. Prospect reviews the deck and books a founder call
4. Qualified investors receive the eligibility questionnaire and SAFE separately

There is intentionally no Invest Now button and no SAFE signing link on this page.

## Prototype access

Access code:

PIKKAH2026

Use any valid name and email and check the confidentiality box.

This access code is only for the prototype and should not be used as production security.

## Production requirements

Engineering should replace the frontend access logic with server controlled authentication.

The production version should:

1. Protect the investor page behind a server session
2. Protect direct deck and PDF routes
3. Keep the route out of public navigation
4. Keep it out of the sitemap
5. Add noindex and nofollow controls
6. Rate limit failed access attempts
7. Store the access code outside the frontend
8. Allow the access code to be rotated without deployment
9. Record investor access, deck views, PDF downloads, and founder contact clicks
10. Connect the founders Google Calendar booking link

Recommended routes:

```text
GET /investor
GET /investor/deck/slide/:number
GET /investor/deck/download
POST /api/investor-room/access
POST /api/investor-room/events
POST /api/investor-room/logout
