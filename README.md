I used the AI on bootcamp spot to help debug. I was unable to get this code to work as well. I think my actual coding is correct, but for some reason it would not read the CSV file. I was also unable to use the git commit command to pull my code for Pypoll. I have included my raw code below to help with any confusion. # -*- coding: UTF-8 -*-
"""PyPoll Homework Starter File."""


# Import necessary modules
import csv
import os


# Files to load and output (update with correct file paths)
file_to_load = os.path.join("Resources", "election_data.csv")  # Input file path
file_to_output = os.path.join("analysis", "election_analysis.txt")  # Output file path


# Initialize variables to track the election data
total_votes = 0  # Track the total number of votes cast


# Define lists and dictionaries to track candidate names and vote counts
candidate_votes = {}  # Dictionary to hold candidate names and their vote counts


# Winning Candidate and Winning Count Tracker
winning_candidate = ""  # Variable to track the name of the winning candidate
winning_count = 0       # Variable to track the highest number of votes received


# Open the CSV file and process it
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)
    # Skip the header row
    header = next(reader)


    # Loop through each row of the dataset and process it
    for row in reader:


        # Print a loading indicator (for large datasets)
        print(". ", end="")


        # Increment the total vote count for each row
        total_votes += 1  # Increase the total vote count by 1 for each row


        # Get the candidate's name from the row
        candidate_name = row[2]  # Getting the candidate's name from the third column


        # If the candidate is not already in the candidate list, add them
        if candidate_name not in candidate_votes:
            candidate_votes[candidate_name] = 0  # Initialize vote count for the candidate
        # Add a vote to the candidate's count
        candidate_votes[candidate_name] += 1  # Increment the candidate's vote count by 1


# Open a text file to save the output
with open(file_to_output, "w") as txt_file:


    # Print the total vote count (to terminal)
    print("\nElection Results")  # Print header for election results
    print("-------------------------")  # Print a line for separation
    print(f"Total Votes: {total_votes}")  # Print the total number of votes
    print("-------------------------")  # Print a line for separation


    # Write the total vote count to the text file
    txt_file.write("Election Results\n")  # Write header to the output file
    txt_file.write("-------------------------\n")  # Write separation line to the output file
