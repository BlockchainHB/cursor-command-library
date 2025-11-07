# Post Tweet

## Task
Open browser, navigate to X (Twitter), and post a tweet with user-provided content.

## Variables
- **{tweet_content}**: User-provided tweet text (prompted during execution)

## Workflow

### 1. Get tweet content if not provided
- Prompt user: "What would you like to tweet?"
- Store response as `{tweet_content}`
- Validate: Check length (X limit is 280 characters for text, 25,000 for premium)
- Success: Tweet content received

### 2. Open browser and navigate to X
- Use `mcp_cursor-browser-extension_browser_navigate` to go to `{x_url}`
- Wait for page to load
- Take snapshot to verify page loaded
- Success: Browser opened at X homepage

### 3. Locate compose box
- Take accessibility snapshot of the page
- Find the compose/tweet input element:
  - **Primary method**: Look for element with `data-testid="tweetTextarea_0"` 
  - **Fallback**: Find element with `role="textbox"` and `aria-label="Post text"`
  - **Alternative**: Look for `div[contenteditable="true"]` with class containing "DraftEditor-content"
  - **Note**: X uses a contenteditable div, not a textarea - accessibility snapshots may not capture it properly
  - If not found in snapshot, try clicking in dialog area and using Tab to navigate to textbox
- Success: Compose box located

### 4. Enter tweet content
- Click on compose box to focus (may need multiple attempts)
- **Important**: The textbox is a contenteditable div - ensure focus is achieved
- Use `mcp_cursor-browser-extension_browser_type` to enter `{tweet_content}`
- If typing fails, try:
  - Press Tab key to navigate to textbox first
  - Use `slowly: true` parameter for typing
  - Click directly on the element before typing
- Wait a moment for text to appear
- **Note**: Accessibility snapshots may not show typed text - verify by attempting to post
- Success: Tweet content entered

### 5. Post the tweet
- Find the "Post" or "Tweet" button:
  - Look for button with text "Post" or "Tweet"
  - Common selector: `[data-testid="tweetButton"]` or button containing "Post"
- Click the Post/Tweet button
- Wait for confirmation (tweet appears in timeline or success message)
- Success: Tweet posted

### 6. Verify and close
- Take final snapshot to confirm tweet was posted
- Optionally wait a few seconds to see tweet in timeline
- Keep browser open for user to verify
- Success: Tweet posted successfully

## Error Handling
- If login required: Inform user they need to log in first
- If compose box not found: Try alternative selectors or check if user is logged in
- If character limit exceeded: Warn user before posting
- If posting fails: Show error message and retry option


