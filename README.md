# hsa13-hw17-peak-loadings

Describe solution that solves peak loadings problem for biggest european football website https://goal.com 

1. Analyze all types of pages on the site
2. Analyze and list possible sources of peak loadings
3. Describe possible solution for each type 

## Page Types on Goal.com
I looked at Goal.com and identified the main types of pages:
- **Homepage**: Shows trending news, live scores, and links to other sections.
- **Live Match Pages**: Real-time scores, commentary, and stats for ongoing matches.
- **News Articles**: Articles about transfers, interviews, and events.
- **Match Reports/Previews**: Post-match reports and pre-match analysis.
- **Video Pages**: Highlight videos, interviews, and analysis.
- **User Interaction Pages**: Comments, forums, and polls.

## Sources of Peak Loadings
Here are the main reasons for peak loadings:
- **High Traffic During Matches**: Big games (e.g., Champions League finals) cause traffic spikes on live match pages and the homepage.
- **Breaking News**: Major events like transfers or scandals drive users to news articles and the homepage.
- **Live Updates**: Users refreshing live match pages for scores and commentary.
- **Video Streaming**: Many users watching highlight videos after matches.
- **User Activity**: Comments and polls spike during controversial events.
- **Bots and Attacks**: Bot scraping and DDoS attacks overload servers.
- **Push Notifications**: Notifications about goals or news cause sudden traffic surges.

## Solutions for Each Page Type

- **Homepage**:
  - Use a CDN (like Amazon CloudFront) to cache static content (images, CSS).
  - Scale backend servers with AWS Auto Scaling during big match days.
  - Send push notifications in batches to avoid sudden spikes.

- **Live Match Pages**:
  - Use WebSockets instead of polling to push live updates (scores, stats).
  - Cache static elements (e.g., team logos) with a CDN.
  - Auto-scale servers during popular matches.

- **News Articles**:
  - Cache articles with a CDN to serve them faster.
  - Use Redis to cache popular articles in memory.
  - Limit bot access with rate limiting in Nginx.

- **Match Reports/Previews**:
  - Pre-generate reports as static pages and host them on a CDN.
  - Use AWS Lambda to generate reports after matches and push them to the CDN.

- **Video Pages**:
  - Host videos on a streaming service like Amazon CloudFront with adaptive bitrate streaming.
  - Block external embedding to prevent uncontrolled traffic.

- **User Interaction Pages**:
  - Cache comments for a few seconds before saving to the database.
  - Add CAPTCHA to block spambots in comment sections.
  - Use AWS Lambda for handling user interactions (e.g., votes, comments).

## General Solutions
I also thought of some overall strategies:
- **Predictive Scaling**: Scale servers before big matches based on schedules.
- **DDoS Protection**: Use AWS Shield or Cloudflare to protect against attacks.
- **Rate Limiting**: Limit bot requests with `robots.txt` and Nginx rules.
- **Monitoring**: Set up real-time monitoring to detect traffic spikes.
