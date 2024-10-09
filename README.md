Natio Note-Taking CLI Application
Overview
This is a Python command-line interface (CLI) application for managing notes using MongoDB as the database. The app allows users to create, view, edit, and delete notes. It provides a simple way to store and organize notes with various commands for easy interaction.

Features
Add new notes
View all notes
Edit note titles and content
Delete specific notes or all notes
Search for a note by title
Display help with available commands
Requirements
Python 3.x
MongoDB server running on localhost at port 27017
Python packages:
pymongo
Installation
Install Python 3.x if it's not installed on your system.

Install MongoDB and ensure it's running on localhost:27017.

Install the required Python package using pip:

bash
Copy code
pip install pymongo
Clone or download this repository.

Usage
To use the application, run the Python script in your terminal. You can interact with the program by entering the commands listed below.

Available Commands
natio — Display help with available commands.
natio -a — Add a new note (will prompt for title and content).
natio -v — View all notes stored in the database.
natio -r — Remove a specific note (will prompt for the title).
natio -ra — Remove all notes (requires confirmation).
natio -s — Search for a note by title.
natio -ea — Edit both the title and content of a note.
natio -et — Edit the title of a note.
natio -ec — Edit the content of a note.
Example Commands
To add a new note:

bash
Copy code
natio -a
To view all notes:

bash
Copy code
natio -v
To remove a specific note:

bash
Copy code
natio -r
To search for a note by title:

bash
Copy code
natio -s
Notes Collection Structure
Each note in the MongoDB notes db collection contains:

title (string): The title of the note
content (string): The content of the note
License
This project is licensed under the MIT License.
