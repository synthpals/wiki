---
title: Troubleshooting
description: Common problems and solutions for AI companion setups
published: true
date: 2026-01-21T15:18:40.959Z
tags: troubleshooting, help, faq
editor: markdown
dateCreated: 2026-01-21T15:18:40.959Z
---

# Troubleshooting

Common issues and how to fix them.

## API & Authentication

### "Invalid API Key" or 401 errors

**Cause:** Your API key is wrong, expired, or lacks permissions.

**Fix:**
1. Check for typos (especially leading/trailing spaces)
2. Regenerate the key from your provider's dashboard
3. Make sure the key has the right permissions
4. Check if you've hit spending limits

### "Rate limited" or 429 errors

**Cause:** You're sending too many requests too fast.

**Fix:**
1. Add delays between requests
2. Upgrade your API tier
3. Implement exponential backoff

## WhatsApp Integration

### QR code won't scan

**Fix:**
1. Make sure you're scanning with WhatsApp (not your phone camera)
2. Open WhatsApp → Settings → Linked Devices → Link a Device
3. Try regenerating the QR code
4. Check your network connection

### Messages not sending/receiving

**Fix:**
1. Check if gateway is running (`clawdbot status`)
2. Look for "disconnected" in logs
3. Re-link WhatsApp if needed
4. Check if your phone has internet

### "Session expired" or constant reconnects

**Fix:**
1. This sometimes happens after phone restarts
2. Re-scan the QR code
3. Make sure WhatsApp is updated

## Memory Issues

### AI keeps forgetting things

**Possible causes:**
1. Memory files not being written
2. Memory search not configured
3. Context window too small
4. Compaction losing important details

**Fix:**
1. Check if memory files exist and are being updated
2. Configure semantic search (e.g., local embeddings)
3. Use a model with larger context window
4. Tune compaction settings

### AI "remembers" things that never happened

**Cause:** Hallucination, not a memory bug.

**Fix:**
1. Be more explicit when correcting
2. Update memory files manually to fix wrong info
3. Consider shorter compaction cycles

## Performance

### Responses are very slow

**Possible causes:**
1. Using a large/expensive model
2. Network issues to API provider
3. Context window full (lots of memory loaded)

**Fix:**
1. Try a faster model for simple tasks
2. Check API provider status page
3. Reduce memory/context being loaded

### High token usage / costs

**Fix:**
1. Use prompt caching if available
2. Reduce system prompt size
3. Implement smarter memory loading
4. Use cheaper models for simple tasks

---
*Got a solution to add? Submit a PR or reach out on synthpals.social!*