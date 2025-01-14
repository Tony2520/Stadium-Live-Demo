# Stadium Live Demo: My work for the past year:

If you want to check out the app -> https://www.stadiumverse.com/

Stadium Live is a rising betting/fantasy mobile app with around 3 Million total downloads with 100K daily active users. I've spent over a year (3 internships) helping to build the new playground for Gen Z Sports fans. With an engineering team of 8, I hit the ground running and shipped multiple complex, end-to-end features. Below are 6 of the most noteworthy ones.

## Project #1: Challenges System 🎯

### Summary
As a main goal of 2024 growth initiatives, we needed a loop that incentivizes users to log in **every day** and engage in the core staking action. I spent ~2 months building out a scalable, dynamic, and personalized Daily Challenge architecture that spearheaded this goal

### Demo

https://github.com/user-attachments/assets/0d976625-32c9-4046-88b4-0f76bbc1a31b

### Technical Breakdown
**BE:**
- **Architecture**
  - 3-layer challenge class hierarchy (Daily/Weekly/One-Time)
  - Extensible OOP design following Open/Closed Principle
  - 20+ Challenge Subclasses each with unique business logic
  - Smart scheduling system adapting to user activeness
  - Automated reward distribution flow

- **Database & Performance**
  - Performance Postgres indexes reducing query time by 80%
  - Multi-table normalized structure:
    - `user_challenges`: Active challenge tracking
    - `user_claimed_challenges`: Historical records
    - `dynamic_fields`: Flexible challenge parameters for personalization
  - Automated cleanup policies maintaining table size ~50M rows

- **Load Management & Scaling**
  - Dual-mode scheduling:
    - Batch processing for 100K+ daily active users
    - On-demand BullMQ queue for new & returning users
  - Async progression system handling 1M+ daily actions
  - Peak load handling during notification spikes 

- **Smart Features**
  - Personalized dynamic challenges based on:
    - User preferences
    - Historical engagement
    - Sport/team affinities
  - Cascading reward system with smart hooks
  - Fail-safe duplicate prevention:
    - Application-level validation
    - Database-level constraints
  - Comprehensive monitoring:
    - Real-time Sentry alerts
    - Performance metrics
    - Error tracking & reporting

