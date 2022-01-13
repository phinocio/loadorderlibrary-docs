# Games

Getting all games is the only supported method. To get a list of all the lists for a specific game, use a query filter on a `GET /lists` request.

## Get All Games

```javascript
const response = await fetch('https://api.loadorderlibrary.com/v1/games', {
	headers: {
		'Accept': 'application/json'
	}
});

console.log(await response.json()); // logs the below response.
```

> The above command returns JSON structured like this

```json
{
    "data": [
        {
            "id": 1,
            "name": "TESIII Morrowind"
        },
        {
            "id": 2,
            "name": "TESIV Oblivion"
        },
        {
            "id": 3,
            "name": "TESV Skyrim LE"
        },
        {
            "id": 4,
            "name": "TESV Skyrim SE"
        },
        {
            "id": 5,
            "name": "TESV Skyrim VR"
        },
        {
            "id": 6,
            "name": "Fallout 3"
        },
        {
            "id": 7,
            "name": "Fallout New Vegas"
        },
        {
            "id": 8,
            "name": "Fallout 4"
        },
        {
            "id": 9,
            "name": "Fallout 4 VR"
        },
        {
            "id": 10,
            "name": "Tale of Two Wastelands"
        },
		...
    ]
}
```

This endpoint retrieves all games.

### HTTP Request

`GET https://api.loadorderlibrary.com/v1/games`

## List of Games
ID | Name 
-- | --
1  | TESIII Morrowind
2  | TESIV Oblivion
3  | TESV Skyrim LE
4  | TESV Skyrim SE
5  | TESV Skyrim VR
6  | Fallout 3
7  | Fallout New Vegas
8  | Fallout 4
9  | Fallout 4 VR
10 | Tale of Two Wastelands
11 | Cyberpunk 2077
12 | Darkest Dungeon
13 | Dark Messiah of Might & Magic
14 | Dark Souls
15 | Dragon Age II
16 | Dragon Age: Origins
17 | Dungeon Siege II
18 | Kerbal Space Program
19 | Mirror's Edge
21 | Mount & Blade II: Bannerlord
22 | No Man's Sky
23 | STALKER Anomaly
24 | Stardew Valley
25 | The Binding of Isaac: Rebirth
26 | The Witcher 3: Wild Hunt
27 | Zeus and Poseidon
