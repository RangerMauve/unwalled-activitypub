# unwalled-activitypub
An [ActivityPub](https://activitypub.rocks/) server that automagically translates between the [unwalled.garden](https://unwalled.garden/) spec

## API

### `GET /:dat_key/`

Get the `title` and `description` from `dat.json` and generate an ActivityPub [Actor](https://www.w3.org/TR/activitypub/#actor-objects)

`:dat_key` can either be a key, or the domain name to resolve to a key.

### `GET /:dat_key/following.json`

Iterate through contents of [/data/follows.json](https://github.com/beakerbrowser/unwalled.garden/blob/master/follows.json),
determine if the scheme is `dat` or `https` and resolve to the correct `Actor` type. Return a [Collection](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-collection).

### `GET /:dat_key/liked.json`

Iterate through [/data/votes/](https://github.com/beakerbrowser/unwalled.garden#the-votes-folder), generate an [OrderedCollection](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-orderedcollection) of [Likes](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like). Figure out how to handle liking `https` URLs.

### `GET /:dat_key/inbox.json`

Generate a `dat://` URL for this account if one doesn't exist yet. Return it.

### `POST /:dat_key/inbox.json`

Accept a post
