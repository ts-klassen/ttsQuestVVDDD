# ttsQuestVVDDD
Detailed Design Document of tts.quest voicevox v3 api

## tts.quest VOICEVOX v3 API
This document provides a detailed design of a Text-to-Speech (TTS) API, which will convert text into speech using pre-defined voices. The API endpoint will be `https://api.tts.quest/v3/voicevox/synthesis`, which will accept text, speaker, and key as parameters. The response will be in JSON format, including links to WAV and MP3 files. Additionally, the response will include a link to check the status of the conversion process.

## API Endpoint
The API endpoint is `https://api.tts.quest/v3/voicevox/synthesis`. It accepts GET or POST requests with the following parameters:

- `text`: A string containing the text to be converted to speech.
- `speaker`: An integer representing the speaker to be used for the conversion. The integer should be a valid ID for one of the pre-defined speakers available in the API.
- `key`: A string containing the API key required for authentication purposes.

If using POST method, `content-type` must be `application/x-www-form-urlencoded`.

## Request Parameters

### text
The `text` parameter is a required parameter that specifies the text to be converted to speech. The maximum length of the `text` parameter is 5000 characters.

### speaker
The `speaker` parameter is a optional parameter that specifies the speaker to be used for the conversion. The value of the `speaker` parameter should be an integer, representing the ID of the pre-defined speaker to be used for the conversion. The default is 0.

### key
The `key` parameter is a required parameter that specifies the API key required for authentication purposes. The `key` parameter should be a string.

## Response Format
The API will respond with an HTTP status code and a response body in JSON format. The response body will include the following keys:

```
{
"success": bool,
"wavDownloadUrl": str,
"mp3DownloadUrl": str,
"audioStatusUrl": str,
"credit": str
}
```

### success
The `success` key is a boolean indicating whether the request was successful or not. This key will be set to `true` when the HTTP status code is 200 and the response body contains valid data. Otherwise, it will be set to `false`.

### wavDownloadUrl
The `wavDownloadUrl` key is a string containing a URL to the WAV file of the converted speech. This URL may not be immediately available depending on the processing status. Explained [here](/audio.md).

### mp3DownloadUrl
The `mp3DownloadUrl` key is a string containing a URL to the MP3 file of the converted speech. This URL may not be immediately available depending on the processing status. Explained [here](/audio.md).

### audioStatusUrl
The `audioStatusUrl` key is a string containing a URL to check the status of the conversion process. The `audioStatusUrl` can be used to check the current status of the conversion process. Explained [here](/status.md).

### credit
The `credit` key is a string containing the name or other identifier of the speaker. This can be useful when using multiple speakers or when the speaker is important for the use case. The `credit` key is required to be displayed when the converted speech is used publicly. Terms and conditions of VOICEVOX and its voice characters apply.

## Error Handling
The API will return error responses in JSON format with a status code indicating the error. The following error codes and messages will be returned:

- `400 Bad Request`: The request is invalid or missing required parameters, such as when the text or speaker parameter is missing or invalid.
- `403 Forbidden`: The API key is invalid or missing.
- `413 Payload Too Large`: The request is too large, such as when the text parameter is too long.
- `429 Too Many Requests`: The user has exceeded the rate limit for the API.
- `5xx Server Error`: An unexpected error occurred while processing the request. This could be due to a problem with the API server or the load balancer.

## Encoding
The API will support UTF-8 encoding for text inputs.

## Supported Speakers
The supported speakers for the Voicevox API can be obtained by sending a GET request to the endpoint `https://api.tts.quest/v3/voicevox/speakers`. The response will be a JSON object that contains information about each speaker, including their ID and name. Explained [here](/speakers.md).

## Rate Limiting
Each API key has points. Explained [here](/apikey.md).
