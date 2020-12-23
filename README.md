# AddressBook-Python
import sys

sys.path.insert(0, 'GUI')

import tkinter as Tk
import db
import new


def get_contact(contact):
   
    entry = []

    try:
        if contact.split()[1]:
            entry.append(contact.split()[0])
            entry.append(contact.split()[1])
    except:
        entry.append('')
        entry.append(contact.split()[0])

    for row in db.get_entry(db.get_id(entry)):
        return row


def add_contact(contact):
   
    db.insert_entry(contact)


def remove_contact(contact):
   
    entry = []
    try:
        entry.append(contact.split()[0])
    except:
        entry.append('')

    try:
        entry.append(contact.split()[1])
    except:
        entry.append('')

    db.delete_entry(db.get_id(entry))


def edit_contact(entry_id, contact):
   
    db.edit_entry(entry_id, contact)


def search(search_string, sort):
   
    return db.search_entry(search_string, sort)


if __name__ == "__main__":
    root = Tk.Tk()
    new.New_AddBookWindow(root)
    root.mainloop()
