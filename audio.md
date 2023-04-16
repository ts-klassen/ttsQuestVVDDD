# Audio URLs
The API will respond with links to WAV and MP3 files of the converted speech. The URLs will look something like the following:

WAV: `https://audioX.tts.quest/v1/download/{audio_id}.wav`

MP3: `https://audioX.tts.quest/v1/download/{audio_id}.mp3`

If the audio file exists, the server will respond with an HTTP status code of 200 and the corresponding audio. 
If the audio file does not exist, the server will respond with an HTTP status code of 404.

Where X in audioX can be a number between 1 and the maximum number of available audio servers. 

Note that the domain and audio_id are included in the wavDownloadUrl and mp3DownloadUrl keys in the response body of the API. These links may not be immediately available depending on the processing status of the audio.
