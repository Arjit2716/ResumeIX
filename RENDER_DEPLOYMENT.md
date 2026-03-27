# Deploying to Render

This guide walks you through deploying the Resume Analyzer on Render.

## Prerequisites

1. **GitHub Account** - Your repository must be on GitHub
2. **Render Account** - Sign up at [render.com](https://render.com)
3. **API Keys** - Have your Groq and Anthropic API keys ready

## Step 1: Connect Your GitHub Repository

1. Go to [render.com](https://render.com)
2. Sign up or log in with your GitHub account
3. Click **"New +"** → **"Web Service"**
4. Connect your GitHub account and select the `Resume-Analyzer` repository
5. Click **"Connect"**

## Step 2: Configure the Web Service

Fill in the following details:

| Field | Value |
|-------|-------|
| **Name** | `resume-analyzer` |
| **Environment** | `Python 3.11` |
| **Build Command** | `pip install -r requirements.txt` |
| **Start Command** | `uvicorn app:app --host 0.0.0.0 --port 8000` |
| **Instance Type** | `Free` (or upgrade as needed) |

## Step 3: Set Environment Variables

Click **"Advanced"** and add these environment variables:

1. **GROQ_API_KEY**
   - Key: `GROQ_API_KEY`
   - Value: Your Groq API key

2. **ANTHROPIC_API_KEY**
   - Key: `ANTHROPIC_API_KEY`
   - Value: Your Anthropic API key

## Step 4: Deploy

1. Click **"Create Web Service"**
2. Render will automatically:
   - Build your project
   - Install dependencies from `requirements.txt`
   - Start the app using the start command
   - Assign you a unique URL

## Step 5: Access Your App

Render will provide you with a URL like:
```
https://resume-analyzer-xxxxx.onrender.com
```

Visit this URL to access your deployed Resume Analyzer!

## Useful Commands

```bash
# View build logs
# (Available in Render dashboard under "Logs")

# View deployment status
# (Available in Render dashboard under "Events")
```

## Cost Information

- **Free Plan**: 0.5 CPU, 512 MB RAM, limited to 750 hours/month
- **Paid Plans**: Start at $7/month with better resources

**Note**: Free tier spins down after 15 minutes of inactivity. Expect a cold start response time of 30+ seconds when restarting.

## Troubleshooting

### Build Fails
- Check that all dependencies are in `requirements.txt`
- Ensure Python version compatibility

### Runtime Errors
- Check logs in the Render dashboard
- Verify API keys are set correctly
- Check that the start command is correct

### Cold Start Issues
- Upgrade to a Paid plan for faster response times
- Consider using background workers for heavy computation

## Auto-Deploy

Render automatically redeploys when you push to your GitHub repository's main branch. To disable this:

1. Go to **Settings** in Render dashboard
2. Disable **"Auto-Deploy"**

## Example Deployment Output

When successful, you should see:
```
INFO:     Started server process [1]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://0.0.0.0:8000
```

Your app is now live! 🚀