# ACSIS

ACSIS is a multi-institution academic platform that brings student, teacher, and administrator tools together in one system. It supports class and exam workflows, student performance tracking, and institution management.

## What the system does

Depending on the user’s role and institution setup, ACSIS can:

- Give students access to their enrolled classes, exams, results, and performance information.
- Help teachers manage their classes and exams.
- Provide institution administrators with tools for managing users and monitoring academic activity.
- Support multiple institutions, with platform-level tools for managing institutions.
- Allow users to sign in with Google, subject to the configured email-domain policy and account access.

## Sign-in and access

Google sign-in uses the `ALLOWED_EMAIL_DOMAIN` setting in the API environment. Set it to the domain accepted by your institution. Faculty and institution administrators must have accounts with the appropriate institution membership and role.

Access to student, teacher, and administrator areas depends on the user’s account and assigned role. Platform-level access requires a super-admin account.

## Run locally

### Requirements

- Git
- Node.js and npm
- PostgreSQL for database-backed local development

Copy `.env.example` to `.env` in the project root and configure the Google OAuth, session, and database settings:

```env
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_CALLBACK_URL=http://localhost:3001/api/auth/google/callback
ALLOWED_EMAIL_DOMAIN=your-institution.edu
SESSION_SECRET=your_long_random_secret
DATABASE_URL=your_postgresql_connection_string
```

Add the callback URL to the authorized redirect URIs for your Google OAuth client.

Install dependencies and start the API and frontend in separate terminals:
```powershell
npm install
npm install --prefix server
npm run dev:api
npm run dev
```
