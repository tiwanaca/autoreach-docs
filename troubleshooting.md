# Troubleshooting

A centralized guide for diagnosing and fixing common issues in AutoReach. Each section follows a **Symptom / Likely Cause / Fix** pattern.

---

## Account Connection Issues

### X Account: "Cookies Invalid"

**Symptom:** Your X account shows as disconnected or you see a "cookies invalid" error.

**Likely Cause:** Your X session has expired. Session cookies typically last 2-4 weeks before they need to be refreshed.

**Fix:** Open the Chrome Extension, click the **three dots** next to the affected account, and click **Reconnect**. Make sure you are logged into X in your browser before reconnecting.

---

### X Account: "Proxy Connection Failed"

**Symptom:** Actions fail with a proxy-related error.

**Likely Cause:** Your proxy has gone offline or its credentials have changed.

**Fix:** Your proxy was provisioned automatically during onboarding. If you see persistent proxy errors, contact support at hello@autoreach.tech.

---

### LinkedIn Account: Session Expired

**Symptom:** LinkedIn actions fail or the account shows as inactive.

**Likely Cause:** Your LinkedIn session cookies have expired. This happens periodically, especially if LinkedIn detects unusual activity.

**Fix:** Open the Chrome Extension on linkedin.com, click the **three dots** next to the account, and click **Reconnect**. You must be logged into LinkedIn in your browser.

---

### LinkedIn Account: Emergency Pause

**Symptom:** All LinkedIn activity has stopped and the account shows as paused.

**Likely Cause:** AutoReach detected an automation warning from LinkedIn (rate limit, bot detection, or IP block) and paused the account to protect it.

**Fix:** Wait for the cooldown period to expire:
- Rate limit: 24 hours
- Bot detection: 7 days
- IP block: 24 hours

Do not attempt to bypass the pause. AutoReach will automatically resume activity once the cooldown expires.

---

### Chrome Extension: "License Key Invalid"

**Symptom:** The extension rejects your license key.

**Likely Cause:** The key has expired or was entered incorrectly.

**Fix:**
1. Go to your AutoReach settings and copy your current license key
2. Paste it into the extension
3. Click **Activate**

---

### Chrome Extension: "Extension Can't Access This Page"

**Symptom:** The extension shows this message when you click it.

**Likely Cause:** You are on a page other than linkedin.com or x.com.

**Fix:** Navigate to linkedin.com or x.com first, then click the extension icon.

---

## Sequence Not Sending Actions

### Sequence is active but nothing is happening

**Symptom:** You started a sequence but no actions are being executed.

**Likely Cause (1):** No leads are enrolled. A sequence needs at least one lead to run.

**Fix:** Open the sequence, go to the Leads tab, and add leads from your pipeline.

**Likely Cause (2):** Your activity window is closed. Actions only execute during your configured activity hours.

**Fix:** Check your activity window in Settings. If it is set to business hours and it is currently outside those hours, actions will resume when the window opens.

**Likely Cause (3):** Your daily action limit has been reached for today.

**Fix:** Wait until tomorrow, or increase your daily action limits in the sequence settings (keeping in mind platform safety guidelines).

**Likely Cause (4):** The connected account is paused or has errors.

**Fix:** Check Analytics > Account Status. If the account shows errors or a paused state, resolve the underlying issue (see Account Connection Issues above).

---

### Actions are stuck in "pending" status

**Symptom:** Actions appear in the timeline but never execute.

**Likely Cause:** The actions are scheduled for a future time based on the delays configured in your flow.

**Fix:** Check the scheduled time on each pending action. If the timing looks correct, just wait. If you want to change the timing, use the **Reschedule** option in the sequence menu to recalculate all pending action times based on current settings.

---

### Specific action type keeps failing

**Symptom:** DMs, likes, or follows repeatedly fail with errors.

**Likely Cause:** The platform is rate-limiting that specific action type, or the lead's account has restrictions (e.g., DMs are closed, account is private).

**Fix:**
1. Check the error message on the failed action
2. If rate-limited, reduce your daily limits for that action type
3. If the lead's account has restrictions, the action may not be possible -- consider removing that lead or skipping the step
4. Retry the failed action using the retry button

---

## Leads Not Getting Scored

### Leads stuck without a buyer score

**Symptom:** Leads appear in your pipeline but have no score (showing as "unscored" or no buyer state).

**Likely Cause (1):** Enrichment has not completed yet. Scoring requires profile data, which is gathered during enrichment.

**Fix:** Check if enrichment is still in progress. New leads go through enrichment before scoring, which can take a few minutes per lead.

**Likely Cause (2):** Your AI API keys have run out of credits.

**Fix:** Check Analytics > AI Health. If you see a quota warning, add credits to your OpenAI and/or Anthropic accounts.

**Likely Cause (3):** Your offer is missing key ICP information.

**Fix:** Open your offer and make sure you have filled in target audience, pain points, and qualifying criteria. Scoring quality depends on a well-defined ICP.

---

## AI Messages Not Generating

### DMs or replies show as failed with AI errors

**Symptom:** Message generation fails, and the action is marked as failed.

**Likely Cause (1):** Your AI provider's API key is invalid or out of credits.

