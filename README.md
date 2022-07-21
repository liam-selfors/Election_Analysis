# Election_Analysis
## Overview of Election Audit

### Project Overview
A Colorado Board of Elections employee has given you the following tasks to complete the election audit of a recent local congressional election.

1. Calculate the total number of votes cast.
2. Get a complete list of counties with voters.
3. Calculate the total number of votes from each county.
4. Calculate the percentage of the total votes for each county.
5. Determine the county with the largest turnout.
6. Get a complete list of candidates who received votes.
7. Calculate the total number of votes each candidate received.
8. Calculate the percentage of votes each candidate won.
9. Determine the winner of the election based on popular vote.

### Resources
- Data Source: election_results.csv
- Software: Python 3.10.5, Visual Studio Code 1.67.2

## Election Audit Results

### Election Outcomes

The analysis of the election shows that:
- There were *369,711* votes cast in the election.
- The counties were:
    - Jefferson
    - Denver
    - Arapahoe
- The county turnouts were:
    - Jefferson received *10.5%* of the vote and *38,855* number of votes.
    - Denver received *82.8%* of the vote and *306,055* number of votes.
    - Arapahoe received *6.7%* of the vote and *24,801* number of votes.
- Denver had the largest county turnout of *306,055*.
- The candidates were:
    - Charles Casper Stockham
    - Diana DeGette
    - Raymon Anthony Doan
- The candidate results were:
    - Charles Casper Stockham reveived *23.0%* of the vote and *85,213* number of votes.
    - Diana DeGette reveived *73.8%* of the vote and *272,892* number of votes.
    - Raymon Anthony Doane reveived *3.1%* of the vote and *11,606* number of votes.

!['PyPoll Results'](Resources/pypoll_results.png)

## Election Audit Summary

### Statement to the election commission

This script will function similarly to the *election_results.csv* use case so long as the new data contains rows that represent unique ballots and include *County* and *Candidate* columns in column index 1 and 2 respectively.

#### Modifications to the Script

The script can be modified in a few different ways to ensure the script can be used for any election data. Two examples are given below:

1. Data Cleaning: A high-profile critique on ballot counting is the possibility for tallying the same ballot multiple times, leading to inflated vote counts that may even impact the election's outcome. To ensure this doesn't happen with future election data, duplicate rows can be removed. A list of the `unique_ballots` can be initialized with `unique_ballots = []`. Then, the conditional `if row[0] not in unique_ballots` can be placed within the `for row in reader:` loop to run an append method, `unique_ballots.append(row[0])`, that ensures a given *Ballot ID* is not counted again. Finally, the rest of the code to process each ballot is run within the conditional.

2. Input File with Additional Columns: New election data may not always be formatted in exactly the same way. If the *County* and *Candidate* columns are not provided in column index 1 and 2 respectively, the current code might erroneously extract another column's data in place of the actual *County* or *Candidate* columns. To add support for new datasets like these, the headers list can be queried to find which column index includes the proper data. By looping through the enumerated headers with `for i, header in enumerate(headers):` and if either of the `if header == "County"` or `if header == "County"` conditions are satisfied, the indexes for each column can be stored with `county_index = i` or `candidate_index = i`. Finally, the indexes can be used when the *County* or *Candidate* columns are referenced later on in the code.