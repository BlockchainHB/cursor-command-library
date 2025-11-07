# Tweet Insights

## Task
Open browser, navigate to X (Twitter), read recent tweets from the timeline, summarize them, and provide reply recommendations.

## Variables
- **{x_url}**: `https://x.com/home`
- **{tweet_count}**: Number of tweets to analyze (default: 5-10)

## Workflow

### 1. Open browser and navigate to X
- Use `mcp_cursor-browser-extension_browser_navigate` to go to `https://x.com/home`
- Wait for page to load (3-5 seconds)
- Take snapshot to verify page loaded
- Success: Browser opened at X homepage

### 2. Wait for timeline to load
- Wait for timeline content to appear
- Look for article elements or tweet containers
- May need to wait for "Loading timeline" progressbar to disappear
- Success: Timeline loaded

### 3. Extract recent tweets
- Take accessibility snapshot
- Find tweet/article elements in the timeline:
  - Look for `role="article"` elements
  - Each article represents a tweet
  - Extract text content from each tweet
  - Limit to first `{tweet_count}` tweets (default: 5-10)
- For each tweet, extract:
  - Author/username (if visible)
  - Tweet text content
  - Engagement metrics (likes, retweets, replies - if visible)
  - Timestamp (if visible)
- Success: Tweets extracted

### 4. Analyze and summarize tweets
- Process extracted tweet text
- Create summary including:
  - Main topics/themes discussed
  - Sentiment overview (positive, negative, neutral)
  - Key points or insights
  - Notable trends or patterns
- Format as readable markdown
- Success: Summary created

### 5. Generate reply recommendations
- For each tweet (or top tweets), suggest:
  - Engaging reply options (2-3 per tweet)
  - Tone/style recommendations
  - Key points to address
  - Questions to ask (if appropriate)
- Consider:
  - Tweet sentiment
  - Topic relevance
  - Engagement potential
  - Professional/appropriate tone
- Success: Reply recommendations generated

### 6. Create output report
- Generate markdown report with:
  - **Summary Section**: Overview of recent tweets
  - **Tweet Details**: Individual tweet breakdowns
  - **Reply Recommendations**: Suggested responses
  - **Insights**: Key takeaways and trends
- Save to file or display in chat
- Success: Report generated

### 7. Display results
- Show summary in chat
- Present reply recommendations in organized format
- Optionally save to file: `tweet_insights_{timestamp}.md`
- Success: Results displayed

## Output Format

```markdown
# Tweet Insights Report - {timestamp}

## Summary
- **Tweets Analyzed**: {count}
- **Main Topics**: {topics}
- **Overall Sentiment**: {sentiment}
- **Key Insights**: {insights}

## Recent Tweets

### Tweet 1
**Author**: @{username}
**Content**: {tweet_text}
**Engagement**: {metrics}

**Reply Recommendations**:
1. {recommendation_1}
2. {recommendation_2}
3. {recommendation_3}

### Tweet 2
...

## Trends & Insights
- {insight_1}
- {insight_2}
```

## Error Handling
- If timeline doesn't load: Wait longer, refresh page, or check login status
- If no tweets found: Check if user is logged in, try different timeline view
- If extraction fails: Try alternative selectors or manual review
- If analysis fails: Provide raw tweet data as fallback

## Notes
- Works best when user is logged into X/Twitter
- May need to scroll to load more tweets
- Some tweets may be truncated - note this in analysis
- Engagement metrics may not always be visible in accessibility snapshots
- Consider rate limits and API alternatives for production use

