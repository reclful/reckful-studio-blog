---
title: LeetCode 0175 - Combine Two Tables
date: 2018-06-04 15:27:31
categories: LeetCode
---
# Combine Two Tables

<!--more-->

## Desicription

Table: `Person`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+
PersonId is the primary key column for this table.
```

Table: `Address`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+
AddressId is the primary key column for this table.
```

Write a SQL query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people:

```
FirstName, LastName, City, State
```

## Solution

```sql
# Write your MySQL query statement below
select Firstname, LastName, City, State
from Person
left join Address
on Person.PersonId = Address.PersonId;
```