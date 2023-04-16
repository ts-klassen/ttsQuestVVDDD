# TTS.Quest v3 API Key

Each API key has points, which will be reassigned every day. The points are used to limit the number of requests a client can make in a day. If a client exhausts their points, they will not be able to make further requests until their points are refreshed the following day.

## Endpoints
Every endpoint requires `key` as GET parameters. 
Can also be provided as POST using `content-type: application/x-www-form-urlencoded`.

### Check API Points Left

This endpoint allows clients to check the number of points they have left in their API key. Clients can use this information to plan their requests for the day.

**Endpoint:** `https://api.tts.quest/v3/keys/points`

```
{
    "success": bool
    "points": int
}
```

### Create Sub Keys

This endpoint allows clients to generate subkeys. Subkeys can be created to allow multiple users to access the same API key without sharing the primary key. Each subkey will have its own set of points that will be reassigned daily.

**Endpoint:** `https://api.tts.quest/v3/keys/generate`

Additionaly requires `points` and `seconds`. 
If npt provided or left empty, they will be it's maximum values.

```
{
    "success": bool
    "subkey": str
}
```

### Get PoW Mask

This endpoint allows clients to get a Proof of Work (PoW) mask. The PoW mask is used to upgrade api keys. Explained [here](/pow.md).

**Endpoint:** `https://api.tts.quest/v3/keys/masks`

```
{
    "success": bool
    "pows": [
        {
            mask: str
            points: int
            expire: long long int
        }
    ]
}
```

## Error Handling
The API will return error responses in JSON format with a status code indicating the error. The following error codes and messages will be returned:

- `400 Bad Request`: The request is invalid or missing required parameters, such as when the text or speaker parameter is missing or invalid.
- `403 Forbidden`: The API key is invalid or missing.
- `429 Too Many Requests`: The user has exceeded the rate limit for the API.
- `5xx Server Error`: An unexpected error occurred while processing the request. This could be due to a problem with the API server or the load balancer.
