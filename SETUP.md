# COR Landing Page - Setup Instructions

## Serverless Form Submission Setup

This project uses Vercel serverless functions with Resend for email delivery.

### 1. Get Your Resend API Key

1. Go to [https://resend.com](https://resend.com) and sign up for a free account
2. Navigate to **API Keys** in your dashboard
3. Click **Create API Key**
4. Copy the API key (it starts with `re_`)

### 2. Configure Environment Variables

#### For Local Development:
Create a `.env` file in the project root:
```bash
cp .env.example .env
```

Then edit `.env` and add your API key:
```
RESEND_API_KEY=re_your_actual_api_key_here
TO_EMAIL=tkrmanisha4s@gmail.com
```

#### For Vercel Production:
1. Go to your Vercel project dashboard
2. Navigate to **Settings** → **Environment Variables**
3. Add the following variables:
   - `RESEND_API_KEY`: Your Resend API key
   - `TO_EMAIL`: `tkrmanisha4s@gmail.com`

### 3. Install Dependencies

```bash
npm install
```

### 4. Test Locally

```bash
# Install Vercel CLI globally (if not already installed)
npm install -g vercel

# Run local development server
vercel dev
```

Visit `http://localhost:3000` and test the contact form.

### 5. Deploy to Vercel

```bash
vercel --prod
```

## Important Notes

- **Email Sender**: By default, Resend uses `onboarding@resend.dev` as the sender. For production, you should:
  1. Verify your own domain in Resend
  2. Update the `from` field in `api/submit.js` to use your domain
  
- **Free Tier Limits**: Resend free tier includes 100 emails/day and 3,000 emails/month

- **Testing**: Always test the form submission in both local and production environments

## Troubleshooting

- **405 Error**: Make sure the API endpoint is accessible at `/api/submit`
- **500 Error**: Check that your `RESEND_API_KEY` environment variable is set correctly
- **Email not received**: Check your spam folder and verify the `TO_EMAIL` address
