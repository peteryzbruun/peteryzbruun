# Chess.com Profile and Rating Badges

Copy-ready badges for the `peteryzbruun` GitHub profile. The live badges use Shields.io to read public rating fields from Chess.com's Published-Data API. They link through to the Chess.com profile.

## Account and data source

- Chess.com profile: <https://www.chess.com/member/peteryzbruun>
- Public stats endpoint: <https://api.chess.com/pub/player/peteryzbruun/stats>
- Username used below: `peteryzbruun`

The stats endpoint currently returns the fields used here: Rapid, Blitz, Bullet, Daily, and the highest puzzle rating. Ratings are public profile data; the requests need no account credentials.

## Profile badge choices

The profile README highlights Daily and puzzle peak because those are the modes Peter plays most. Puzzle is a peak rating, while Daily is the latest published rating. Rapid, Blitz, and Bullet are included below as alternate live rating badges.

```html
<p>
  <a href="https://www.chess.com/member/peteryzbruun"><img alt="Chess.com Rapid rating" src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.chess.com%2Fpub%2Fplayer%2Fpeteryzbruun%2Fstats&query=%24.chess_rapid.last.rating&label=rapid&logo=chessdotcom&logoColor=white&color=81B64C" /></a>
  <a href="https://www.chess.com/member/peteryzbruun"><img alt="Chess.com Blitz rating" src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.chess.com%2Fpub%2Fplayer%2Fpeteryzbruun%2Fstats&query=%24.chess_blitz.last.rating&label=blitz&logo=chessdotcom&logoColor=white&color=0096FF" /></a>
  <a href="https://www.chess.com/member/peteryzbruun"><img alt="Chess.com Bullet rating" src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.chess.com%2Fpub%2Fplayer%2Fpeteryzbruun%2Fstats&query=%24.chess_bullet.last.rating&label=bullet&logo=chessdotcom&logoColor=white&color=E76F51" /></a>
</p>
```

For a static profile link with no API dependency:

```markdown
[![Chess.com](https://img.shields.io/badge/Chess.com-81B64C?logo=chessdotcom&logoColor=white)](https://www.chess.com/member/peteryzbruun)
```

## Rapid, Blitz, Bullet, and puzzle peak

Use these if you want to feature other time controls. Puzzle uses `tactics.highest.rating`, a peak value rather than a current game-mode rating.

```markdown
[![Chess.com Daily rating](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.chess.com%2Fpub%2Fplayer%2Fpeteryzbruun%2Fstats&query=%24.chess_daily.last.rating&label=daily&logo=chessdotcom&logoColor=white&color=607D8B)](https://www.chess.com/member/peteryzbruun)
[![Chess.com Puzzle peak](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.chess.com%2Fpub%2Fplayer%2Fpeteryzbruun%2Fstats&query=%24.tactics.highest.rating&label=puzzle%20peak&logo=chessdotcom&logoColor=white&color=8B5CF6)](https://www.chess.com/member/peteryzbruun)
```

## How the live badge URL works

- `dynamic/json` tells Shields.io to fetch a JSON document and display a selected value.
- `url=` is the Chess.com stats URL, percent-encoded as a query parameter value.
- `query=` is JSONPath. `%24` is the URL-encoded `$` root: `%24.chess_rapid.last.rating` selects `chess_rapid.last.rating`.
- `label=`, `logo=`, `logoColor=`, and `color=` set the text, icon, and colors.
- The surrounding Markdown link or HTML anchor sends a click to the Chess.com profile. It does not change the data request.

The JSON fields are:

| Badge | JSONPath | Meaning |
|---|---|---|
| Rapid | `$.chess_rapid.last.rating` | Latest published Rapid rating |
| Blitz | `$.chess_blitz.last.rating` | Latest published Blitz rating |
| Bullet | `$.chess_bullet.last.rating` | Latest published Bullet rating |
| Daily | `$.chess_daily.last.rating` | Latest published Daily rating |
| Puzzle peak | `$.tactics.highest.rating` | Highest recorded puzzle rating |

## Updates and troubleshooting

Chess.com describes the PubAPI as read-only and says endpoints refresh at most once every 12 hours. Shields.io also caches dynamic badge responses, so a game result may take time to appear in a badge.

If a badge shows an error or no value:

1. Open the stats endpoint above and check whether the selected field exists and has a rating.
2. Confirm the `query` matches the field path in the response.
3. Allow for Chess.com and Shields.io caching, then reload the profile.
4. Use the static profile badge if either service is unavailable.

These badges use public profile data and contain no credentials. A dynamic badge depends on both Chess.com's API and Shields.io; neither service guarantees that a badge will always render.

## Sources

- [Chess.com Published-Data API help](https://support.chess.com/en/articles/9650547-what-is-the-pubapi-and-how-do-i-use-it)
- [Chess.com player stats](https://api.chess.com/pub/player/peteryzbruun/stats)
- [Shields.io Dynamic JSON Badge](https://shields.io/badges/dynamic-json-badge)
