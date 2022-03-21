# Playlist Pair API

Playlist Pair is a project I wanted to do to solve the problem of people not being able to share playlists when they have different music services. Now, with this project, users are able to sync up their gym, work, etc. type of playlists with their friends that use another platform.

An alternative way of using the project is for when you are switching services yourself. If you decide to go from Spotify to Apple, or vice-versa, then you can use this project to move each of your playlists with ease.

Playlist Pair is accessible at playlistpair.com

## Running the website locally

Code for the backend of the Music Connect Project


To spin up development server:
- vagrant up (wait for it to finish running)
- vagrant ssh (to connect to the vagrant server on virtual box)
- cd /vagrant (to move into the directory that is synced up with our local machine project directory)
- python -m venv ~/env (to create a python virtual env so it won't affect your local machine | important incase you need to respin up the vagrant server)
    - "~/" is specified so the virtual environment is created on the home directory of the vagrant folder as opposed to the local directory of our computer
    - this only needs be run once when creating the virtual environment
- source ~/env/bin/activate (to activate the python virtual environment)
    - deactive (when you want to deactivate the python virtual environment)
- pip install -r requirements.txt (to install the packages in the requirements.txt file)
- python manage.py runserver 0.0.0.0:8000
    - '0.0.0.0' makes the server accessible on all network adapters on our server
    - ':8000' is for port 8000
    - ctrl-c (stops the server)
- python ./manage.py qcluster
    - this is to run the scheduler

- python manage.py makemigrations
- python manage.py migrate
- python manage.py createsuperuser


# When creating project

- django-admin.py startproject playlist_connect_project .
- python manage.py startapp playlist_connect_api
- enable new app in settings.py in playlist_connect_project
    - add 'rest_framework' to INSTALLED_APPS
    - add 'rest_framework.authtoken'
    - add {new_app_name}
    - add trailing comma ',' at the end of each line


# heroku

- heroku ps:scale worker=1
    - to run the scheduler because it doesn't run it automatically
- heroku logs --tail
    - to read the logs for checking errors and proccesses, etc.
