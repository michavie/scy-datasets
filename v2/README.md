## V2

The provided data is close to what our API returns. While the API is not released yet, we don't expect any significant breaking changes at this point and can provide you with access via a generated token.

Documentation of experimental API: [https://api.superciety.com/docs/#endpoints](https://api.superciety.com/docs/#endpoints) (includes Postman collection and OpenApi specs).

## Requested Data

1. Listing of DAOs, with description, members
   - Is available via API endpoint: `v1/entities`
   - Manual JSON export provided as: `entities.json`
   - Formatted CSV (can open with Excel) provided as: `entities.csv`
   - Members who have a 'role' are included in the JSON export
   - Members who have connected at least once to superciety can be retrieved via API `v1/entities/{entityAddress}/members`
   - Other members can be retrieved from Explorer or MultiversX API **as holders of the governance token**
2. Number or proposals executed, passed, failed
   - Manual global JSON export provided as: `stats-global.json`
   - Available globally via API: `v1/stats`
   - Available per DAO via API: `v1/entities/{entityAddress}/stats`
3. Most active addresses, proposal creation/voting
   - Manual JSON export provided as: `stats-members-votes-global.json` (contains first 100 returned from API)
   - Available globally via API: `v1/stats/members?sort=votes`
   - Available per DAO via API: `v1/entities/{entityAddress}/members?sort=votes`
4. Addresses with most passed proposals
   - Manual JSON export provided as: `stats-members-proposals-global.json`
   - Available globally via API: `v1/stats/members?sort=proposals`
   - Available per DAO via API: `v1/entities/{entityAddress}/members?sort=proposals`
5. Excel of all the possible DAO contracts and their description
   - Formatted CSV (can open with Excel) provided as: `entities.csv` (let me know if you meant something different)
6. Video tutorials on using snapshot.
   - Videos tutorials are currently not available.

## Data Types

The API exports contain collections (array) of domain-specific objects:

- `User`: in `full-api-exports/all-stats-members-proposals-global.json` & `all-stats-members-votes-global.json`
- `Entity` (the Fellowship DAO): in `full-api-exports/all-entities.json`

While their general properties can be derived from the provided exports, here are a few more details that may be good to know:

### About the USER object

The user object contains general information about members, but can also contain _conditional_ properties depending on the context:

- in `all-stats-members-proposals-global.json`: a conditional `proposals` (integer) property that signals the total amount of PROPOSALS created by the user
- in `all-stats-members-votes-global.json`: a conditional `votes` (integer) property that signals the total amount VOTES the user has performed

### About the ENTITY object

The Entity object also contains general information about the Fellowship DAO, including a `roles` property which is an array of Roles created for the DAO. Each of those roles lists `User`s that are assigned a role in the `Entity` under the `roles->*->users` key.

---

In addition to the above, there is a lot more data that can be fetched using the API. Please refer to the [docs](https://api.superciety.com/docs/#endpoints).
