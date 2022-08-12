# Feature Request
### Application: Jamming
### Date: May 27, 2022
### Developer: Prince Ephraim Quarshie
### email: prince.quarshie@amalitech.org
OBJECTIVE

To implement a conditional modal window (a modal window is a graphical control element subordinate to an application's main window), to redirect a user to Spotify to connect their account before accessing the Jamming application.

### BACKGROUND 	

Currently, when a user first use Jamming, they enter a search term, are then sent to Spotify to log in to their account, and then are redirected to Jamming. Unfortunately, their search term is lost when they are redirected back to Jamming from Spotify. 
In this feature request, I propose the following application updates:
*	Create a full screen modal window that only appears if the user has not connected Jamming to their Spotify account.
*	This modal will have a button that says CONNECT TO SPOTIFY
*	The user is sent to Spotify to sign in, and then is redirected back to Jamming to create their playlists
*	All Jamming users that authenticate with Spotify will have a check mark at the top of the app that says CONNECTED TO SPOTIFY.
*	A new Footer component will also be created to protect the intellectual rights of both jamming and Codecademy.

### TECHNICAL DESIGN
Design Updates:
The new Modal component will contain all of the UI features of the modal window. Its render method will contain a JSX section container with a welcome message and button to connect to Spotify. Above the return statement, a conditional statement will return “null” if this.props.loggedInStatus === true. This will ensure that the user is only prompted to authorize with Spotify using the Modal on their initial log in. 
Modal’s button property onClick will call the Spotify.getAccessToken() function to authorize Jamming to access their Spotify account. After successful authorization, the user is sent back to Jamming to search songs and the Modal box will disappear when App’s loggedIn state is set to “true.”
The new Footer component will contain logic for the current year for the copyright statement. Copyright will cover Jamming and Codecademy.  This component will render at the very bottom of App’s render() method.
1.	Features:

Below Is a list of the website’s features used in the Application: 

*	Spotify Login — the first time a user searches for a song, album, or artist, Spotify will ask them to log in or set up a new account. You will need to follow the steps in the Spotify Developer Guide https://developer.spotify.com/web-api/tutorial/ to register your application.

*	Search by Song, Album, or Artist — a user can type the name of a song, artist, or album into the search bar and click the SEARCH button. The app will request song data about the user's input from the Spotify library (find Spotify endpoints here https://developer.spotify.com/web-api/endpoint-reference/ ).

*	Populate Results List — Jamming displays the list of returned tracks from the user's query.

*	Add Song to a Custom Playlist — users can add a track to their playlist by selecting a + sign on the right side of the track's display container.

*	Remove Song from Custom Playlist — users can remove a track from their playlist by selecting a - sign on the right side of the track's display container.

*	Change Playlist Title — users can change the title of their custom playlist.
*	Save Playlist to Account — users can save their custom playlist by clicking a button called SAVE TO SPOTIFY.

  The below are components being rendered in the App.

     App.js 
+	Playlist.js
+	SearchBar.js 
+	SearchResults.js 
+	Track.js
+	TrackList.js 
+	Spotify.js 
+	index.js

2.	Requirements
 How the application handle state:
State will be handled by the App.js component. State flow SearchResults:
*	The Spotify.js component will be invoked by App.js and the information will be stated in the same
*	App.js "props" the information to SearchResults.js
*	SearchResults.js "props" the information to TrackList.js
*	TrackList.js "props" the information to Track.js
State flow Playlist:
*	The Spotify.js component will be invoked by App.js and the information will be stated in the same
*	App.js "props" the information to Playlist.js
*	Playlist.js "props" the information to TrackList.js
*	TrackList.js "props" the information to Track.js



Methods used in the Application:

+	App.js 
+	.addTrack
+	.removeTrack
+	.updatePlaylistName
+	.savePlaylist
+	.search
+	Playlist.js 
+	.handleNameChange.js
+	SearchBar.js
+	.search.js
+	handleTermChange.js
+	SearchResults.js
+	Track.js 
+	.addTrack
+	.removeTrack
+	.renderAction
+	Tracklist.js 
+	Spotify.js 
+	.getAccessToken
+	.search
+	.savePlaylist
 
Figure 1. mock up design of Jamming App.

### CAVEATS

Currently, after a user type in a search query, they are sent to Spotify to authorize their account, and are then sent back to resubmit their query. The goal of this update, then, is to eliminate the need to type the same search query more than once. To achieve this goal, a modal blocks the user from searching until they have signed in.
A simpler solution would be to save the search query as a prop, state, or cookie and then return the value to the search field after a user returns to the Jamming application. However, the method proposed in this feature request creates a more intuitive authorization flow. 


