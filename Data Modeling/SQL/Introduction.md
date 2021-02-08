Why can't everything be stored in a giant Excel spreadsheet?

    There are limitations to the amount of data that can be stored in an Excel sheet. So, a database helps organize the elements into tables - rows and columns, etc. Also reading and writing operations on a large scale is not possible with an Excel sheet, so it's better to use a database to handle most business functions.

Does data modeling happen before you create a database, or is it an iterative process?

    It's definitely an iterative process. Data engineers continually reorganize, restructure, and optimize data models to fit the needs of the organization.

How is data modeling different from machine learning modeling?

    Machine learning includes a lot of data wrangling to create the inputs for machine learning models, but data modeling is more about how to structure data to be used by different people within an organization. You can think of data modeling as the process of designing data and making it available to machine learning engineers, data scientists, business analytics, etc., so they can make use of it easily.

Key points about Data Modeling

    Data Organization: The organization of the data for your applications is extremely important and makes everyone's life easier.
    
    Use cases: Having a well thought out and organized data model is critical to how that data can later be used. Queries that could have been straightforward and simple might become complicated queries if data modeling isn't well thought out.
    
    Starting early: Thinking and planning ahead will help you be successful. This is not something you want to leave until the last minute.
    
    Iterative Process: Data modeling is not a fixed process. It is iterative as new requirements and data are introduced. Having flexibility will help as new information becomes available.

Relational Databases 
![](images/rel_database.png)

ACID Transactions

Properties of database transactions intended to guarantee validity even in the event of errors or power failures.

    Atomicity: The whole transaction is processed or nothing is processed. A commonly cited example of an atomic transaction is money transactions between two bank accounts. The transaction of transferring money from one account to the other is made up of two operations. First, you have to withdraw money in one account, and second you have to save the withdrawn money to the second account. An atomic transaction, i.e., when either all operations occur or nothing occurs, keeps the database in a consistent state. This ensures that if either of those two operations (withdrawing money from the 1st account or saving the money to the 2nd account) fail, the money is neither lost nor created. Source Wikipedia for a detailed description of this example.

    Consistency: Only transactions that abide by constraints and rules are written into the database, otherwise the database keeps the previous state. The data should be correct across all rows and tables. Check out additional information about consistency on Wikipedia.

    Isolation: Transactions are processed independently and securely, order does not matter. A low level of isolation enables many users to access the data simultaneously, however this also increases the possibilities of concurrency effects (e.g., dirty reads or lost updates). On the other hand, a high level of isolation reduces these chances of concurrency effects, but also uses more system resources and transactions blocking each other. Source: Wikipedia

    Durability: Completed transactions are saved to database even in cases of system failure. A commonly cited example includes tracking flight seat bookings. So once the flight booking records a confirmed seat booking, the seat remains booked even if a system failure occurs. 
    
### When to not use a Relational Database

![image.png](https://boostnote.io/api/teams/F3fu2GG5h/files/58291a2397db5c4b36b0c7bd3961ed8a4a9cac8cb3057d725e9076b7fe97139c-image.png)

NoSQL Types os DBs
![image.png](https://boostnote.io/api/teams/F3fu2GG5h/files/c4df135d0acbee524bbda828b9a2d1892be960128032d325660845119c37cc1d-image.png)

![image.png](https://boostnote.io/api/teams/F3fu2GG5h/files/8bc99f2b99934024695131d5289f41efec1d93b879b0b6ea2257b6d6b0fb2679-image.png)
