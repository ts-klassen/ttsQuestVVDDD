# Supported Speakers
The Voicevox API supports multiple speakers, each with its own unique ID and name. 
The available speakers and their respective IDs can be obtained by sending a GET request to the endpoint `https://api.tts.quest/v3/voicevox/speakers`.

## Request Parameters
### key
The `key` parameter is a required parameter that specifies the API key required for authentication purposes. 
The key parameter should be a string.

## Response
The response body is a JSON object that includes an array of each speaker object, containing an `id` and a `name` field.
The order of array may not be sorted by `id` nor `name`.
```
{
    "success": true,
    "speakers": [
        {
            "id": int,
            "name": str,
        }
    ]
}
```
