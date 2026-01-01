# YouTube Comment Analyzer - Setup Instructions

## Getting Your YouTube API Key

To use this analyzer with real YouTube data, you need to get a free API key from Google:

### Step 1: Create a Google Cloud Project
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Sign in with your Google account
3. Click "Select a project" → "New Project"
4. Give it a name (e.g., "YouTube Comment Analyzer")
5. Click "Create"

### Step 2: Enable YouTube Data API v3
1. In the Google Cloud Console, go to "APIs & Services" → "Library"
2. Search for "YouTube Data API v3"
3. Click on it and press "Enable"

### Step 3: Create API Credentials
1. Go to "APIs & Services" → "Credentials"
2. Click "Create Credentials" → "API Key"
3. Copy the API key that appears
4. (Optional but recommended) Click "Restrict Key" to:
   - Add application restrictions (e.g., HTTP referrers if hosting)
   - Restrict to YouTube Data API v3 only

### Step 4: Add API Key to the Code
1. Open `youtube-analyzer.html` in a text editor
2. Find this line near the top of the `<script>` section:
   ```javascript
   const API_KEY = 'YOUR_YOUTUBE_API_KEY_HERE';
   ```
3. Replace `'YOUR_YOUTUBE_API_KEY_HERE'` with your actual API key:
   ```javascript
   const API_KEY = 'AIzaSyD...your-actual-key-here';
   ```
4. Save the file

### Step 5: Test It Out
1. Open `youtube-analyzer.html` in a web browser
2. Paste any YouTube video URL
3. Click "Analyze"
4. Watch as it fetches real comment data!

## API Quota Information

The YouTube Data API has a free quota of 10,000 units per day.

**Cost per operation:**
- Fetching video details: 1 unit
- Fetching 100 comment threads: 1 unit

**Example:** Analyzing a video with 5,000 comments would use approximately:
- 1 unit for video details
- 50 units for comments (5,000 ÷ 100)
- **Total: ~51 units**

You can analyze roughly **195 videos** per day (10,000 ÷ 51) with average comment counts.

## Features

- ✅ Real YouTube video thumbnail, title, and metadata
- ✅ Fetches all comments and replies
- ✅ Smart data aggregation (daily/weekly/monthly based on video age)
- ✅ Activity chart showing comment patterns over time
- ✅ Separate tracking for comments vs replies
- ✅ YouTube's official red-to-magenta brand colors

## Troubleshooting

**"Please configure your YouTube API key"**
- Make sure you replaced `'YOUR_YOUTUBE_API_KEY_HERE'` with your actual API key

**"Failed to fetch video details"**
- Check that you enabled YouTube Data API v3 in your Google Cloud project
- Verify the API key is correct
- Make sure the video URL is valid

**"This video has no comments or comments are disabled"**
- Some videos have comments disabled by the creator
- Try a different video

**"Error: The request cannot be completed because you have exceeded your quota"**
- You've hit the daily 10,000 unit limit
- Wait until the next day (quota resets at midnight Pacific Time)
- Or request a quota increase in Google Cloud Console

## Privacy & Security

- Your API key is stored locally in the HTML file only
- All API calls are made directly from your browser to YouTube's servers
- No data is sent to any third-party servers
- Consider restricting your API key to specific domains if hosting publicly

## Next Steps

Want to enhance this analyzer? Consider adding:
- Sentiment analysis of comments
- Top commenters list
- Word cloud of common terms
- Export data to CSV
- Multiple video comparison
