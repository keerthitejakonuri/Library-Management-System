Quick Guide
1. Introduction
2. Search and Availability
3. CheckOut
4. Adding a Borrower
5. CheckIn
6. Fines
Introduction
The Library Management which I created has five modules, 1st module mainly performs search of a book and displays the availability of book in a particular branch, 2nd module is dedicated to checkout a book that is selected by the librarian, 3rd module is used to add a new borrower, 4th module is used in case of return of a book to check-in the book, 5th module deals with fines and displaying of fines. To create User Interface for library application I used Java Swings. And this is data files provided. I used JTabbed pane to create tabs.
Search and Availability
Using my GUI, librarian will be able to search for a book, given any combination of book_id, title,
And / or Author(s), which may be either author_name OR any combination of
part of an author's name. And on pressing Fetch Data button it displays rows that are matched with the given input. The multiple copies at different branch locations are displayed on separate lines, to facilitate
location specific checkout. Clear all button clears the data in the text fields and also the data in the JTable.
A Dialogue box is displayed when there is no Matching row. On clicking on a row transfers the control to checkout tab with text fields filled with the values of the row clicked.
CheckOut
Using my GUI, librarian will be able to check out a book, given the combination of
BOOK_COPIES (book_id, branch_id) and BORROWER (Card_no), i.e. create a new tuple
in BOOK_LOANS. I Generated a new unique primary key for loan_id. The date_out should
be today’s date. The due_date should be 14 days after the date_out.
Each BORROWER is permitted a maximum of 3 BOOK_LOANS. If a BORROWER
already has 3 BOOK_LOANS, then the checkout (i.e. create new BOOK_LOANS tuple)
will fail and return a useful error message.
If the number of BOOK_LOANS for a given book at a branch already equals the
No_of_copies (i.e. There are no more book copies available at your library_branch), then
the checkout will fail and return a useful error message.
Adding a Borrower
Using my GUI, librarian will be able to create new borrowers in the system.
All name and address attributes are created to a new account (i.e. value must be
not null).
Automatically generated new card_no primary keys for each
new tuple that uses a compatible format with the existing borrower IDs using AUTOINCREMENT.
Borrowers are allowed to possess exactly one library card. If a new borrower is
attempted with the same fname, lname, and address, then it rejects and
return a useful error message.
Check-In
This module provides text fields to enter Book_id, card_no and borrowername. And displays rows that are matched with the given input values. Using my GUI, librarian will be able to check in a book., he/she will be able to locate BOOK_LOANS tuples by searching on any of book_id, Card_no, and/or any part of BORROWER name. Once located on clicking the particular row the corresponding book from the corresponding branch is checked out on pressing checkedout and pay button. This button also allows the librarian to checkout a book and take the fine. So the corresponding book is again made as available and the fine for the corresponding card_no and loan_id is made as paid in fines table. Clear All button is used to set the data of text fields and JTable to empty.

Fines
Created a new table FINES ( loan_id, fine_amt, paid), The primary key loan_id is also a foreign key that references BOOK_LOANS ( loan_id) ,fine_amt attribute is a dollar amount that should have two decimal places. paid attribute is a boolean value (or integer 0/1) that idicates whether a fine has been
paid.
Fines are assessed at a rate of $0.25/day (twentyfive
cents per day).
Refresh button updates/refreshes entries in the FINES table. In reality, this will be executed daily.
There are two scenarios for late books
(1) Late books that have been returned — the fine will be [(the difference in days
between the due_date and date_in) * $0.25].
(2) Late book that are still out — the estimated fine will be [(the difference between the
due_date and TODAY) * $0.25].
If a row already exists in FINES for a particular late BOOK_LOANS record, then
If paid == FALSE, only updates the fine_amt if different than current value.
If paid == TRUE, nothing is done.
Provided a mechanism for librarians to enter payment of fines (i.e. to update a FINES record
where paid == TRUE) through check-in and payment button in check-in tab.
Payment of fines that are not yet returned aren’t allowed
Display of Fines is grouped by card_no. i.e. SUM the fine_amt for each
Borrower.
While displaying fines I am just displaying the fines on card_no that are yet to be paid.
Also the text field is used to fetch the fine on a particular card.