**Fix:** Check Analytics > AI Health for provider errors. Verify your API keys are correct in Settings > API Keys and that you have available credits.

**Likely Cause (2):** Both your primary and fallback AI models are down.

**Fix:** This is rare but can happen during provider outages. AutoReach will show a health warning. Wait for the provider to recover, or switch your model configuration in Settings > AI Models.

---

### AI messages sound generic

**Symptom:** Messages are technically correct but lack personality or feel templated.

**Likely Cause:** The AI does not have enough context about your voice and style.

**Fix:**
1. Add **tone examples** to your sequence (real messages you have sent that represent your style)
2. Customize the **AI prompt** and **DM generation prompt** in sequence settings with specific tone instructions
3. Use the **Simulation** tool to preview and iterate on message quality

---

## Low Reply Rates

### Reply rate below 3% after 100+ DMs

**Symptom:** You have sent a meaningful volume of messages but very few people are responding.

**Likely Cause (1):** Weak targeting. Your leads may not be a good fit for your offer.

**Fix:** Review your lead scores. If most scored leads are below 50, tighten your ICP in your offer settings. Consider using more targeted search methods (intent-based keyword search instead of broad people search).

**Likely Cause (2):** Messages are not compelling or personalized enough.

**Fix:** Use Simulation to preview your DMs for several different leads. Refine your message template and AI prompt until messages feel natural and relevant.

**Likely Cause (3):** No warmup before the DM.

**Fix:** Add engagement steps before the DM in your sequence flow (like a post, follow the account, view their profile). People respond better to names they recognize.

**Likely Cause (4):** Wrong platform or timing.

**Fix:** Try switching to the other platform (X vs. LinkedIn). Also review your activity window to ensure messages arrive during business hours in the lead's time zone.

---

## Account Health Warnings

### "Rate Limited" status

**Symptom:** Account shows as rate limited, and some actions are paused.

**Likely Cause:** You hit the platform's daily or hourly limit for a specific action type.

**Fix:** Wait 24 hours for the cooldown to expire. Then reduce your daily action limits to stay under the platform's thresholds. Start conservative (15-20 DMs/day for X, stay well under LinkedIn's weekly connection limit).

---

### "Bot Detected" status

**Symptom:** Account shows bot detection warning, and all activity is paused.

**Likely Cause:** The platform flagged a pattern of activity that looks automated (too many actions in rapid succession, unusual hours, or suspicious IP).

**Fix:**
1. Wait the full 7-day cooldown -- do not try to bypass it
2. After the cooldown, reduce your daily limits significantly
3. Make sure your activity window matches realistic usage patterns
4. Verify your proxy is working (residential IPs are safest)

> **Warning:** Repeated bot detection warnings can lead to permanent account suspension. Take them seriously and reduce your activity levels.

---

### "Auth Error" on LinkedIn

**Symptom:** LinkedIn account shows authentication error.

**Likely Cause:** Your session cookies have been revoked, often because LinkedIn detected a mismatch between your login location and the proxy location.

**Fix:** Reconnect your LinkedIn account via the Chrome Extension. If this happens repeatedly, contact support -- your proxy configuration may need adjustment.

---

## Chrome Extension Issues

### Extension not detecting the current page

**Symptom:** The extension popup is blank or shows "not connected" even though you are on linkedin.com or x.com.

**Likely Cause:** The extension does not have permission to access the current tab, or the page has not fully loaded.

**Fix:**
1. Make sure the page has fully loaded before clicking the extension
2. Try refreshing the page
3. Check Chrome's extension settings to ensure AutoReach has permission to access linkedin.com and x.com
4. If the issue persists, remove and reinstall the extension

---

### "Connection Not Detected" for LinkedIn

**Symptom:** A LinkedIn connection was accepted but AutoReach does not detect it.

**Likely Cause:** The extension was not running or the LinkedIn tab was closed when the acceptance happened.

**Fix:** Use the **Check Acceptances** button in the CRM to manually trigger a detection check.

---

## Enrichment Failures

### Leads stuck in "enriching" state

**Symptom:** Leads have been in the enrichment stage for a long time without progressing to scored.

**Likely Cause (1):** The enrichment queue is backed up. If you added many leads at once, they are processed sequentially.

**Fix:** Wait for the queue to clear. Enrichment processes leads in order, and large batches may take time.

**Likely Cause (2):** The platform is rate-limiting profile data requests.

**Fix:** This usually resolves on its own as AutoReach respects rate limits and retries. If leads are stuck for more than an hour, try the recovery option in the lead's menu.

**Likely Cause (3):** The lead's profile is private or has been deleted.

**Fix:** Private or deleted profiles cannot be enriched. These leads will be marked accordingly and can be removed from your pipeline.

---

### Cross-platform match not found

**Symptom:** A LinkedIn lead does not get matched to an X profile (or vice versa).

**Likely Cause:** The lead does not have a public presence on the other platform, or their usernames are too different for automated matching.

**Fix:** This is expected behavior. Not everyone has accounts on both platforms. You can manually add a profile URL for the other platform if you know it.

---

## Getting More Help

If your issue is not covered here:

1. Check the specific feature's documentation page -- most have their own troubleshooting section
2. Email support at **hello@autoreach.tech** with a description of the issue and any error messages you see
