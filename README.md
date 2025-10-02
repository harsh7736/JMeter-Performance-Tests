# WebTours Performance Testing Project (JMeter)

[![Build](https://img.shields.io/badge/build-passing-brightgreen)](https://github.com/harsh7736/saucedemo-selenium-java-automation/actions)
[![JMeter](https://img.shields.io/badge/JMeter-Performance-red)](https://jmeter.apache.org/)
[![CSV](https://img.shields.io/badge/Data-CSV-blue)](https://en.wikipedia.org/wiki/Comma-separated_values)
[![HTTP Cookie](https://img.shields.io/badge/Session-HTTPCookieManager-yellow)](https://jmeter.apache.org/)
[![Regex Extractor](https://img.shields.io/badge/Correlation-RegexExtractor-orange)](https://jmeter.apache.org/)
[![Transaction Controller](https://img.shields.io/badge/Flow-TransactionController-purple)](https://jmeter.apache.org/)

---

This repository contains a robust, data-driven performance test suite developed in **Apache JMeter**, designed to simulate realistic user load on the **WebTours flight reservation application**.

The primary goal of this project is to validate the application's scalability and identify potential performance bottlenecks under concurrent user traffic.

---

## 🚀 Scenario & Workflow
The test script simulates a complete, end-to-end business transaction flow, structured using Transaction Controllers for precise timing measurements:

1. **Login:** User authentication using unique credentials.  
2. **Flight Search:** Submitting search criteria for flights.  
3. **Flight Selection:** Choosing a specific outbound and inbound flight.  
4. **Reservation:** Providing passenger details and submitting the final booking.  
5. **Sign Off:** Securely logging out of the application.  

---

## 🛠️ Technical Implementation

| Feature               | Implementation Detail                                                                 | Purpose                                                         |
|-----------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| Data-Driven Testing   | Uses a CSV Data Set Config to inject data for 5 concurrent users (Username, Password, Passenger Count, Flight Class, etc.) | Ensures each thread uses unique, dynamic data for every iteration. |
| Correlation           | Employs a Regular Expression Extractor to dynamically capture the crucial userSession ID from the login response | Maintains session integrity and prevents functional failures under load |
| Session Management    | HTTP Cookie Manager configured to handle cookies automatically                        | Maintains the state of each virtual user throughout the booking workflow |
| Flow Control          | Transaction Controllers used for distinct scenarios (Login, Reservation, Sign-Off)   | Provides meaningful response time metrics per business transaction |
| Validation            | Response and Duration Assertions at critical steps (e.g., Login)                      | Confirms functional correctness and SLA adherence |

---

## 📊 Reporting & Analysis
- **CLI Execution:** Configured for command-line execution to ensure efficiency during large load tests.  
- **Raw Output:** Results saved to a `.jtl` file (CSV format).  
- **Performance Dashboard:** HTML reports generated post-execution using the `-e -o` flags, providing:  
  - Aggregate Report (Average, 90th Percentile, Throughput)  
  - Time-based charts (Transactions per Second, Response Times, Latency)  

**JMeter Listeners used:**  
- View Results Tree: For inspecting request/response payloads, validating correlation, and confirming assertion hits.  
- Aggregate Report: For summarizing key performance metrics.  

---

## 🖼️ Report Snapshots
Key performance indicators and successful run details:

1. **Aggregate Report Summary**  
*(Place screenshot here)*  

2. **View Results Tree (Successful Transaction)**  
*(Place screenshot here)*  

3. **HTML Dashboard Overview**  
*(Place screenshot here)*  

> For the complete set of screenshots, refer to [`JMeter_Test_Results.docx`](JMeter_Test_Results.docx).

---

## ⚡ How to Run
1. **Clone the repository:**  
"```bash"
git clone https://github.com/harsh7736/JMeter-Performance-Tests.git

2. Open JMeter (Apache JMeter 5.x recommended).

3. Load the .jmx file from the JMX_Files folder.

4. Ensure CSV data files are placed in CSV_Data/.

5. Run the Test Plan: Execute locally or in CLI mode using:

   jmeter -n -t JMX_Files/WebTools_FlightTest.jmx -l HTML_Reports/results.jtl -e -o HTML_Reports/dashboard

6. View Results: Open generated HTML dashboard or refer to the Word document for screenshots.



Author
Harsh Singh
