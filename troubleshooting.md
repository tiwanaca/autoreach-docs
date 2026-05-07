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

**Symptom:** LinkedIn actions fail or the account shows as inactive. You may receive a "LinkedIn cookie expiry" email.

**Likely Cause:** LinkedIn issued a new session token (`li_at`) for your account, which invalidates the cookies stored in AutoReach. The most common triggers are:

1. **Signing in to the same LinkedIn account from another browser, phone, or device.** LinkedIn rotates session tokens whenever it sees a new device, especially if the IP differs from the proxy AutoReach uses.
2. **Changing your LinkedIn password** or accepting a security prompt.
3. **Choosing "Sign out of all sessions"** in LinkedIn settings.
4. LinkedIn detecting unusual activity and forcing a session refresh.

**Fix:**
1. Open the Chrome Extension on linkedin.com, click the **three dots** next to the account, and click **Reconnect**. You must be logged into LinkedIn in the same browser.
2. To prevent this from repeating, see [LinkedIn Account: Repeatedly Disconnects](#linkedin-account-repeatedly-disconnects) below.

---

### LinkedIn Account: Repeatedly Disconnects

**Symptom:** Your LinkedIn account expires and needs reconnection multiple times per week, even though you reconnect promptly each time.

**Likely Cause:** You are logging in to the same LinkedIn account from multiple browsers or devices (for example, your work laptop, a personal browser, the LinkedIn mobile app, or a second computer). Each new sign-in causes LinkedIn to rotate the `li_at` cookie, which invalidates the one AutoReach is using.

**Fix:** Pick one access path and stick to it.

1. Open LinkedIn in your browser and go to **Settings & Privacy > Sign In & Security > Where you're signed in**.
2. Review the list of active sessions. Each entry shows a device, location, and last activity time.
3. Sign out of any sessions you do not actively use (old browsers, phones you no longer carry, shared computers). Click the three dots next to the session and select **End**.
4. Going forward, sign in to this LinkedIn account from a single browser only. If you need to use the LinkedIn mobile app, sign in there once and avoid switching devices frequently.
5. Reconnect the account in AutoReach via the Chrome Extension.

> **Note:** AutoReach's proxy IP will not appear in "Where you're signed in" because AutoReach reuses your existing session cookie via API calls rather than performing a full login. Not seeing the proxy listed is normal and not a sign of a problem. See the next entry for details.

---

### LinkedIn Settings: AutoReach's Proxy Is Not Listed Under "Where You're Signed In"

**Symptom:** You check **Settings & Privacy > Sign In & Security > Where you're signed in** in LinkedIn and you do not see AutoReach's proxy IP or location in the list of active sessions.

**Likely Cause:** This is expected behavior, not a misconfiguration.

LinkedIn's "Where you're signed in" page only shows sessions that completed a full login flow (username, password, browser fingerprint). AutoReach connects to LinkedIn by reusing the session cookie that your own browser created when you first connected the account through the Chrome Extension. Because no new login flow happens, no new session entry appears.

**Fix:** No action needed. Your account is connected correctly as long as the Accounts page in AutoReach shows the account as **active**.

---

### LinkedIn Account: Emergency Pause

**Symptom:** All LinkedIn activity has stopped and the account shows as paused.

**Likely Cause:** AutoReach detected an issue with the account (rate limit, bot detection, IP block, captcha, or session expired) and paused all associated automation - sequences, warmup, and pending actions are all halted.

**Fix:** What to do depends on the error type shown on the Accounts page:
- **Auto-recoverable** (rate limit, timeout, proxy error, IP block, expired auth): cooldowns range from 2h to 7 days. Activity resumes automatically once the cooldown expires - do not attempt to bypass the pause.
- **Manual fix required** (bot detection, captcha, AI provider out of credits): you will receive an email and must address the underlying issue, then manually resume the account from the Accounts page. Bot detection in particular is serious - treat repeat occurrences as a sign to reduce activity significantly.

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

**Fix:** Check the **Accounts** page. If the account shows errors or a paused state, resolve the underlying issue (see Account Connection Issues above).

---

### Actions are stuck in "pending" status

**Symptom:** Actions appear in the timeline but never execute.

**Likely Cause:** The actions are scheduled for a future time based on the delays configured in your flow.

**Fix:** Check the scheduled time on each pending action in the lead timeline. If the timing looks correct, just wait-  actions execute at their scheduled time within your activity window. If the delays are wrong, pause the sequence, adjust step delays in the flow editor, then resume.

---

### Specific action type keeps failing

**Symptom:** DMs, likes, or follows repeatedly fail with errors.

**Likely Cause:** The platform is rate-limiting that specific action type, or the lead's account has restrictions (e.g., DMs are closed, account is private).

**Fix:**
1. Check the error message on the failed action
2. If rate-limited, reduce your daily limits for that action type
3. If the lead's account has restrictions, the action may not be possible - consider removing that lead or skipping the step
4. Retry the failed action using the retry button

---

## Leads Not Getting Scored

### Leads stuck without a buyer score

**Symptom:** Leads appear in your pipeline but have no score (showing as "unscored" or no buyer state).

**Likely Cause (1):** Enrichment has not completed yet. Scoring requires profile data, which is gathered during enrichment.

**Fix:** Check if enrichment is still in progress. New leads go through enrichment before scoring, which can take a few minutes per lead.

**Likely Cause (2):** Your AI API keys have run out of credits.

**Fix:** Check the health warnings on the Dashboard. If you see a quota warning, add credits to your OpenAI and/or Anthropic accounts.

**Likely Cause (3):** Your offer is missing key ICP information.

**Fix:** Open your offer and make sure you have filled in target audience, pain points, and qualifying criteria. Scoring quality depends on a well-defined ICP.

---

## AI Messages Not Generating

### DMs or replies show as failed with AI errors

**Symptom:** Message generation fails, and the action is marked as failed.

**Likely Cause (1):** Your AI provider's API key is invalid or out of credits.

**Fix:** Check the health warnings on the Dashboard for provider errors. Verify your API keys are correct in **Settings > AI & Models** and that you have available credits.

**Likely Cause (2):** Both your primary and fallback AI models are down.

**Fix:** This is rare but can happen during provider outages. AutoReach will show a health warning. Wait for the provider to recover, or switch your model configuration in **Settings > AI & Models**.

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

**Fix:**
1. Open your sequence and check the score distribution of enrolled leads. If most are below 50, your offer's ICP is too broad or doesn't match the leads your searches are surfacing.
2. The fastest way to fix this: open a lead that scored wrong and click **Should be a buyer** (thumbs up) or **Should NOT be a buyer** (thumbs down). This launches the **Offer Refinement** flow, where AutoReach analyzes why the score was off and suggests specific edits to your target audience or pain points. Review the suggestions and apply them. See [Score Feedback](core-concepts/buyer-intelligence.md#score-feedback).
3. After updating the offer, new leads will be scored against the updated ICP. To re-evaluate leads already in your pipeline, select them on the Leads page and run a rescore — see [Rescoring](core-concepts/buyer-intelligence.md#rescoring) for how this works.
4. Switch your discovery method. If you've been using broad people-search by role, try **From Signals** (intent-based) or **From a Lookalike** (audience of an account whose followers match your ICP). These produce higher-intent leads than role-only search.
5. Watch the next 50-100 leads. If scores trend higher and reply rate improves, the offer was the issue. If not, move to Cause (2).

**Likely Cause (2):** Messages are not compelling or personalized enough.

**Fix:** Use Simulation to preview your DMs for several different leads. If the messages read as generic, the fix is usually in the offer (richer pain points give the AI more to work with) or the template (add a `{{post}}` reference on X, or `{{current_role}}` + `{{company_name}}` on LinkedIn). Refine your message template and AI prompt until messages feel natural and relevant. See [DM Personalization](outreach/dm-personalization.md).

> **How to tell which cause is yours:** Run Simulation on 10 diverse leads. If the generated messages look generic and interchangeable, fix the message (Cause 2). If the messages look personalized but the leads themselves seem off-target, fix the offer (Cause 1).

**Likely Cause (3):** No warmup before the DM.

**Fix:** Add engagement steps before the DM in your sequence flow (like a post, follow the account, view their profile). People respond better to names they recognize.

**Likely Cause (4):** Wrong platform or timing.

**Fix:** Try switching to the other platform (X vs. LinkedIn). Also review your activity window to ensure messages arrive during business hours in the lead's time zone.

---

## Account Health Warnings

### "Rate Limited" status

**Symptom:** Account shows as rate limited, and some actions are paused.

**Likely Cause:** You hit the platform's daily or hourly limit for a specific action type.

**Fix:** AutoReach automatically applies cooldown periods when rate limits are hit. Wait for the cooldown to expire, then reduce your daily action limits to stay under the platform's thresholds. Start conservative (15-20 DMs/day for X, stay well under LinkedIn's daily connection limit).

---

### "Bot Detected" status

**Symptom:** Account shows bot detection warning, and all activity is paused.

**Likely Cause:** The platform flagged a pattern of activity that looks automated (too many actions in rapid succession, unusual hours, or suspicious IP).

**Fix:** Bot detection is treated as a serious event that requires manual intervention - AutoReach will email you and the account stays paused until you manually resume it from the Accounts page. Before resuming:
1. Investigate what the platform flagged (the error message on the account is your best clue)
2. Reduce your daily action limits significantly
3. Make sure your activity window matches realistic usage patterns
4. Verify your proxy is working (residential IPs are safest)
5. Manually resume the account from the Accounts page once you have addressed the underlying cause

> **Warning:** Repeated bot detection warnings can lead to permanent account suspension. Take them seriously and reduce your activity levels.

---

### "Auth Error" on LinkedIn

**Symptom:** LinkedIn account shows authentication error.

**Likely Cause:** Your session cookies have been revoked, often because LinkedIn detected a mismatch between your login location and the proxy location.

**Fix:** Reconnect your LinkedIn account via the Chrome Extension. If this happens repeatedly, contact support - your proxy configuration may need adjustment.

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

**Fix:** Use the **Check Acceptances** button in the Chrome Extension's CRM panel to manually trigger a detection check.

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

1. Check the specific feature's documentation page - most have their own troubleshooting section
2. Email support at **hello@autoreach.tech** with a description of the issue and any error messages you see
