# Spotify-

# Spotify-
Using Spotify API to get Jay Z albulm name, release date, track, type, and album URI

Code
=
```
import requests
import json 

#Client ID and SECRET - USE YOUR OWN!
CLIENT_ID = 'Client ID Go Here'
CLIENT_SECRET = 'Client Secret Go Here'

AUTH_URL = 'https://accounts.spotify.com/api/token'

# POST
auth_response = requests.post(AUTH_URL, {
    'grant_type': 'client_credentials',
    'client_id': CLIENT_ID,
    'client_secret': CLIENT_SECRET,
})

# convert the response to JSON
auth_response_data = auth_response.json()

# save the access token
access_token = auth_response_data['access_token']

#creating the headers
headers = {
    'Authorization': 'Bearer {token}'.format(token=access_token)
}

# base URL of all Spotify API endpoints
BASE_URL = 'https://api.spotify.com/v1/'

#Jay Z ARTIST ID
artist_id = '3nFkdlSjzX9mRTtwJOzDYB'

# actual GET request with proper header
r = requests.get(BASE_URL + 'artists/' + artist_id  + '/albums', headers=headers)

data = r.json()

formatted_json = json.dumps(data, sort_keys=True, indent=10)
# print(formatted_json)
print('Album Name:', data['items'][0]['name'])
print('Release Date:', data['items'][0]['release_date'])
print('Track #:', data['items'][0]['total_tracks'])
print('Type:', data['items'][0]['type'])
print('Albulm URI:', data['items'][0]['uri'])


print()
print('Album Name:', data['items'][2]['name'])
print('Release Date:', data['items'][2]['release_date'])
print('Track #:', data['items'][2]['total_tracks'])
print('Type:', data['items'][2]['type'])
print('Albulm URI:', data['items'][2]['uri'])

```
Output
=

```
Album Name: 4:44
Release Date: 2017-07-07
Track #: 10
Type album
Albulm URI: spotify:album:7GoZNNb7Yl74fpk8Z6I2cv

Album Name: Magna Carta... Holy Grail
Release Date: 2013-07-04
Track #: 16
Type album
Albulm URI: spotify:album:0anlRE2dYlRqEKL1gj1WPq

```
