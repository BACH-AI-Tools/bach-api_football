# Api Football MCP Server

[English](./README_EN.md) | 简体中文 | [繁體中文](./README_ZH-TW.md)

## 🚀 使用 EMCP 平台快速体验

**[EMCP](https://sit-emcp.kaleido.guru)** 是一个强大的 MCP 服务器管理平台，让您无需手动配置即可快速使用各种 MCP 服务器！

### 快速开始：

1. 🌐 访问 **[EMCP 平台](https://sit-emcp.kaleido.guru)**
2. 📝 注册并登录账号
3. 🎯 进入 **MCP 广场**，浏览所有可用的 MCP 服务器
4. 🔍 搜索或找到本服务器（`bach-api_football`）
5. 🎉 点击 **"安装 MCP"** 按钮
6. ✅ 完成！即可在您的应用中使用

### EMCP 平台优势：

- ✨ **零配置**：无需手动编辑配置文件
- 🎨 **可视化管理**：图形界面轻松管理所有 MCP 服务器
- 🔐 **安全可靠**：统一管理 API 密钥和认证信息
- 🚀 **一键安装**：MCP 广场提供丰富的服务器选择
- 📊 **使用统计**：实时查看服务调用情况

立即访问 **[EMCP 平台](https://sit-emcp.kaleido.guru)** 开始您的 MCP 之旅！


---

## 简介

这是一个 MCP 服务器，用于访问 Api Football API。

- **PyPI 包名**: `bach-api_football`
- **版本**: 1.0.0
- **传输协议**: stdio


## 安装

### 从 PyPI 安装:

```bash
pip install bach-api_football
```

### 从源码安装:

```bash
pip install -e .
```

## 运行

### 方式 1: 使用 uvx（推荐，无需安装）

```bash
# 运行（uvx 会自动安装并运行）
uvx --from bach-api_football bach_api_football

# 或指定版本
uvx --from bach-api_football@latest bach_api_football
```

### 方式 2: 直接运行（开发模式）

```bash
python server.py
```

### 方式 3: 安装后作为命令运行

```bash
# 安装
pip install bach-api_football

# 运行（命令名使用下划线）
bach_api_football
```

## 配置

### API 认证

此 API 需要认证。请设置环境变量:

```bash
export API_KEY="your_api_key_here"
```

### 环境变量

| 变量名 | 说明 | 必需 |
|--------|------|------|
| `API_KEY` | API 密钥 | 是 |
| `PORT` | 不适用 | 否 |
| `HOST` | 不适用 | 否 |



### 在 Claude Desktop 中使用

编辑 Claude Desktop 配置文件 `claude_desktop_config.json`:


```json
{
  "mcpServers": {
    "api_football": {
      "command": "uvx",
      "args": ["--from", "bach-api_football", "bach_api_football"],
      "env": {
        "API_KEY": "your_api_key_here"
      }
    }
  }
}
```

**注意**: 请将 `E:\path\to\api_football\server.py` 替换为实际的服务器文件路径。


## 可用工具

此服务器提供以下工具:


### `v3___fixtures_head_to_head_between_two_teams`

$241

**端点**: `GET /v3/fixtures/headtohead`


**参数**:

- `h2h` (string) *必需*: The ids of the teams id-id

- `date` (string): A valid date

- `league` (string): The id of the league

- `season` (string): The season of the league 4 characters Like 2020; 2021 ...

- `last` (string): For the X last fixtures <= 2 characters

- `next` (string): For the X next fixtures <= 2 characters

- `from` (string): A valid date

- `to` (string): A valid date

- `venue` (string): The venue id of the fixture

- `status` (string): One or more fixture status short Like NS or NS-FT-CANC

- `timezone` (string): A valid timezone from the endpoint Timezone



---


### `v3___top_yellow_cards`

Get the 20 players with the most yellow cards for a league or cup.  **How it is calculated:**         * 1 : The player that received the higher number of yellow cards         * 2 : The player that received the higher number of red cards         * 3 : The player that assists in the higher number of matches         * 4 : The player that played the fewer minutes  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.

**端点**: `GET /v3/players/topyellowcards`


**参数**:

- `league` (string) *必需*: The id of the league

- `season` (string) *必需*: The season of the league 4 characters Like 2020, 2021 ...



---


### `v3___injuries_by_team_id_and_season`

$242

**端点**: `GET /v3/injuries`


**参数**:

- `league` (string): The id of the league

- `season` (string): The season of the league, required with league, team and player parameters

- `fixture` (string): The id of the fixture

- `team` (string): The id of the team

- `player` (string): The id of the player

- `date` (string): A valid date

- `timezone` (string): A valid timezone from the endpoint Timezone



---


### `v3___teams_seasons`

Get the list of seasons available for a team.  **This endpoint requires at least one parameter.** **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get all seasons available for a team from one team {id} `https://api-football-v1.p.rapidapi.com/v3/teams/seasons?team=33`

**端点**: `GET /v3/teams/seasons`


**参数**:

- `team` (string) *必需*: The id of the team



---


### `v3___odds_in_play`

$243

**端点**: `GET /v3/odds/live`


**参数**:

- `fixture` (string): The id of the fixture

- `league` (string): The id of the league In this endpoint the \\\\\\\"season\\\\\\\" parameter is not needed

- `bet` (string): The id of the bet



---


### `v3___fixtures_from_severals_fixtures_ids`

$244

**端点**: `GET /v3/fixtures`


**参数**:

- `id` (string): The id of the fixture

- `live` (string): Enum: all or id-id for filter by league id

- `date` (string): A valid date

- `league` (string): The id of the league

- `season` (string): The season of the league 4 characters Like 2020; 2021 ...

- `team` (string): The id of the team

- `last` (string): For the X last fixtures <= 2 characters

- `next` (string): For the X next fixtures <= 2 characters

- `from` (string): A valid date

- `to` (string): A valid date

- `round` (string): The round of the fixture

- `timezone` (string): A valid timezone from the endpoint Timezone

- `status` (string): One or more fixture status short Like NS or NS-FT-CANC

- `venue` (string): The venue id of the fixture

- `ids` (string): One or more fixture ids id-id-id Maximum of 20 fixtures ids



---


### `v3___coachs_by_team_id`

Get all the information about the coachs and their careers.  **Update Frequency** : This endpoint is updated every day. **Recommended Calls** : 1 call per day.  **Use Cases** Get coachs from one coach {id} `https://api-football-v1.p.rapidapi.com/v3/coachs?id=1`  Get coachs from one {team} `https://api-football-v1.p.rapidapi.com/v3/coachs?team=33`  Allows you to search for a coach in relation to a coach {name} `https://api-football-v1.p.rapidapi.com/v3/coachs?search=Klopp`

**端点**: `GET /v3/coachs`


**参数**:

- `id` (string): The id of the coach

- `team` (string): The id of the team



---


### `statisticsfixturefixture_id`

Get all statistics game from one fixture

**端点**: `GET /statistics/fixture/{fixture_id}/`


**参数**:

- `fixture_id` (string) *必需*: Example value: 



---


### `v3___odds_bets__in_play`

Get all available bets for in-play odds.  All bets `id` can be used in endpoint `odds/live` as filters, **but are not compatible with endpoint `odds` for pre-match odds**.  **Update Frequency** : This endpoint is updated every 60 seconds.

**端点**: `GET /v3/odds/live/bets`



---


### `v3___teams_countries`

Get the list of countries available for the `teams` endpoint.  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get all countries available for the teams endpoints `https://api-football-v1.p.rapidapi.com/v3/teams/countries`

**端点**: `GET /v3/teams/countries`



---


### `v3___teams_informations`

Get the list of available teams.  The team `id` are **unique** in the API and teams keep it among all the leagues/cups in which they participate.  \u003e All the parameters of this endpoint can be used together.  **This endpoint requires at least one parameter.**  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get one team from one team {id} `https://api-football-v1.p.rapidapi.com/v3/teams?id=33`  Get one team from ...

**端点**: `GET /v3/teams`


**参数**:

- `id` (string): The id of the team

- `name` (string): The name of the team

- `league` (string): The id of the league

- `season` (string): The season of the league 4 characters Like 2019, 2020, 2021 ...

- `country` (string): The country name of the team

- `code` (string): The code of the team

- `venue` (string): The id of the venue



---


### `v3___search_league`

$24d

**端点**: `GET /v3/leagues`


**参数**:

- `id` (string): The id of the league

- `name` (string): The name of the league

- `country` (string): The country name of the league

- `code` (string): The Alpha2 code of the country 2 characters Like FR, GB, IT…

- `season` (string): The season of the league 4 characters Like 2018, 2019 etc...

- `team` (string): The id of the team

- `type` (string): The type of the league Enum: league or cup

- `current` (string): The state of the league Enum: true or false

- `last` (string): The X last leagues/cups added in the API <= 2 characters



---


### `v3___search_player`

$24e

**端点**: `GET /v3/players`


**参数**:

- `id` (string): The id of the player

- `team` (string): The id of the team

- `league` (string): The id of the league

- `season` (string): The season of the league 4 characters Requires the fields Id, League or Team

- `page` (string): Use for the pagination Default: 1



---


### `v3___search_bookmaker`

Get all available bookmakers.  All bookmakers `id` can be used in endpoint odds as filters.  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get all available bookmakers `https://api-football-v1.p.rapidapi.com/v3/odds/bookmakers`  Get bookmaker from one {id} `https://api-football-v1.p.rapidapi.com/v3/odds/bookmakers?id=1`  Allows you to search for a bookmaker in relation to a bookmakers {name} `https://api-football-v...

**端点**: `GET /v3/odds/bookmakers`


**参数**:

- `id` (string): The id of the bookmaker



---


### `v3___search_country`

Get the list of available countries.  The `name` and `code` fields can be used in other endpoints as filters. \u003e Examples available in Request samples \

**端点**: `GET /v3/countries`


**参数**:

- `name` (string): The name of the country

- `code` (string): The Alpha2 code of the country 2 characters Like FR, GB, IT…



---


### `v3___search_venue`

Get the list of available venues.  The venue `id` are **unique** in the API.  \u003e All the parameters of this endpoint can be used together.  **This endpoint requires at least one parameter.**  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get one venue from venue {id} `https://api-football-v1.p.rapidapi.com/v3/venues?id=556`  Get one venue from venue {name} `https://api-football-v1.p.rapidapi.com/v3/venues?name=...

**端点**: `GET /v3/venues`


**参数**:

- `id` (string): The id of the venue

- `name` (string): The name of the venue

- `city` (string): The city of the venue

- `country` (string): The country name of the venue



---


### `v3___search_bet`

Get all available bets.  All bets `id` can be used in endpoint odds as filters.  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get all available bets `https://api-football-v1.p.rapidapi.com/v3/odds/bets`  Get bet from one {id} `https://api-football-v1.p.rapidapi.com/v3/odds/bets?id=1`  Allows you to search for a bet in relation to a bets {name} `https://api-football-v1.p.rapidapi.com/v3/odds/bets?search=winner`

**端点**: `GET /v3/odds/bets`


**参数**:

- `id` (string): The id of the bet



---


### `v3___seasons`

Get the list of available seasons.  All seasons are only **4-digit keys**, so for a league whose season is `2018-2019` like the English Premier League (EPL), the `2018-2019` season in the API will be `2018`.  All `seasons` can be used in other endpoints as filters.  \u003e This endpoint does not require any parameters.  **Update Frequency** : This endpoint is updated each time a new league is added. **Recommended Calls** : 1 call per day.

**端点**: `GET /v3/leagues/seasons`



---


### `v3___odds_mapping`

Get the list of available odds.  All fixtures, leagues `id` and `date` can be used in endpoint odds as filters.  This endpoint uses a **pagination system**, you can navigate between the different pages thanks to the `page` parameter.  \u003e **Pagination** : 100 results per page.  **Update Frequency** : This endpoint is updated every day. **Recommended Calls** : 1 call per day.

**端点**: `GET /v3/odds/mapping`


**参数**:

- `page` (string): Use for the pagination Default: 1



---


### `v3___fixtures_statistics`

$24f

**端点**: `GET /v3/fixtures/statistics`


**参数**:

- `fixture` (string) *必需*: The id of the fixture

- `team` (string): The id of the team

- `type` (string): The type of statistics Like Fouls, Offsides...



---


### `v3___fixtures_lineups`

$250

**端点**: `GET /v3/fixtures/lineups`


**参数**:

- `fixture` (string) *必需*: The id of the fixture

- `team` (string): The id of the team

- `player` (string): The id of the player

- `type` (string): The Lineup type Like Formation, Substitutes...



---


### `v3___players_statistics_by_fixture_id`

Get the players statistics from one fixture.  **Update Frequency** : This endpoint is updated every minute. **Recommended Calls** : 1 call every minute for the fixtures in progress otherwise 1 call per day.  **Use Cases** Get all available players statistics from one {fixture} `https://api-football-v1.p.rapidapi.com/v3/fixtures/players?fixture=169080`  Get all available players statistics from one {fixture} \u0026 {team} `https://api-football-v1.p.rapidapi.com/v3/fixtures/players?fixture=1690...

**端点**: `GET /v3/fixtures/players`


**参数**:

- `fixture` (string) *必需*: The id of the fixture

- `team` (string): The id of the team



---


### `v3___players_squads`

Return the current squad of a team when the `team` parameter is used. When the `player` parameter is used the endpoint returns the set of teams associated with the player.  \u003e The response format is the same regardless of the parameter sent.  **This endpoint requires at least one parameter.**  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per week.  **Use Cases** Get all players from one {team} `https://api-football-v1.p.rapidapi.com/...

**端点**: `GET /v3/players/squads`


**参数**:

- `team` (string): The id of the team

- `player` (string): The id of the player



---


### `v3___top_assists`

Get the 20 best players assists for a league or cup.  **How it is calculated:**         * 1 : The player that has delivered the higher number of goal assists         * 2 : The player that has scored the higher number of goals         * 3 : The player that has scored the fewer number of penalties         * 4 : The player that assists in the higher number of matches         * 5 : The player that played the fewer minutes         * 6 : The player that received the fewer number of red cards       ...

**端点**: `GET /v3/players/topassists`


**参数**:

- `league` (string) *必需*: The id of the league

- `season` (string) *必需*: The season of the league 4 characters Like 2020, 2021 ...



---


### `v3___top_red_cards`

Get the 20 players with the most red cards for a league or cup.  **How it is calculated:**         * 1 : The player that received the higher number of red cards         * 2 : The player that received the higher number of yellow cards         * 3 : The player that assists in the higher number of matches         * 4 : The player that played the fewer minutes  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.

**端点**: `GET /v3/players/topredcards`


**参数**:

- `league` (string) *必需*: The id of the league

- `season` (string) *必需*: The season of the league 4 characters Like 2020, 2021 ...



---


### `v3___players_seasons_by_player_id`

Get all available seasons for players statistics filtered by a player {id}.  **Update Frequency** : This endpoint is updated every day. **Recommended Calls** : 1 call per day.  **Use Cases** Get all seasons available for a player {id} `https://api-football-v1.p.rapidapi.com/v3/players/seasons?player=276`

**端点**: `GET /v3/players/seasons`


**参数**:

- `player` (string): Example value: 276



---


### `v3___timezone`

Get the list of available timezone to be used in the fixtures endpoint.  \u003e This endpoint does not require any parameters.   **Update Frequency** : This endpoint contains all the existing timezone, it is not updated. **Recommended Calls** : 1 call when you need.

**端点**: `GET /v3/timezone`



---


### `v3___top_scorers`

Get the 20 best players for a league or cup.  **How it is calculated:**         * 1 : The player that has scored the higher number of goals         * 2 : The player that has scored the fewer number of penalties         * 3 : The player that has delivered the higher number of goal assists         * 4 : The player that scored their goals in the higher number of matches         * 5 : The player that played the fewer minutes         * 6 : The player that plays for the team placed higher on the ta...

**端点**: `GET /v3/players/topscorers`


**参数**:

- `league` (string) *必需*: The id of the league

- `season` (string) *必需*: The season of the league 4 characters Like 2020, 2021 ...



---


### `v3___sidelined_by_coach_id`

Get all available sidelined for a player or a coach.  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get all from one {player} `https://api-football-v1.p.rapidapi.com/v3/sidelined?player=276`  Get all from several {player} ids `https://api-football-v1.p.rapidapi.com/v3/sidelined?players=276-278`  Get all from one {coach} `https://api-football-v1.p.rapidapi.com/v3/sidelined?coach=2`  Get all from several {coachs} ids...

**端点**: `GET /v3/sidelined`


**参数**:

- `player` (string): The id of the player

- `coach` (string): The id of the coach

- `players` (string): Maximum of 20 players ids id-id-id

- `coachs` (string): Maximum of 20 coachs ids id-id-id



---


### `v3___trophies_by_coach_id`

Get all available trophies for a player or a coach.  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get all trophies from one {player} `https://api-football-v1.p.rapidapi.com/v3/trophies?player=276`  Get all trophies from several {player} ids `https://api-football-v1.p.rapidapi.com/v3/trophies?players=276-278`  Get all trophies from one {coach} `https://api-football-v1.p.rapidapi.com/v3/trophies?coach=2`  Get all tr...

**端点**: `GET /v3/trophies`


**参数**:

- `player` (string): The id of the player

- `coach` (string): The id of the coach

- `players` (string): Maximum of 20 players ids id-id-id

- `coachs` (string): Maximum of 20 coachs ids id-id-id



---


### `v3___players_teams`

Returns the list of teams and seasons in which the player played during his career.  **This endpoint requires at least one parameter.** **Update Frequency** : This endpoint is updated several times a week.  **Recommended Calls** : 1 call per week.

**端点**: `GET /v3/players/teams`


**参数**:

- `player` (string) *必需*: The id of the player



---


### `v3___players_profiles`

$258

**端点**: `GET /v3/players/profiles`


**参数**:

- `player` (string): The id of the player

- `page` (string): Default: 1 Use for the pagination



---


### `v3___fixtures_rounds_with_dates`

Get the rounds for a league or a cup.  The `round` can be used in endpoint fixtures as filters     **Update Frequency** : This endpoint is updated every day. **Recommended Calls** : 1 call per day.  **Use Cases** Get all available rounds from one {league} \u0026 {season} `https://api-football-v1.p.rapidapi.com/v3/rounds?league=39\u0026season=2019`  // Get all available rounds from one {league} \u0026 {season} With the dates of each round get(\

**端点**: `GET /v3/fixtures/rounds`


**参数**:

- `league` (string) *必需*: The id of the league

- `season` (string) *必需*: The season of the league 4 characters Like 2020, 2021 ...

- `current` (string): Retrun the current round only Enum: true or false

- `dates` (string): Default: false Enum: "true" "false" Add the dates of each round in the response



---


### `v3___odds_by_league_id`

$25b

**端点**: `GET /v3/odds`


**参数**:

- `fixture` (string): The id of the fixture

- `league` (string): The id of the league

- `season` (string): The season of the league 4 characters Like 2020, 2021 ...

- `date` (string): A valid date

- `timezone` (string): A valid timezone from the endpoint Timezone

- `page` (string): Use for the pagination Default: 1

- `bookmaker` (string): The id of the bookmaker

- `bet` (string): The id of the bet



---


### `v3___predictions`

$25e

**端点**: `GET /v3/predictions`


**参数**:

- `fixture` (string) *必需*: The id of the fixture



---


### `v3___transfers_by_team_id`

Get all available transfers for players and teams  **Update Frequency** : This endpoint is updated several times a week. **Recommended Calls** : 1 call per day.  **Use Cases** Get all transfers from one {player} `https://api-football-v1.p.rapidapi.com/v3/transfers?player=35845`  Get all transfers from one {team} `https://api-football-v1.p.rapidapi.com/v3/transfers?team=463`

**端点**: `GET /v3/transfers`


**参数**:

- `player` (string): The id of the player

- `team` (string): The id of the team



---


### `v3___standings_by_league_id`

Get the standings for a league or a team.  Return a table of one or more rankings according to the league / cup.  Some competitions have several rankings in a year, group phase, opening ranking, closing ranking etc…  \u003e Most of the parameters of this endpoint can be used together.  **Update Frequency** : This endpoint is updated every hour. **Recommended Calls** : 1 call per hour for the leagues or teams who have at least one fixture in progress otherwise 1 call per day.  **Use Cases** Ge...

**端点**: `GET /v3/standings`


**参数**:

- `league` (string): The id of the league

- `season` (string) *必需*: The season of the league 4 characters Like 2020, 2021 ...

- `team` (string): The id of the team



---


### `v3___fixtures_events`

$261

**端点**: `GET /v3/fixtures/events`


**参数**:

- `fixture` (string) *必需*: The id of the fixture

- `team` (string): The id of the team

- `player` (string): The id of the player

- `type` (string): The event type Like Goal, Card ...



---


### `v3___teams_statistics`

**Update Frequency** : This endpoint is updated twice a day. **Recommended Calls** : 1 call per day for the teams who have at least one fixture during the day otherwise 1 call per week.  \u003e Here is an example of what can be achieved ![demo-teams-statistics](https://www.api-football.com/public/img/demo/demo-teams-statistics.png)  **Use Cases** Get all statistics for a {team} in a {league} \u0026 {season} `https://api-football-v1.p.rapidapi.com/v3/teams/statistics?league=39\u0026team=33\u00...

**端点**: `GET /v3/teams/statistics`


**参数**:

- `league` (string) *必需*: The id of the league

- `season` (string) *必需*: The season of the league 4 charactersLike 2020, 2021 ...

- `team` (string) *必需*: The id of the team

- `date` (string): The limit date



---



## 技术栈

- **传输协议**: stdio
- **HTTP 客户端**: httpx

## 开发

此服务器由 [API-to-MCP](https://github.com/BACH-AI-Tools/api-to-mcp) 工具自动生成。

版本: 1.0.0
