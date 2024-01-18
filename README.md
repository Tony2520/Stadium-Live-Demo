


# Stadium Live Demo: My work for the past 8 months:

If you want to check out the app -> https://www.stadiumverse.com/

Stadium Live is a rising betting / fantasy mobile app with around 80k daily active user and 250K total downloads. With an engineering team of 8,
I hit the ground running and shipped multiple complex, end-to-end features. Below are 4 most note-worthy ones.

## Feature#1: User Profile Revamp📱

### Summary
The old profile has not been touched up since a year ago -- ancient history for a startup. The goal of the revamp is to give it a more slick and themeatic design along with 3 objectives in mind
  - Increase in Virality (Share rate)
  - Set up as main entry point for the upcoming monitization expansion
  - Allow users for a more personalized skill expression (favourites, win rates, etc)

New Profile             |  Old Profile
:-------------------------:|:-------------------------:
![](Profiles/profile_new.png)  |  ![](Profiles/profile_old.png)



### Features
- Refractored old profile queries using graphql batching and caching for speedy performance gains

<div style="width: 100%; display: flex; justify-content: center;">
  <table style="width: 100%">
    <tr>
        <th style="width: 50%; text-align: center;">Smooth, animated scrolling/loading components</th>
        <th style="width: 50%; text-align: center;">Faves editing and player profiles</th>
    </tr>
    <tr>
        <td><img src="Profiles/intro.gif" alt="Profile Demo"></td>
        <td><img src="Profiles/faves.gif" alt="Faves gif"></td>
    </tr>
    <tr>
        <td style="width: 50%; text-align: center;">Badges collection</td>
        <td style="width: 50%; text-align: center;">Paginated collectibles scroll view and animated slider</td>
    </tr>
    <tr>
        <td style="text-align: center;"><img src="Profiles/badges.gif" alt="Badges gif"></td>
        <td style="text-align: center;"><img src="Profiles/collectibles.gif" alt="Collectibles gif"></td>
    </tr>
    <tr>
        <td style="width: 50%; text-align: center;">Paginated friends profiles</td>
        <td style="width: 50%; text-align: center;">Avatar items list view with output preview</td>
    </tr>
    <tr>
        <td style="text-align: center;"><img src="Profiles/friends.gif" alt="Friends gif"></td>
        <td style="text-align: center;"><img src="Profiles/items.gif" alt="Items gif"></td>
    </tr>
  </table>
</div>