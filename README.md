Here’s the content you can use for the README file of your project:

---

# BSafe: Crime and Accident Database

**Group Members:**
- Suja Ganesh Murugan  
  Email: [ganeshmurugan.s@northeastern.edu](mailto:ganeshmurugan.s@northeastern.edu)  
  Phone: 617-602-9351  
  Percentage of Effort: 50%

- SaiTeja Reddy Gajula  
  Email: [gajula.sai@northeastern.edu](mailto:gajula.sai@northeastern.edu)  
  Phone: 857-961-6330  
  Percentage of Effort: 50%

**Submission Date:** 12-10-2023

## 1. Introduction

The BSafe project was developed to address the increasing safety concerns of travelers and residents post-COVID-19. Leveraging advancements in technology and transportation, BSafe provides an intuitive platform that enables users to access real-time information about safety, crime, and accidents in their geographical location.

The Crime and Accident Database collects information from a wide range of sources, including law enforcement reports, safety blogs, and other credible databases. This platform offers valuable insights, helping users stay informed and mitigate risks.

Key features of BSafe include:
- **Color-Coded Map:** Areas are highlighted based on crime and accident severity (yellow for accidents, orange for moderate crimes, and red for severe crimes).
- **Safe Zones:** Users are directed to nearby safe zones like hospitals, police stations, and fire stations.
- **Real-Time Notifications:** Location-based alerts notify users of potential hazards as they move through different areas.

## 2. Conceptual Data Modelling

### EER (Enhanced Entity Relationship) Diagram & UML Diagram
The design of the database captures relationships between users, areas, crimes, incidents, and safety zones.

## 3. Mapping Conceptual Model to Relational Model

The following entities and relationships were mapped:
- **Users** (User_ID, Email_ID, Gender, Address, Ethnicity)
- **Feedback** (Feedback_ID, Description, User_ID)
- **Areas** (Area_ID, Crime_Rate, Population, Location, Nearest_Safezone_ID)
- **Safezones** (Safezone_ID, Location)
- **Incidents** (Incident_ID, Incident_Type, DateTime, Area_ID)
- **Suspects** (Suspect_ID, Name, In_jail, Photo)

## 4. Implementation in MySQL

The database schema was implemented using the following key tables and relationships:

### Example SQL Queries:
1. **Retrieve User Information:**  
   ```sql
   SELECT Email_ID, Address FROM Users;
   ```

2. **Find Average Crime Rate:**  
   ```sql
   SELECT ROUND(AVG(Crime_Rate), 2) AS AVG_Crime_Rate FROM Areas;
   ```

3. **List Incidents and Suspects:**  
   ```sql
   SELECT S.Name, I.Incident_Type, I.Incident_DateTime, I.Description  
   FROM Caused_by C  
   INNER JOIN Incidents I ON I.Incident_ID = C.Incident_ID  
   INNER JOIN Suspects S ON C.Suspect_ID = S.Suspect_ID  
   WHERE MONTH(Incident_DateTime) = 03  
   ORDER BY Incident_DateTime;
   ```

## 5. Implementation in NoSQL

MongoDB was used for the NoSQL implementation with collections for **Users**, **Areas**, **Suspects**, and **Incidents**.

### Example MongoDB Queries:
1. **Update User Location:**
   ```javascript
   db.users.update(
     { "User_ID": 0 },
     { $set: { "Current_location": "529 South Rocky Hague Road" } }
   );
   ```

2. **Count of Suspects in Jail:**
   ```javascript
   db.suspects.aggregate([
     { $group: { _id: "$In_jail", total: { $sum: 1 } } },
     { $sort: { total: 1 } }
   ]);
   ```

## 6. Data Analysis with Python

Using MySQL connector in Python, SQL query results were transformed into Pandas DataFrames and visualized using Matplotlib and Seaborn.

### Example Visualizations:
- **Crime Rate Across Areas**
- **Correlation Between Crime Rates and Incidents**
- **Distribution of Suspects by Location**

## 7. Summary and Recommendations for Improvement

BSafe successfully provides a comprehensive solution for users concerned with safety in various geographical regions. It enables real-time access to crime and accident information and directs users to safe zones.

### Areas for Improvement:
1. **Enhanced User Registration:** Improve the registration process for better user experience and data collection.
2. **Expanded Notifications:** Include real-time updates about local events and weather to provide a broader view of the users' surroundings.
3. **Privacy & Data Security:** Ensure robust data security measures to maintain user trust and confidentiality.
4. **Community Engagement:** Foster an active community where users can share safety tips and experiences.

## Conclusion

BSafe is a step towards creating safer travel and living experiences by providing users with data-driven insights about their surroundings. The continued improvement of user features and security measures will ensure its relevance and effectiveness in promoting safety awareness.
