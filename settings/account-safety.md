# Account Safety & Anti-Detection

AutoReach is built to protect your accounts from detection while automating outreach. It uses advanced techniques to mimic real user behavior across X/Twitter and LinkedIn.

## TLS Fingerprinting

AutoReach connects to X/Twitter and LinkedIn with **Chrome-identical TLS fingerprints**:

- **Technology** - Go-based TLS client with hardcoded cipher suites
- **Matching** - exact replication of Chrome's cipher suite order and HTTP/2 behavior
- **Detection Evasion** - advanced TLS fingerprinting services see a real Chrome browser
- **Updates** - fingerprints updated when Chrome releases major versions

{% hint style="info" %}
TLS fingerprinting is one of the most advanced detection techniques. By matching Chrome exactly, AutoReach bypasses commercial bot detection services that rely on TLS analysis.
{% endhint %}

## User-Agent Rotation

Each account maintains a realistic browser identity:

- **Diverse Signatures** - 40+ realistic user agent strings (Chrome, Firefox, Safari, Edge versions)
- **Per-Account Persistence** - same user-agent between actions for 14-30 days
- **Consistent Fingerprint** - device platform, screen resolution, and language match the user-agent
- **Auto-Rotation Timing** - randomized per account to avoid patterns

### Platform Emulation
- **Browser Platform** - configurable per account (Windows, Mac, Linux)
- **Chrome Extension Detection** - AutoReach's extension auto-detects `navigator.platform` from your actual browser

## Rate Limiting & Request Management

### X/Twitter
X has informal rate limits on DMs and actions. AutoReach respects these by:

- **Daily Caps** - configurable limits (default 20 DMs/day)
- **Exponential Backoff** - automatic retry with increasing delays on failures
- **Activity Windows** - most actions scheduled during configured hours (default 9am-6pm)

### LinkedIn (Three-Layer Defense)

LinkedIn's automation detection is sophisticated. AutoReach uses three overlapping protections:

**Layer 1: Concurrency Semaphore**
- Maximum 1 concurrent operation at a time
- Prevents bursty traffic patterns that signal bots

**Layer 2: Token Bucket**
- 15 requests per minute maximum
- Smooths request rate to appear human

**Layer 3: Daily Budget**
- 25,000 requests per day hard cap
- Automatically pauses if approaching limit

{% hint style="warning" %}
All three layers must be respected. A single layer breach can trigger platform suspicion. AutoReach enforces all three simultaneously.
{% endhint %}

## Emergency Pause

AutoReach instantly pauses automation if it detects platform warnings:

- **429 (Too Many Requests)** - immediate pause for rate limiting
- **999 (Automation Detected)** - LinkedIn's explicit automation flag
- **403 with Automation Keywords** - blocks mentioning "bot", "automation", or "script"

When emergency pause activates:
1. All pending actions are canceled
2. The account shows "Safety Pause" status
3. You receive a notification with the trigger reason
4. Manual resume is required before automation restarts

## Human Delay Simulation

AutoReach simulates realistic human behavior between actions:

### Reading Speed
- **Range** - 200-300 words per minute
- **Logic** - delays longer for complex profiles, shorter for simple data
- **Variation** - randomized around the base calculation

### Typing Speed
- **Range** - 40-60 words per minute
- **Distribution** - log-normal distribution (natural human typing rhythm)
- **Mistakes & Backspace** - rare character corrections simulated

### Action Timing
- **Time-of-Day Multiplier** - slower during 2am-6am, faster during 10am-2pm
- **Day-of-Week Multiplier** - slightly slower on weekends, busier on Tuesdays through Thursdays
- **Session Breaks** - automatic 30-60min breaks after 2-3 hours of activity
- **Action Abandon Rate** - 4% of scheduled actions randomly abandoned (like a human forgetting)

### Per-Account Personality
Each account develops its own behavior pattern:

- **Action Latency Profile** - unique delay distribution per account
- **Session Schedule** - consistent preferred activity windows
- **Action Preference Order** - some accounts engage more, some message more

{% hint style="tip" %}
These delays genuinely protect your account. They slow down automation slightly, but dramatically reduce suspension risk. The slowdown is usually invisible to campaign performance.
{% endhint %}

## Account Health Monitoring

AutoReach tracks account health with a 24-hour rolling window:

### Health Status Conditions

| Condition              | Detection                | Cooldown  | Impact                                            |
| ---------------------- | ------------------------ | --------- | ------------------------------------------------- |
| **Rate Limited**       | Soft blocks detected     | 24 hours  | 50% action capacity reduction                     |
| **Bot Detected**       | 429/999 from platform    | 7 days    | 90% capacity (near-stop)                          |
| **Auth Error**         | Session expired          | 48 hours  | Auto-recover with re-auth                         |
| **Proxy Error**        | Proxy connection failed  | 24 hours  | Auto-recover on next action                       |
| **IP Blocked**         | 403/IP ban detected      | 24 hours  | Full stop (requires new proxy IP)                 |
| **CAPTCHA Required**   | User solve needed        | Manual    | 30% of CAPTCHA solves succeed                     |
| **Timeout/Network**    | Connection timeout       | 2 hours   | 20% action success rate during period             |
| **AI Provider Error**  | OpenAI/Anthropic down    | Manual    | Personalization disabled, fallback model           |

### Response Actions

When health issues are detected:

- **Minor Issues (Auth, Proxy, Timeout)** - auto-recovery attempted, actions continue
- **Medium Issues (Rate Limit)** - capacity reduced to 50%, actions continue slower
- **Severe Issues (Bot Detection, IP Block)** - automatic emergency pause, requires manual review
- **Critical Issues (Suspension)** - account marked suspended, no actions scheduled

## Negative Content Screening

AutoReach skips leads posting about certain topics to protect account safety:

### Skipped Topics
- Death and obituaries
- Serious illness or injury
- Disasters and emergencies
- Graphic violence or injury
- Self-harm

### Allowed (Usually Safe)
- Work frustrations and complaints
- Business failures and layoffs
- Industry criticism or problems
- Competitive pressure

{% hint style="info" %}
Engaging with people posting about death, illness, or disasters damages account trust. Engaging with people complaining about work or layoffs is acceptable and normal professional networking.
{% endhint %}

## Browser Extension Security

AutoReach's Chrome extension provides:

- **Secure Cookie Storage** - encrypted, never sent to AutoReach servers
- **Local-Only Operation** - session management happens on your machine
- **Platform Auto-Detection** - automatically detects your browser's navigator.platform
- **No Password Storage** - you input credentials once per session

## Best Practices for Account Safety

1. **Use Dedicated Proxies** - one proxy per account minimum
2. **Rotate Accounts** - spread activity across 3+ accounts if possible
3. **Respect Daily Limits** - do not set limits higher than 20-30/day on X, 30-50/day on LinkedIn
4. **Monitor Health** - check the Accounts dashboard weekly
5. **Warm up new accounts with the Engagement Engine** - respect the 4-week ramp-up period on LinkedIn
6. **Pause Proactively** - if you see warnings, pause before emergency pause triggers
7. **Update Your Proxy** - replace proxies every 3-6 months to avoid IP reputation issues

{% hint style="warning" %}
No anti-detection technique is 100% foolproof. Platform detection systems are constantly evolving. AutoReach's safety measures reduce risk significantly, but aggressive automation always carries some suspension risk.
{% endhint %}
