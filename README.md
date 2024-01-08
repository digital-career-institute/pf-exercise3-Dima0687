Assignment: Understanding Primary Keys and Foreign Keys in an Election Database
Overview:
In this assignment, you will be working with a database related to an election. You'll apply your knowledge of primary keys and foreign keys by creating tables, manipulating data, and establishing relationships between them.

Tasks:
# 1. CREATE TABLE with PRIMARY KEY:

Create a table named Candidates with the following columns:
candidate_id (INTEGER) as the primary key
name (TEXT)
party_affiliation (TEXT)
position (TEXT)

```SQL
CREATE TABLE Candidates ( candidate_id INT PRIMARY KEY, name TEXT, party_affiliation TEXT, position TEXT );
```

# 2. DROP PRIMARY KEY:

Remove the primary key constraint from the Candidates table (if it exists).
```SQL
ALTER TABLE Candidates DROP PRIMARY KEY;
```

# 3. ADD PRIMARY KEY:

Add a primary key constraint to the Candidates table on the candidate_id column.
```SQL
ALTER TABLE Candidates ADD PRIMARY KEY( candidate_id );
```

# 4. COMPOSITE PRIMARY KEY:

Create a table named Votes with the following columns:
voter_id (INTEGER)
candidate_id (INTEGER)
Make a composite primary key using both voter_id and candidate_id.
```SQL
CREATE TABLE Votes ( voter_id INT, candidate_id INT, PRIMARY KEY ( voter_id, candidate_id ) );
```

# 5. FOREIGN KEY:

Alter the Votes table to add a foreign key constraint to reference the Candidates table's candidate_id column.
```SQL
ALTER TABLE Votes ADD FOREIGN KEY ( candidate_id ) REFERENCES Candidates ( candidate_id );
```

# 6. CREATE TABLE with FOREIGN KEY:

Create a table named Voters with the following columns:
voter_id (INTEGER) as the primary key
name (TEXT)
age (INTEGER)
voted_for (INTEGER) as a foreign key referencing candidate_id in the Candidates table.
```SQL
CREATE TABLE Voters ( voter_id INT PRIMARY KEY, name TEXT, age INT, voted_for INT, FOREIGN KEY ( voted_for ) REFERENCES Candidates ( candidate_id ) );
```

# 7. DROP FOREIGN KEY:

Remove the foreign key constraint from the Voters table (if it exists).
```SQL
ALTER TABLE Voters DROP FOREIGN KEY voters_ibfk_1;
```

# 8. ADD FOREIGN KEY:

Add a foreign key constraint to the Voters table referencing the candidate_id column in the Candidates table.
```SQL
ALTER TABLE Voters ADD FOREIGN KEY ( voted_for ) REFERENCES Candidates ( candidate_id );
```

# Data Manipulation:
## Populate the Candidates table with at least 5 records of hypothetical candidates and their respective party affiliations and positions.
```SQL
INSERT INTO Candidates (candidate_id, name, party_affiliation, position)
VALUES
(1, 'Candidate1', 'PartyA', 'PositionA'),
(2, 'Candidate2', 'PartyB', 'PositionB'),
(3, 'Candidate3', 'PartyC', 'PositionC'),
(4, 'Candidate4', 'PartyA', 'PositionD'),
(5, 'Candidate5', 'PartyB', 'PositionE');
```
## Insert data into the Voters table with at least 10 records containing names, ages, and candidates they voted for.
```SQL
INSERT INTO Voters (voter_id, name, age, voted_for)
VALUES
(101, 'Voter1', 25, 1),
(102, 'Voter2', 30, 2),
(103, 'Voter3', 22, 1),
(104, 'Voter4', 35, 3),
(105, 'Voter5', 28, 2),
(106, 'Voter6', 40, 4),
(107, 'Voter7', 33, 1),
(108, 'Voter8', 27, 5),
(109, 'Voter9', 29, 4),
(110, 'Voter10', 31, 3);
```

## Manipulate the data to perform queries like finding candidates' details, voters who voted for a specific candidate, etc.

```SQL
SELECT * FROM Candidates;

SELECT Voters.name AS Voter_Name, Candidates.name AS Candidate_Name
FROM Voters
INNER JOIN Candidates ON Voters.voted_for = Candidates.candidate_id
WHERE Candidates.name = "Candidate1";
```
