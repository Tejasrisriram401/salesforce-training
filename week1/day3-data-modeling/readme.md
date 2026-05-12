Here’s a clean and well-structured `README.md` content for your assignment 🚀
You can directly copy this into:

```text
/day3-data-modeling/README.md
```

---

# Salesforce Data Modeling – Day 3

## 1. Difference Between App, Object, Record, and Field

| Component  | Description                                                                        | Example                    |
| ---------- | ---------------------------------------------------------------------------------- | -------------------------- |
| **App**    | A collection of tools, tabs, and objects designed for a specific business purpose. | DreamHouse App             |
| **Object** | A database table that stores related information.                                  | Student, Account, Property |
| **Record** | A single row of data inside an object.                                             | One student’s details      |
| **Field**  | A column in an object used to store specific information.                          | Name, Email, Phone         |

---

## 2. Standard vs Custom Objects

| Standard Objects                       | Custom Objects                    |
| -------------------------------------- | --------------------------------- |
| Pre-built by Salesforce                | Created by users                  |
| Available by default                   | Built for business-specific needs |
| Example: Account, Contact, Opportunity | Example: Student__c, Hostel__c    |
| Cannot be deleted easily               | Fully customizable                |

### Examples

#### Standard Objects

* Account
* Contact
* Opportunity
* Lead

#### Custom Objects

* Student__c
* Faculty__c
* Course__c
* Hostel__c

---

# 3. College Data Model

## Objects Used

### Standard Objects

* Account
* Contact

### Custom Objects

* Student__c
* Course__c
* Faculty__c
* Hostel__c
* Attendance__c

---

## Relationships

| Object 1   | Relationship Type | Object 2 |
| ---------- | ----------------- | -------- |
| Student    | Lookup            | Course   |
| Student    | Lookup            | Hostel   |
| Faculty    | Lookup            | Course   |
| Attendance | Master-Detail     | Student  |

---

## College Data Model Diagram

```text
             +----------------+
             |   Faculty__c   |
             +----------------+
                     |
                     | teaches
                     |
             +----------------+
             |   Course__c    |
             +----------------+
                     |
                     | enrolled in
                     |
             +----------------+
             |   Student__c   |
             +----------------+
                /          \
               /            \
      stays in              has
             /                \
+----------------+    +----------------+
|   Hostel__c    |    | Attendance__c  |
+----------------+    +----------------+
```

---

# 4. Formula Fields

Formula fields automatically calculate values based on other fields.

## Example 1: Days Remaining for Contract

### Formula

\text{EndDate} - \text{TODAY()}

### Explanation

This formula calculates how many days are left before the contract expires.

---

## Example 2: Student Full Name

### Formula

\text{FirstName} + \ "\ " + \text{LastName}

### Explanation

This combines first name and last name into a full name.

---

## Example 3: Attendance Percentage

### Formula

\frac{\text{Classes Attended}}{\text{Total Classes}} \times 100

### Explanation

This calculates the attendance percentage of a student.

---

# 5. Validation Rules

Validation rules help maintain accurate and clean data.

---

## Example 1: ZIP Code Validation

### Rule

The contact ZIP code must match the account ZIP code.

### Formula

```text
AND(
NOT(ISBLANK(AccountId)),
MailingPostalCode <> Account.ShippingPostalCode
)
```

### Explanation

* Checks whether the contact is linked to an account
* Compares ZIP codes
* Prevents saving if they are different

---

## Example 2: Student Age Validation

### Formula

```text
Age__c < 16
```

### Explanation

Prevents saving student records if age is less than 16.

---

## Example 3: Email Required Validation

### Formula

```text
ISBLANK(Email__c)
```

### Explanation

Ensures every student record contains an email address.

---

# 6. Reflection – Why Structured Enterprise Data Matters

Structured enterprise data is very important because it helps organizations store, manage, and analyze information efficiently. In Salesforce, proper data modeling improves automation, reporting, security, and decision-making.

A well-structured system:

* Reduces duplicate data
* Improves data accuracy
* Helps generate meaningful reports
* Supports automation workflows
* Makes applications scalable and maintainable

In a college management system, structured data helps manage students, faculty, attendance, hostel details, and courses in an organized way. It improves communication, tracking, and overall operational efficiency.

---

# Conclusion

Through this activity, I learned:

* Salesforce data modeling concepts
* Difference between standard and custom objects
* Creating relationships between objects
* Using formula fields
* Implementing validation rules
* Importance of structured enterprise data

This knowledge helps in building scalable and efficient Salesforce applications for real-world business scenarios.
