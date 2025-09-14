# JMeter Chaining with Dmoney API  
## Project Summary

This project demonstrates **JMeter chaining** using the Dmoney API. The goal is to simulate multiple transaction scenarios with agents, customers, and merchants using JMeter.  

---
##  API Website  
All transactions were executed using the Dmoney API available at:  
[http://dmoney.roadtocareer.net](http://dmoney.roadtocareer.net)  

##  Scenario Implemented  
**Deposits** - 5 agents perform deposits for 10 customers.

**Send Money** - 5 customers send money to another 10 customers.

**Payments** - 5 customers make payments to 2 merchants.

---

##  Implementation Details  

###  Admin Login Token  
- Logged in once as **Admin** to generate an authorization token.  
- The token is reused across all transactions (via **HTTP Header Manager**).  


###  CSV Data  
Used **CSV Data Set Config** to manage accounts dynamically:  
- `deposit.csv` → Agent & Customer data  
- `sendMoney.csv` → Customer-1 & Customer-2 data  
- `payment.csv` → Customer & Merchant data  

###  Dynamic Amount  
- Used **Random Variable Config** to generate small random amounts (so balance never becomes empty).  

###  Chaining  
- Each request uses **data/response from the previous step** (e.g., customer/agent IDs, token).  
- Ensures **seamless flow of dependent requests**.  

###  Assertions  
- Added **Response Assertion** to verify that each transaction is successful.  


---

##  How to Run

1. **Clone the repository**  
   ```bash
   git clone <repo_url>
2. Open Apache JMeter

3. Ensure the following CSV files are in the same directory as `DMoney.jmx`:

- `deposit.csv`
- `sendMoney.csv`
- `payment.csv`

4. Open the JMX file
5. Run the test plan

##  HTML report for DMoney Jmeter Collection -
<img width="1505" height="489" alt="image" src="https://github.com/user-attachments/assets/e6a615aa-eda7-4275-b602-c29453727d5a" />
<img width="1469" height="571" alt="image" src="https://github.com/user-attachments/assets/d3c4f566-b57a-4993-9397-bc98ac37f732" />


