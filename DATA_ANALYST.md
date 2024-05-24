# Lending Data Analyst Case

## Introduction

The goal here is to assess your proficiency in SQL and data visualization.

Your task involves analyzing and managing this data to provide business insights. We expect not just task execution, but also a clear articulation of your thought process. Each solution should include an explanation of your logic and a reference to the code used to reach that solution.

## The dataset

The clients and loans tables translate the lending operations of a Brazilian bank. All the loans have a 90-day duration and no installment payments. The clients must pay at the pace that they see fit. The cost (interest) of the loan is fixed. The due amount of the loan is clearly stated for the client when the contract is issued. For this example, let’s suppose that it doesn't matter how fast the loan is repaid, the amount charged will remain unchanged despite the interest rate.

Consider the current date to be January 25, 2024.

# Tables Structure

## Clients Table ([csv](files/clients.csv))

| Column Name    | Data Type      | Description                                                                                          |
|----------------|----------------|------------------------------------------------------------------------------------------------------|
| user_id        | int64          | Unique identifier for each user                                                                      |
| created_at     | datetime64[ns] | Date and time when the user was created                                                             |
| status         | string         | The status of the user (approved, denied). If denied, the user cannot take new loans.               |
| batch          | int64          | The batch to which the user belongs                                                                  |
| credit_limit   | int64          | The credit limit assigned to the user. The maximum amount the user can borrow.                      |
| interest_rate  | int64          | The annual interest rate assigned to the user. The rate at which the user will be charged for borrowing money. |
| denied_reason  | string         | The reason for denial of the user. If the user is approved, this field is empty.                     |
| denied_at      | datetime64[ns] | The date and time when the user was denied. If the user is approved, this field is empty.            |

## Loans Table ([csv](files/loans.csv))

| Column Name  | Data Type      | Description                                                                                               |
|--------------|----------------|-----------------------------------------------------------------------------------------------------------|
| user_id      | int64          | Unique identifier for each user                                                                           |
| loan_id      | int64          | Unique identifier for each loan                                                                           |
| created_at   | datetime64[ns] | Date and time when the loan was created                                                                   |
| due_at       | datetime64[ns] | Date and time when the loan is due                                                                        |
| paid_at      | datetime64[ns] | Date and time when the loan was paid. If the loan is not paid, this field is empty.                       |
| status       | string         | The status of the loan (paid, default, ongoing). If the loan is ongoing, it means there is an open loan. The user cannot have two open loans at the same time. If the loan is defaulted, the user cannot take new loans. |
| loan_amount  | float64        | The amount of the loan.                                                                                   |
| tax          | float64        | The tax on the loan (3.8% of the principal amount + 0.0082% of the principal amount per day for 90 days)  |
| due_amount   | float64        | The total amount due on the loan (loan_amount + tax + 90 days interest)                                   |
| amount_paid  | float64        | The amount paid on the loan, until the current moment.                                                    |



## Instructions

- Set up an infrastructure using Python for you to make queries over the tables and present charts/tables of your results.
- All answers must have charts and a clear explanation of your results.


## Case Resolution

1. Provide a detailed description of the data you are handling.
2. Identify the best month in terms of loan issuance. What was the quantity and amount lent in each month?
3. Which batch had the best overall adherence?
4. Do different interest rates lead to different loan outcomes in terms of default rate?
5. Rank the best 10 and 10 worst clients. Explain your methodology for constructing this ranking.
6. What is the default rate by month and batch?
7. Assess the profitability of this operation. Provide an analysis of the operation's timeline.
    - Clearly state how you are defining the concept of profit.
    - Show the growth of this metric throughout time and what may have impacted the positive/negative growth.

> adherence: clients that got loans\
> season: loan issuing month\
> default rate: defaulted/issued loans

## Case delivery

To submit this case, email pedro.beraldin@cloudwalk.io with a link to a GitHub repository. In this repository, there must be a Jupyter Notebook with the answers for each of the questions. You can be creative in the way the Notebook is structured and how it interacts with the rest of the repository. Just make sure to add a readme file with the instructions to use it.

Good luck!