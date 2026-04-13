# A/B Testing with the Simulator

Use the Conversation Simulator to test messaging variations before sending them to real leads. By simulating multiple variants with diverse leads, you can identify which approaches resonate best with your target audience.

For instructions on running simulations and previewing messages, see [Simulation](simulation.md).

## Testing Strategies

### Test 1: Soft vs. Direct Ask

**Variant A (Soft):**

```
Hi {{first_name}},

Saw your post on {{topic}}. Would love to connect and learn
how you're thinking about it.
```

**Variant B (Direct):**

```
{{first_name}},

We help {{company_size}} companies improve {{pain_point}}.
Interested in a quick conversation?
```

Simulate both with 3-5 different leads. Which feels more authentic for your audience?

### Test 2: Long vs. Short

**Variant A (Long):**

```
Hi {{first_name}},

I've been following {{company}} for a while and really impressed
by how you're building {{achievement}}.

In my experience working with similar companies, one thing that often
holds teams back is {{pain_point}}. We've built a framework to help with this.

Would you be open to a 20-min conversation to explore?
```

**Variant B (Short):**

```
{{first_name}},

Impressed by {{company}}'s progress. We help with {{pain_point}}.
Worth a chat?
```

Simulate with your target audience. Short and punchy, or long and detailed?

### Test 3: Reference vs. No Reference

**Variant A (Reference):**

```
{{first_name}},

Noticed your post about {{recent_topic}}. We've worked with
{{example_company}} on the same challenge.

Worth a conversation?
```

**Variant B (Generic):**

```
{{first_name}},

We help companies like {{company}} improve {{pain_point}}.
Interested?
```

Does referencing their specific activity or posts produce better simulated responses?

### Test 4: Tone

**Variant A (Professional):**

```
Dear {{first_name}},

I would like to discuss how we can assist {{company}}
in improving {{pain_point}}.
```

**Variant B (Casual):**

```
Hey {{first_name}},

Been following {{company}}'s journey. Think we could help
with {{pain_point}}.

Worth exploring?
```

## Tips for Effective A/B Testing

1. **Simulate with 5+ different leads** -- not just one. Include different roles, industries, and company sizes.
2. **Include edge cases** -- leads with minimal data or from unexpected companies.
3. **Test AI responses** -- reply as different lead personas (eager, skeptical, uninterested) and compare how each variant handles follow-ups.
4. **Document patterns** -- note which messaging approaches work best for different audience segments.
5. **Re-test before scaling** -- before launching to a large audience, run fresh simulations to confirm your chosen variant.

## Next Steps

- **[Simulation](simulation.md)**: Run simulations and preview messages with real lead data
- **[Cold DM Generation](cold-dm-generation.md)**: How AI generates personalized first messages
- **[Template Variables](template-variables.md)**: All available personalization variables
