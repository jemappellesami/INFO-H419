# 1. Introduction to Data Warehouses (D.W)

## 1.1. Brief introduction
- Database : general term that we will use to talk about **operationnal databases**
  - Specialized for being updated and executing queries
  - Store, maintain, and query
- Data Warehouse : database specialized for data analytics


## 1.2. Real introduction
A database is simply a piece of software to handle data : store, maintain, and query. As often, the chosen system should depend on the **situation** we are in.

### 1.2.1. Online Transaction Processing (OLTP)
- Database management :
  - Must ensure concurrent access : **Atomicity**. The entire transaction must be done, or not at all !!
  - Data consistency
    - One a transaction is executed, the modification should be consistent ! *La transaction a un sens*. 
    - For each transaction, there must be a log in and a log out, with a signature of the consistency at this stage. So when a problem occurs, we know when it happened.

  - Durability : everything that has been forwarded to the user *should be the true*
  - Isolation : if two persons manage the same account. 
    - The DB can have this two "access points". 
    - See example to see how the arrengement of the operations have a crucial role.
    - To avoid it : we use "LOCKS", or read-only mode. But we do it smartly. We don't provide access to "only one cell in the table", because it would be too expensive ! Usually, we give access to a "whole page"


Brought together : ACID

All these concurrency control protocols are taking a lot of resources. As for data warehouses, we don't need that !

### 1.2.2. DW
We take a **snapshot**, a copy of the state of the database. We throw away all the mecanisms of the DB, and we use all the computer resources for data analytics, etc. Transaction processing resources are dropped off!
## 1.3. Design theory
### 1.3.1. About normalization (reminder)
- We want to avoid inconsistancy (update 1 information = update a lot of lines if the DB is not normalized)
- We want to avoid some data to exist

