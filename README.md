# Author: Nieco Carty
# Date Created: 04/12/2023
# Course: ITT103
# Purpose: This program implements a bus reservation system allowing users to select seats in different classes (First, Business, Economy).
#          It prompts users to choose a class, select a seat type (aisle or window), and reserves the seat if available.

# Define the number of seats in each class on each bus
FIRST_CLASS_SEATS = 27
BUSINESS_CLASS_SEATS = 38
ECONOMY_CLASS_SEATS = 56

# Create a two-dimensional array to represent the seats
seats = [[0] * FIRST_CLASS_SEATS, [0] * BUSINESS_CLASS_SEATS, [0] * ECONOMY_CLASS_SEATS]

while True:
    # Prompt the user for the desired class of bus
    print("\Welcome to the bus reservation system!")
    print("Please select a class: First (F/f), Business (B/b), or Economy (E/e)")
    print("You can also Quit (Q/q) or Cancel at any time.")

    # Read the class of bus chosen by the user
    class_of_bus = input("Enter your choice: ").upper()

    # Check if the user wants to quit or cancel
    if class_of_bus == "Q":
        print("Exiting the reservation system. Goodbye!")
        break

    # Check if the chosen class is valid
    if class_of_bus in ["F", "B", "E"]:
        # Convert class_of_bus to index for seats array
        class_index = {"F": 0, "B": 1, "E": 2}[class_of_bus]

        print(f"Please select a seat in {class_of_bus} Class:")
        row_number = int(input(f"Enter the row number (1-{FIRST_CLASS_SEATS if class_of_bus == 'F' else BUSINESS_CLASS_SEATS if class_of_bus == 'B' else ECONOMY_CLASS_SEATS}): "))
        seat_type = input("Enter the seat type: Aisle (A/a), Window (W/w), or Cancel (C/c): ").upper()

        if seat_type in ["A", "W"]:
            if seats[class_index][row_number - 1] == 0:
                seats[class_index][row_number - 1] = 1
                print(f"{('Aisle' if seat_type == 'A' else 'Window')} seat in row {row_number} has been reserved.")
                continue  # Continue program if seat reserved successfully
            else:
                print(f"Sorry, the {('aisle' if seat_type == 'A' else 'window')} seat in row {row_number} has already been reserved. Please choose another seat.")
        elif seat_type == "C":
            print("Reservation canceled.")
        else:
            print("Invalid seat type. Please enter 'A', 'W', or 'C'.")
    else:
        print("Invalid choice. Please select from 'F', 'B', 'E', or 'Q'.")
