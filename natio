#!/usr/bin/env python3
from pymongo import MongoClient


client = MongoClient('localhost', 27017)
db = client['database']
notes_collection = db['notes db']

def user_choices():
    user = input("\n").lower().strip()
    return user

def typo_error():
    print("\nTypo error")

def changes_saved():
    print("\nChanges are saved")

def no_changes():
    print("\nNo changes were made")

def print_all_notes():
    for note in notes_collection.find():
        print(f"\ntitle: {note["title"]}")
        print("-----")
        print(f"content: {note["content"]}")
        print("-----")

def not_found():
    print("\nNote does not exist")

def empty_db():
    if notes_collection.count_documents({}) == 0:
        print("\nThese notes are empty, Do you know that?")
        return True
    
    return False

def title_found(title):
    return notes_collection.find_one({"title": title})

def update_title(old_title, new_title):
    notes_collection.update_one({"title": old_title},
                                {"$set": {"title": new_title}})

def update_content(title, new_cotent):
    notes_collection.update_one({"title": title},
                                       {"$set": {"content": new_cotent}})

def help_command():
    print("Type (natio -a) to add a note")
    print("Type (natio -v) to view all of the notes")
    print("Type (natio -r) to remove a note")
    print("Type (natio -ra) to remove all note")
    print("Type (natio -s) to search a note")
    print("Type (natio -ea) to edit a note as a whole")
    print("Type (natio -et) to edit a title of a note")
    print("Type (natio -ec) to edit a content of a note")

def add_note(storetd_notes):
        note_title = input("Type the note title: ").lower().strip()
        note_content = input("Type the content of the note: ").lower().strip()

        storetd_notes = {
                "title": note_title,
                "content": note_content
                }

        notes_collection.insert_one(storetd_notes)
        changes_saved()

def view_notes():
    if empty_db():
        pass
    else:
        print_all_notes()

def remove_note():
    if empty_db():
        pass
    else:
        removed_note_title = input("\nType the title of the note you want to remove: ").lower().strip()

        if title_found(removed_note_title):
            notes_collection.delete_one({"title": removed_note_title})
            changes_saved()

        else:
            not_found()

def remove_all_notes():
    if empty_db():
        pass

    else:
        is_sure = input("\nAre you sure; this will remove all the notes, Type (y) to processd, type (n) to undo: ").lower().strip()
        
        if is_sure == "y":
            notes_collection.delete_many({})
            changes_saved()
        elif is_sure == "n":
            no_changes()
        else:
            typo_error() 
            
def search_note():
    if empty_db():
        pass
    else:
        searched_note_title = input("\nType the title of the note you want to search: ").lower().strip()

        searched_note = title_found(searched_note_title)
        if searched_note:
            print(f"\ntitle: {searched_note["title"]}")
            print("")
            print(f"-----\ncontent: {searched_note["content"]}")
        else:
            not_found()

def edit_note():
    if empty_db():
        pass
    
    else:
        old_note_title = input("\nType the OLD title of the note: ").lower().strip()
  
        new_note_title = input("\nType the NEW title of the note: ").lower().strip()
        new_note_content = input("\nType the NEW content of the note: ").lower().strip()
        
        if title_found(old_note_title):
            update_title(old_note_title, new_note_title)
            update_content(new_note_title, new_note_content)
            changes_saved()
        else:
            not_found()

def edit_note_title():
    if empty_db():
        pass
    else:
        old_note_title = input("\nType the OLD title of the note: ").lower().strip() 
        new_note_title = input("\nType the NEW title of the note: ").lower().strip()

        if title_found(old_note_title):
            update_title(old_note_title, new_note_title)
            changes_saved()
        else:
            not_found()

def edit_note_content():
    if empty_db():
        pass
    else:
        current_title = input("\nType the title of the note: ").lower().strip()
        new_note_content = input("\nType the NEW content of the note: ").lower().strip()

        if title_found(current_title):
            update_content(current_title, new_note_content)
            changes_saved()
        else:
            not_found()

def natio(user):
    storetd_notes = {}
    
    if user == "natio":
        help_command()
    elif user == "natio -a":
        add_note(storetd_notes)
    elif user == "natio -v":
        view_notes()
    elif user == "natio -r":
        remove_note()
    elif user == "natio -ra":
        remove_all_notes()
    elif user == "natio -s":
        search_note()
    elif user == "natio -ea":
        edit_note()
    elif user == "natio -et":
        edit_note_title()
    elif user == "natio -ec":
        edit_note_content()
    
user = user_choices()

if __name__ == "__main__":
    natio(user)
