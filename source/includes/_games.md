# Games

Getting all games is the only supported method. To get a list of all the lists for a specific game, use a query filter on a `GET /lists` request.

## Get All Games

```javascript
const response = await fetch('https://api.loadorderlibrary.com/v1/games', {
	headers: {
		'Accept': 'application/json'
	}
});

console.log(response.json()); // logs the below response.
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
        }
    ]
}
```

This endpoint retrieves all lists.

### HTTP Request

`GET https://api.loadorderlibrary.com/v1/games`
