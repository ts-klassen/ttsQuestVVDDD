# Audio Status

The `audioStatusUrl` key in the response of the tts.quest VOICEVOX v3 API provides a URL to check the status of the conversion process.

## API Response
A GET request to the `audioStatusUrl` endpoint returns a JSON object with the following keys:

- `success`: A boolean indicating whether the request was successful or not.
- `isAudioReady`: A boolean indicating whether the audio file is ready for download or not.
- `isAudioError`: A boolean indicating whether an error occurred during the audio conversion process.
- `status`: A string indicating the current status of the conversion process.
- `updatedTime`: A long long int Unix timestamp representing the last time the status was updated.

## Status Codes
The audioStatusUrl endpoint may return the following status codes:

- `200 OK`: The request was successful, and the response body contains valid data.
- `404 Not Found`: The requested resource was not found.
- `5xx Server Error`: An unexpected error occurred while processing the request. This could be due to a problem with the API server or the load balancer.

## Response Description
- `success`: Set to `true` if the request was successful, `false` otherwise.
- `isAudioReady`: Set to `true` if the audio file is ready for download, `false` otherwise.
- `isAudioError`: Set to `true` if an error occurred during the audio conversion process, `false` otherwise.
- `status`: Possible values are `accepted`, `creating`, `wav file creation failed`, `mp3 file creation failed` and `done`.
- `updatedTime`: An Unix timestamp representing the last time the status was updated.
