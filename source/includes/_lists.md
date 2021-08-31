# Lists
	All responses with multiple lists are return paginated with 14 results per page and include relations to `game`, `author`, and `files`. If a list does not have an author (was uploaded anonymously), the author field in the response will be `null`.

## Get All Lists

```javascript
const response = await fetch('https://api.loadorderlibrary.com/v1/lists', {
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

This will return all `TESIII Morrowind` lists by `Phinocio` ordered by the newest one first.

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
filter[author] | null | If supplied with an author's name, returns all public lists for that author.
filter[game] | null | If if supplied with the name of a game, returns all lists for that game.
sort | newest first | Takes either `updated` or `created`. Prepend `-` before either to reverse the order. `created` would return the oldest created first for example.

<aside class="notice">
All parameters can be used alone or together.
</aside>

## Get a Specific List

```javascript
const response = await fetch('https://api.loadorderlibrary.com/v1/lists/my-new-list-again-2', {
	headers: {
		'Accept': 'application/json'
	}
});

console.log(await response.json()); // logs the below response.
```

> The above command returns JSON structured like this

```json
{
    "data": {
        "name": "My New List! Again",
        "version": null,
        "slug": "my-new-list-again-2",
        "url": "https://loadorderlibrary.com/lists/my-new-list-again-2",
        "private": 0,
        "created": 1625937809,
        "updated": 1625937809,
        "author": null,
        "game": {
            "id": 1,
            "name": "TESIII Morrowind"
        },
        "files": [
            {
                "name": "04ff9e544df36ef076bd26e8f42aeee4-plugins.txt",
                "clean_name": "plugins.txt",
                "bytes": 6404,
                "created": 1624752048,
                "updated": 1624752048
            },
            {
                "name": "00acfcec29588e25041c76307b860016-modlist.txt",
                "clean_name": "modlist.txt",
                "bytes": 8420,
                "created": 1624752076,
                "updated": 1624752076
            },
            {
                "name": "9f87e14d8aa888362776f88f995d08cd-Skyrim.ini",
                "clean_name": "Skyrim.ini",
                "bytes": 3117,
                "created": 1624752076,
                "updated": 1624752076
            }
        ]
    }
}
```

This endpoint retrieves a specific list via the slug.


### HTTP Request

`GET https://api.loadorderlibrary.com/v1/lists/<slug>`

### URL Parameters

Parameter | Description
--------- | -----------
slug | The slug of the list you want to retrieve.

## Create a List

```javascript
const formData = new FormData();
const files = document.querySelector('input[type="file"][multiple]');

formData.append('name', 'My New List');
formData.append('game_id', 1);
formData.append('is_private', 0); // optional, defaults to false.
formData.append('expires_at', '24h'); // optional, defaults to 24h for anonymous lists.

for (let i = 0; i < files.files.length; i++) {
  formData.append('files[]', files.files[i]);
}

const response = await fetch('https://api.loadorderlibrary.com/v1/lists', {
  method: 'POST',
  body: formData,
  headers: {
	  'Accept': 'application/json'
  }
});

console.log(await response.json()); // logs the below response.
```

> The above command returns JSON structured like this

```json
{
    "data": {
        "name": "My New List",
        "version": null,
        "slug": "my-new-list",
        "url": "https://testing.loadorderlibrary.com/lists/my-new-list",
        "private": false,
        "expires": 1630524048,
        "created": 1630437648,
        "updated": 1630437648,
        "author": null,
        "game": {
            "id": 1,
            "name": "TESIII Morrowind"
        },
        "files": [
            {
                "name": "9f87e14d8aa888362776f88f995d08cd-Skyrim.ini",
                "clean_name": "Skyrim.ini",
                "bytes": 3117,
                "created": 1630437398,
                "updated": 1630437398
            },
            {
                "name": "00acfcec29588e25041c76307b860016-modlist.txt",
                "clean_name": "modlist.txt",
                "bytes": 8420,
                "created": 1630437398,
                "updated": 1630437398
            },
            {
                "name": "04ff9e544df36ef076bd26e8f42aeee4-plugins.txt",
                "clean_name": "plugins.txt",
                "bytes": 6404,
                "created": 1630437398,
                "updated": 1630437398
            }
        ],
        "links": {
            "url": "https://testing.loadorderlibrary.com/lists/my-new-list",
            "self": "http://api.loadorderlibrary.localhost/v1/lists/my-new-list"
        }
    }
}
```

This endpoint creates a new list.


### HTTP Request

`POST https://api.loadorderlibrary.com/v1/lists`

### Body Data

Parameter | Required? | Description
--------- | ------- | -----------
name | required | The name for the list.
version | optional | The version for the list. Defaults to `null` when not provided.
game_id | required | The id of the game the list is for.
is_private | optional | Whether the list is private or not. Defaults to `false` when not provided.
files[] | required | The files for the list.
expires_at | optional | When the list will expire. Accepted options are strings of `3h`, `24h`, `3d`, `1w`, and `perm`. Defaults to `24h` when `null` is provided.