**FE:**
- Responsive design with animations and loading states. Inspired by Marvel Snap:
  [Marvel Snap Challenge UI](https://oyster.ignimgs.com/mediawiki/apis.ign.com/marvel-snap/c/cf/Challenges_%26_Refresh.jpeg?width=640)
- Deeplink for every challenge routing in & out of the app that mitigates completion friction
- A/B tested different entry points to find best coverage




## Project #2: Personalized Stakes 💸

### Summary
One of the biggest pivots we took in 2023 is the addition of competitive sports betting, which internally we called Stakes. I built a hefty recommendation algorithm to display 6 of the most relevant stakes to a user's feed page at any point during the day. 
Algorithm consists of...
- Personalized scoring system using users' favorites and history to find explicit and implicit relevant players, teams, and leagues
- Rank and order available Moneyline/Player Props stakes based on relevance score system. 
- Additional scoring factors such as league variety, start time decay function, and player popularity
- A degree of seed randomization to ensure uniqueness of each user's stakes for the day

### Demo

<div style="width: 100%; display: flex; justify-content: center;">
  <table style="width: 100%">
    <tr>
        <th style="width: 33%; text-align: center;">NBA Fan</th>
        <th style="width: 33%; text-align: center;">NHL Fan</th>
        <th style="width: 33%; text-align: center;">I love all sports</th>
    </tr>
    <tr>
        <td ><img src="Stakes/nba.gif" alt="nba stakes" loop=infinite></td>
        <td ><img src="Stakes/nhl.gif" alt="nhl stakes" loop=infinite></td>
        <td ><img src="Stakes/mixed.gif" alt="mixed stakes" loop=infinite></td>
    </tr>
  </table>
</div>

### Challenges and Learnings
- Really stretched my SQL knowledge. Delved into tons of PostgreSQL docs to achieve some of the behaviors mentioned above
- Many timezone-based edge cases to consider such as answered stakes, pending stakes, missed stakes, and pushed stakes (delayed)
- Learned and applied advanced SQL tools such as PostgreSQL performance indexes and nested window functions
- Quite hard to generalize a one-size-fits-all experience for our broad user base -- even Product wasn't quite sure. Took some iterations to finally land on this score-based approach. 
- Also set up as a 4-variant A/B test which experiments with limiting different sizes of pairs of Moneylines vs player props stakes.
- My last project during my internship so wrote many detailed documentations for handoff.

## Project #3: User Profile Revamp📱

### Summary
The old profile has not been touched up since a year ago -- ancient history for a startup. The goal of the revamp is to give it a more slick and thematic design along with 3 objectives in mind
  - Increase in Virality (Share rate)
  - Set up as the main entry point for the upcoming monetization expansion
  - Allow users for a more personalized skill expression (favorites, collectibles, win rates, etc)

New Profile             |  Old Profile
:-------------------------:|:-------------------------:
![](Profiles/profile_new.png)  |  ![](Profiles/profile_old.png)

### Features
- Refactored old profile queries using GraphQL batching and caching for speedy performance gains

<div style="width: 100%; display: flex; justify-content: center;">
  <table style="width: 100%">
    <tr>
        <th style="width: 33%; text-align: center;">Animated scrolling/loading components</th>
        <th style="width: 33%; text-align: center;">Faves editing and player profiles</th>
        <th style="width: 33%; text-align: center;">Badges collection</th>
    </tr>
    <tr>
        <td ><img src="Profiles/intro.gif" alt="Profile Demo"></td>
        <td ><img src="Profiles/faves.gif" alt="Faves gif"></td>
        <td ><img src="Profiles/badges.gif" alt="Badges gif"></td>
    </tr>
    <tr>
        <th style="width: 33%; text-align: center;">Paginated collectibles list & animated slider</th>
        <th style="width: 33%; text-align: center;">Paginated friends profiles</th>
        <th style="width: 33%; text-align: center;">Avatar items list view with outfit preview</th>
    </tr>
    <tr>
        <td style=><img src="Profiles/collectibles.gif" alt="Collectibles gif"></td>
        <td style=><img src="Profiles/friends.gif" alt="Friends gif"></td>
        <td style=><img src="Profiles/items.gif" alt="Items gif"></td>
    </tr>
  </table>
</div>

### Challenges and Learnings
- Lots of net new components to build out. Volume wise easily the beefiest front-end feature I'd had to build
- Animation is fun but hard. Lots of sleep lost on timing the animation parts (username scrollY, profile pic shrink, background blur) in sync with each other so that it all looks like a single
seamless scroll
- Definitely a challenge trying to make React animation work properly on both iOS and Android

## Project #4: Squad 2.0 🎮

### Summaries
Major expansion on our clan-like multiplayer mode Squad

### Features

<div style="width: 100%; display: flex; justify-content: center;">
  <table style="width: 100%">
    <tr>
        <th style="width: 33%; text-align: center;">Private/Global Squad leaderboard</th>
        <th style="width: 33%; text-align: center;">Squad weekly challenges and rewards</th>
    </tr>
    <tr>
        <td ><img src="Squads/leaderboards.gif" alt="Squads Leaderboards" loop=infinite></td>
        <td ><img src="Squads/challenge.gif" alt="Squads Challenges" loop=infinite></td>
    </tr>
    <tr>
        <th style="width: 33%; text-align: center;">Paginated squad chats with profiles</th>
        <th style="width: 33%; text-align: center;">Skill-based squads matching & animated squad card</th>
    </tr>
    <tr>
        <td style=><img src="Squads/paginatedChats.gif" alt="Squads Chats" loop=infinite></td>
        <td style=><img src="Squads/matchmaking.gif" alt="Squads LandingPage" loop=infinite></td>
    </tr>
  </table>
</div>

### Challenges and Learnings
- This was my first major project after ramp up. Took some stumbles but learned many interesting things like end-to-end deployment methods and backward compatibility
- First time working with real-time data as we use Firebase pub/sub for our chat, quite a powerful tool
- Handling squad join/leave end-to-end flow could be tricky at times. Learned a lot about thinking in different perspectives in terms of clients vs server

## Project #5: Player Mentions 🏀
### Summaries
Added player/user lookup & mention functionality into chatbox with suggestion preview, auto-complete, and player profile routing

### Demo
<img src="Mentions/mention.gif" alt="Squads Chats" loop=infinite>

### Challenges and Learnings
This nimble-looking feature was particularly hard for multiple reasons
  1. React doesn't support rich text editor natively, to achieve in-place auto-complete I had to add some complex string parsing and manipulation in our own text editor 
  2. For the mention popup to feel reactive upon input change, backend player lookup has to be near instantaneous 
  3. Non-distinct player names require extra data to be packaged and stored on the backend. Adding encode/decode structure everywhere in the codebase is a pretty big undertaking
  4. Backward compatibility is a pain to work with from 3). Sanitization had to be added everywhere to ensure no weirdness for returning users

Learnings:
  1. Learned and implemented debounced fuzzy search and GIN indexes used for speedy player lookup on the backend
  2. Hacked together a mini rich text editor to highlight and in-place auto-complete player names on the frontend

---
