# Contributing to ChatProfiles

Bug reports and small pull requests are welcome.

## Ground rules

- Keep changes focused — one thing per pull request.
- Match the existing code style.
- Use the stable Paper API only, no NMS, so the plugin keeps working across versions.
- Don't do disk access on event or main threads; heavy work goes through the async pipeline.

