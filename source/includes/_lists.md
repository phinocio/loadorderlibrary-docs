# Lists
	All lists return paginated with 14 results per page and include relations to `game`, `author`, and `files`. If a list does not have an author (was uploaded anonymously), the author field in the response will be `null`.
	
<aside class="notice">
	Please send all requests with an <code>Accept: application/json</code> header.
</aside>
## Get All Lists

```javascript
const response = await fetch('https://api.loadorderlibrary.com/v1/lists', {
	headers: {
		'Accepts': 'application/json'
	}
});

console.log(response.json()); // logs the below response.
```

> The above command returns JSON structured like this

```json
{
    "data": [
        {
            "name": "A Third Morrowind List!",
            "version": "2.69.0",
            "slug": "a-third-morrowind-list",
            "url": "https://loadorderlibrary.com/lists/a-third-morrowind-list",
            "private": 0,
            "created": 1625604170,
            "updated": 1625604170,
            "author": {
                "name": "Phinocio"
            },
            "game": {
                "id": 1,
                "name": "TESIII Morrowind"
            },
            "files": [
                {
                    "name": "f8456ddcaf77ee434325eeda2af6e032-loadorder.txt",
                    "clean_name": "loadorder.txt",
                    "bytes": 3341,
                    "created": 1624752076,
                    "updated": 1624752076
                }
            ]
        },
        // more lists
    ],
    "links": {
        "first": "http://api.loadorderlibrary.localhost/v1/lists?filter%5Bauthor%5D=phinocio&filter%5Bgame%5D=TESIII%20MoRRowind&sort=-created&page=1",
        "last": "http://api.loadorderlibrary.localhost/v1/lists?filter%5Bauthor%5D=phinocio&filter%5Bgame%5D=TESIII%20MoRRowind&sort=-created&page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "http://api.loadorderlibrary.localhost/v1/lists?filter%5Bauthor%5D=phinocio&filter%5Bgame%5D=TESIII%20MoRRowind&sort=-created&page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "http://api.loadorderlibrary.localhost/v1/lists",
        "per_page": 14,
        "to": 3,
        "total": 3
    }
}
```

This endpoint retrieves all lists.

### HTTP Request

`GET https://api.loadorderlibrary.com/v1/lists`

### Example With All Params

`GET http://api.loadorderlibrary.com/v1/lists?filter[author]=phinocio&filter[game]=TESIII Morrowind&sort=-created`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
filter[author] | null | If supplied with an author's name, returns all public lists for that author.
filter[game] | null | If if supplied with the name of a game, returns all lists for that game.
sort | null | Takes either `updated` or `created`. Prepend `-` before either to reverse the order. `-created` would return the newest created first for example.

<aside class="notice">
All parameters can be used alone or together.
</aside>

## Get a Specific List

```javascript
const response = await fetch('https://api.loadorderlibrary.com/v1/lists/a-third-morrowind-list', {
	headers: {
		'Accepts': 'application/json'
	}
});

console.log(response.json()); // logs the below response.
```

> The above command returns JSON structured like this

```json
{
    json response
}
```

This endpoint retrieves a specific list via the slug.


### HTTP Request

`GET https://api.loadorderlibrary.com/v1/lists/<slug>`

### URL Parameters

Parameter | Description
--------- | -----------
slug | The slug of the list you want to retrieve.