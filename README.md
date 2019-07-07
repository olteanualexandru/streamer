# Streamer

This project allows users to view, create and edit streams.
Every user can broadcast to their stream using OBS Software and the stream 
will be available for all users to see.


## Client

I built this project during the days I was learning React & Redux, so my main
focus was on the client part. This is a pretty basic-level project, it's great
for learning or as a starting point for a different project.

Key concepts used in this project:
* Fundamental React & Redux concepts
* React Portals
* React Ref System
* Redux Form
* Basic CRUD operations
* And more...


## API Server

Because my focus was on the React & Redux part, I didn't spend much time
developing a backend server. I used the `json-server` library to generate it,
so the data is available in the `db.json` file. You can send basic requests 
to this server `(POST, GET, PUT, PATCH, DELETE)` and it will respond 
accordingly.

A major improvement will be to build the backend yourself, but like I said,
I just wanted to learn React & Redux, so I didn't spend much time on the 
backend side of things.


## RTMP Server

This server is responsible for the streaming part of the application.
I used the `node-media-server` library, basically all you need to know is that
the OBS Software from your computer is sending data to this server through one
port, and the client side of this app is requesting the same data through a
different port. Because this wasn't the main focus of the project, it's using
the `flv` encoding.
 
You can start streaming from your local machine using OBS software. How do 
you do that? It's pretty straight forward actually, after you installed OBS,
go to `Settings -> Stream`, open the `Service` selector and choose `Custom`,
add this server `rtmp://localhost/live` and the `Stream key`. The stream key 
is the id of the stream you want to broadcast to. If you don't know how to
find the id, you can open `api-server/db.json` (remember, this is acting
like our database).

If you're having trouble with this, you can check the documentation of OBS
and figure out what's wrong yourself.


## Setup

Before we start with the setup, it's important to know that this project 
is using Google's OAuth API. Every user can login directly with their
Google account, so it's essential you configure this in order for the
login system to work. All you need to do is navigate to 
https://console.cloud.google.com, create a project and create the credentials
for the required API (OAuth 2.0 API). After you create the credentials, 
you will get your client id. The next step is to open 
`client/src/components/GoogleAuth.js` and replace `YOUR_CLIENT_ID` with your
actual client id.

Good, now that this is taken care of, we can build and start the app.
You need to open 3 different terminal windows, navigate to each server
(api-server, client and rtmp-server) and run this following commands:

#### `npm install`

This installs all the required dependencies.

#### `npm start`

This starts the server. It's important to let the script run foreach server.


## Examples

Unlogged list:
![Unlogged list](./examples/unlogged_list.png?raw=true "Unlogged list")

Logged list:
![Logged list](./examples/logged_list.png?raw=true "Logged list")

Create stream:
![Create stream](./examples/create_stream.png?raw=true "Create stream")

Edit stream:
![Edit stream](./examples/edit_stream.png?raw=true "Edit stream")

Delete stream:
![Delete stream](./examples/delete_stream.png?raw=true "Delete stream")

View stream:
![View stream](./examples/view_stream.png?raw=true "View stream")

OBS software:
![OBS software](./examples/obs_software.png?raw=true "OBS software")
