# Project Contact Book

Contact = {}  # Dictionary to store contact names and phone numbers

# Function to display all contacts
def ShowFunction():
     print(Contact.items())  # (Optional/Debug) This prints all contact key-value pairs as a dict_items object
     print("Name \t Contact")  # Header for contact list
     for key in Contact:
         print("{} \t {}".format(key, Contact.get(key)))  # Format and print each contact name and number

# Infinite loop for menu options until user chooses to exit
while True:
     # Displaying the menu and taking user choice as input
     choice = int(input("1. Add New Contact \n"
                    "2. Search Contact  \n"
                    "3. Display Contact \n"
                    "4. Edit Contact \n"
                    "5. Delete Contact \n"
                    "6. Exit \n"
                    "Please Write Number Between 1-6: "))

     # Option 1: Add new contact
     if choice == 1:
         name = input("Add Your Contact Name: ")  # Get contact name from user
         phone = input("Add Your Phone Number: ")  # Get phone number from user
         Contact[name] = phone  # Store the name and phone in the dictionary

     # Option 2: Search for a contact
     elif choice == 2:
         ContactName = input("Search the Contact: ")  # Ask for contact name to search
         if ContactName in Contact:  # Check if the name exists
             print(ContactName, "Contact Number is:  ", Contact[ContactName])  # Show contact number
         else:
             print(" Not found the contact.")  # If name not found

     # Option 3: Display all contacts
     elif choice == 3:
         if not Contact:  # If the dictionary is empty
             print("Contact book is empty")
         else:
             ShowFunction()  # Call function to show all contacts

     # Option 4: Edit an existing contact
     elif choice == 4:
         EditContact = input("Edit Your Contact: ")  # Get name to edit
         if EditContact in Contact:  # If name exists
             phone = input("Change Your Number: ")  # Ask for new number
             Contact[EditContact] = phone  # Update the contact
             print("Contact Update Successfully ")
             ShowFunction()  # Show updated contact list
         else:
             print("Name is Not Found")  # If name doesn't exist

     # Option 5: Delete a contact
     elif choice == 5:
         Del_Contact = input("which Contact Do you want to delete?: ")  # Ask for contact to delete
         if Del_Contact in Contact:  # If name exists
             DeletedConfirm = input("Do you want to delete this contact [y/n]")  # Confirm deletion
             if DeletedConfirm == "y" or DeletedConfirm == "Y":  # If user confirms
                 Contact.pop(Del_Contact)  # Delete the contact
             ShowFunction()  # Show contact list after deletion
         else:
             print("The name is not found in the contact")  # If name doesn't exist

     # Option 6 or any other number: Exit the loop
     else:
         break  # Exit the program
