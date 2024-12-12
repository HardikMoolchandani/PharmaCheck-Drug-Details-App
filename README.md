# PharmaCheck-Drug-Details-App
import tkinter as tk
from tkinter import messagebox

# List of drugs as provided
drugs = [
    {"Drug Name": "Paracetamol", "Disease": "Fever", "Price": 2.5, "Side Effect": "Liver damage"},
    {"Drug Name": "Ibuprofen", "Disease": "Pain Relief", "Price": 3.0, "Side Effect": "Stomach ulcers"},
    {"Drug Name": "Amoxicillin", "Disease": "Bacterial Infection", "Price": 5.0, "Side Effect": "Allergic reactions"},
    {"Drug Name": "Cetirizine", "Disease": "Allergy", "Price": 2.0, "Side Effect": "Drowsiness"},
    {"Drug Name": "Omeprazole", "Disease": "Acid Reflux", "Price": 4.5, "Side Effect": "Bone fractures"},
    {"Drug Name": "Metformin", "Disease": "Diabetes", "Price": 3.5, "Side Effect": "Lactic acidosis"},
    {"Drug Name": "Aspirin", "Disease": "Blood Thinner", "Price": 1.5, "Side Effect": "Internal bleeding"},
    {"Drug Name": "Salbutamol", "Disease": "Asthma", "Price": 4.0, "Side Effect": "Rapid heart rate"},
    {"Drug Name": "Atorvastatin", "Disease": "High Cholesterol", "Price": 5.5, "Side Effect": "Muscle damage"},
    {"Drug Name": "Clonazepam", "Disease": "Seizures", "Price": 6.0, "Side Effect": "Addiction"}
]

# Function to display drug details when selected
def display_drug_details():
    drug_name = drug_selection.get()
    found = False

    for drug in drugs:
        if drug["Drug Name"].lower() == drug_name.lower():
            # Display drug details
            details_label.config(text=f"Drug: {drug['Drug Name']}\n"
                                      f"Disease: {drug['Disease']}\n"
                                      f"Price: ${drug['Price']}\n"
                                      f"Side Effect if Overconsumed: {drug['Side Effect']}")
            found = True
            break

    if not found:
        messagebox.showerror("Error", "Drug not found. Please select a valid drug.")

# Initialize the main window
root = tk.Tk()
root.title("Drug Information")
root.geometry("600x450")

# Add a label to instruct the user
instruction_label = tk.Label(root, text="Select a Drug to Check its Price, Disease, and Side Effects", 
                             font=("Helvetica", 14))
instruction_label.pack(pady=30)

# Create a dropdown menu for drug selection
drug_names = [drug["Drug Name"] for drug in drugs]  # List of drug names
drug_selection = tk.StringVar(root)
drug_selection.set(drug_names[0])  # Default selection
dropdown = tk.OptionMenu(root, drug_selection, *drug_names)
dropdown.config(font=("Helvetica", 12))
dropdown.pack(pady=15)

# Button to display drug details
check_button = tk.Button(root, text="Check Details", command=display_drug_details, font=("Helvetica", 12), 
                         width=20, height=2)
check_button.pack(pady=20)

# Label to show drug details (price, disease, and side effects)
details_label = tk.Label(root, text="", font=("Helvetica", 12), width=60, height=6, anchor="w", justify="left")
details_label.pack(pady=10)

# Add a footer for style
footer_label = tk.Label(root, text="Drug Information | Created with love", font=("Helvetica", 10))
footer_label.pack(side="bottom", pady=15)

# Run the tkinter event loop
root.mainloop()
