# RXNOW  
## Feature Planning

---

## Overview  
This document organizes system functionality into feature groups and defines the development tasks required to implement each feature. Features are derived from the Product Functions (PF1–PF6) and are prioritized for MVP development.

---

## Feature 1: Authentication (PF1)

**Description:**  
Handles user account creation, login, logout, and password recovery.

**Tasks:**
- [ ] Implement User entity and database schema (DB1)
- [ ] Validate unique email and format (FR1)
- [ ] Implement password validation rules (FR2, DB8)
- [ ] Implement authentication logic (FR3)
- [ ] Implement session termination (FR4)
- [ ] Implement password reset via email workflow (FR5)
- [ ] Hash and store passwords securely (SA3)
- [ ] Validate required input fields (SA4)

**Priority:** High  
**Dependencies:** None  

---

## Feature 2: Medication Management (PF2)

**Description:**  
Allows users to create, edit, view, and delete medication records.

**Tasks:**
- [ ] Implement Medication entity and schema (DB2)
- [ ] Enforce User–Medication relationship (DB3)
- [ ] Implement create medication functionality (FR6)
- [ ] Implement update medication functionality (FR8)
- [ ] Implement delete medication functionality (FR9)
- [ ] Store medication attributes (FR7)
- [ ] Validate input constraints (DB4–DB7)
- [ ] Handle invalid or missing records gracefully (SA2)

**Priority:** High  
**Dependencies:** Authentication  

---

## Feature 3: Supply Calculation (PF3)

**Description:**  
Calculates and provides remaining medication supply in days.

**Tasks:**
- [ ] Implement days_remaining calculation logic (FR10)
- [ ] Integrate calculation with medication data retrieval (FR11)
- [ ] Ensure calculation performance meets requirements (PR3)
- [ ] Handle edge cases (e.g., zero or invalid values)

**Priority:** High  
**Dependencies:** Medication Management  

---

## Feature 4: Dashboard (PF4)

**Description:**  
Displays all medication data and supply status in a single view.

**Tasks:**
- [ ] Retrieve all medications for authenticated user (FR12)
- [ ] Display required medication fields (FR13)
- [ ] Implement dashboard UI layout (IR3)
- [ ] Ensure mobile-responsive design (IR1)
- [ ] Display medication name and days_remaining in same view (UR2)
- [ ] Optimize dashboard load performance (PR1)

**Priority:** High  
**Dependencies:** Medication Management, Supply Calculation  

---

## Feature 5: Notifications (PF5)

**Description:**  
Generates and displays alerts when medication supply is low.

**Tasks:**
- [ ] Implement threshold detection logic (7, 3, 1 days) (FR14–FR15)
- [ ] Prevent duplicate notifications unless reset condition occurs (FR15)
- [ ] Generate notification messages (FR16)
- [ ] Display notifications in UI (UR4)
- [ ] Add visual indicators for low supply (UR3)
- [ ] Validate notification accuracy

**Priority:** Medium  
**Dependencies:** Supply Calculation, Dashboard  

---

## Feature 6: Refill Workflow (PF6)

**Description:**  
Supports refill request creation, tracking, and message generation.

**Tasks:**
- [ ] Add provider association to medication (FR18)
- [ ] Generate structured refill request message (FR19)
- [ ] Implement refill initiation control (FR17)
- [ ] Simulate sending refill request (FR20)
- [ ] Display confirmation message (FR21)
- [ ] Track refill request status (FR22)
- [ ] Display refill status in UI (FR23)
- [ ] Integrate with external email application (IR5)
- [ ] Handle message generation and send failures (Section 4.5)

**Priority:** Medium  
**Dependencies:** Medication Management, Dashboard  

---

## Development Order (MVP Priority)

1. Authentication (PF1)  
2. Medication Management (PF2)  
3. Supply Calculation (PF3)  
4. Dashboard (PF4)  
5. Notifications (PF5)  
6. Refill Workflow (PF6)  

---

## Notes

- All features must comply with performance requirements (PR1–PR4)
- All input must be validated before processing (SA4)
- The system must remain stable under invalid input conditions (SA2)
- External integrations are limited to launching the device email client (DC1, IR5)
