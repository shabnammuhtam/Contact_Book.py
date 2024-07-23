{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "06294a69-b60c-4b13-9a61-45750a30a657",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Contact Book\n",
      "1. Add Contact\n",
      "2. View Contacts\n",
      "3. Search Contacts\n",
      "4. Exit\n"
     ]
    }
   ],
   "source": [
    "import os\n",
    "\n",
    "# File path for the contacts file\n",
    "file_path = 'contacts.txt'\n",
    "\n",
    "# Function to add a new contact\n",
    "def add_contact():\n",
    "    name = input(\"Enter contact name: \")\n",
    "    phone = input(\"Enter phone number: \")\n",
    "    email = input(\"Enter email address: \")\n",
    "    \n",
    "    with open(file_path, 'a') as file:\n",
    "        file.write(f\"{name},{phone},{email}\\n\")\n",
    "    \n",
    "    print(\"Contact added successfully!\")\n",
    "\n",
    "# Function to view all contacts\n",
    "def view_contacts():\n",
    "    if not os.path.exists(file_path):\n",
    "        print(\"No contacts found.\")\n",
    "        return\n",
    "    \n",
    "    with open(file_path, 'r') as file:\n",
    "        contacts = file.readlines()\n",
    "    \n",
    "    if not contacts:\n",
    "        print(\"No contacts available.\")\n",
    "        return\n",
    "    \n",
    "    print(\"\\nContact List:\")\n",
    "    for contact in contacts:\n",
    "        name, phone, email = contact.strip().split(',')\n",
    "        print(f\"Name: {name}, Phone: {phone}, Email: {email}\")\n",
    "\n",
    "# Function to search contacts by name\n",
    "def search_contacts():\n",
    "    name_to_search = input(\"Enter name to search: \")\n",
    "    \n",
    "    if not os.path.exists(file_path):\n",
    "        print(\"No contacts found.\")\n",
    "        return\n",
    "    \n",
    "    with open(file_path, 'r') as file:\n",
    "        contacts = file.readlines()\n",
    "    \n",
    "    found = False\n",
    "    print(\"\\nSearch Results:\")\n",
    "    for contact in contacts:\n",
    "        name, phone, email = contact.strip().split(',')\n",
    "        if name_to_search.lower() in name.lower():\n",
    "            print(f\"Name: {name}, Phone: {phone}, Email: {email}\")\n",
    "            found = True\n",
    "    \n",
    "    if not found:\n",
    "        print(\"No contacts found with that name.\")\n",
    "\n",
    "# Main function to run the project\n",
    "def main():\n",
    "    while True:\n",
    "        print(\"\\nContact Book\")\n",
    "        print(\"1. Add Contact\")\n",
    "        print(\"2. View Contacts\")\n",
    "        print(\"3. Search Contacts\")\n",
    "        print(\"4. Exit\")\n",
    "        \n",
    "        choice = input(\"Choose an option: \")\n",
    "        \n",
    "        if choice == '1':\n",
    "            add_contact()\n",
    "        elif choice == '2':\n",
    "            view_contacts()\n",
    "        elif choice == '3':\n",
    "            search_contacts()\n",
    "        elif choice == '4':\n",
    "            break\n",
    "        else:\n",
    "            print(\"Invalid choice. Please try again.\")\n",
    "\n",
    "# Run the main function\n",
    "if __name__ == \"__main__\":\n",
    "    main()\n"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.11.7"
  },
  "widgets": {
   "application/vnd.jupyter.widget-state+json": {
    "state": {},
    "version_major": 2,
    "version_minor": 0
   }
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
