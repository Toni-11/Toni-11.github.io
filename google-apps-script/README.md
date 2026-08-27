# OTP email service

The portfolio contact API uses a Google Apps Script Web App as the OTP email provider.

Web App endpoint:
`https://script.google.com/macros/s/AKfycbzlCZ0FQYvp_Cp7N_VWImgy3vLD3agL-M4ywM_sb-YmyPRGeJGt5TJ6X-6O-OUTZAyvhQ/exec`

The shared `authKey` must never be committed to this repository. Store it as a Cloudflare Worker secret named `GOOGLE_OTP_AUTH_KEY`.

Expected POST body:
```json
{
  "to": "user@example.com",
  "otp": "123456",
  "authKey": "<secret>"
}
```

The Apps Script must be deployed as a Web App executing as the owner's account and accessible to anyone so the Worker can call it.
