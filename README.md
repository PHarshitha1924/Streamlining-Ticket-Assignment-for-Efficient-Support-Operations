
Project: Streamlining Ticket Assignment for Efficient Support Operations

Objective: Implement an automated ticket routing system in ServiceNow at ABC Corporation to improve operational efficiency by accurately assigning support tickets, reducing resolution delays, enhancing customer satisfaction, and optimizing resource utilization.

1. User Creation: Open ServiceNow → All → Users (System Security) → New → Enter user details → Submit → Repeat to create more users.

2. Group Creation: Open ServiceNow → All → Groups (System Security) → New → Enter group details → Submit → Repeat as needed.

3. Role Creation: Open ServiceNow → All → Roles (System Security) → New → Enter role details → Submit → Repeat as needed.

4. Table Creation: Open ServiceNow → All → Tables (System Definition) → New → Label: Operations Related → Enable Create module & Create mobile module → Menu Name: Operations Related → Add required columns → Submit.
Choices for Issue field: Unable to login to platform, 404 Error, Regarding Certificates, Regarding User Expired.

5. Assign Roles & Users to Groups:
Certificates Group: All → Groups → Certificates Group → Add user: Katherine Pierce → Add role: Certification_Role.
Platform Group: All → Groups → Platform Group → Add user: Manne Niranjan → Add role: Platform_Role.

6. Assign Roles to Table: All → Tables → Operations Related → Application Access → For Read and Write operations → Require Platform_Role and Certification_Role.

7. Create ACL: All → Access Control (ACL) (System Security) → New → Define ACL → Requires Role: Admin → Submit → Repeat for 4 fields.

8. Flow Designer – Ticket Assignment:
Flow 1 (Regarding Certificates): Flow Designer → New Flow → Name: Regarding Certificate → Application: Global → Run As: System User → Trigger: Create/Update Record (Table: Operations Related, Condition: Issue = Regarding Certificates) → Action: Update Record (Assigned to Group = Certificates) → Save & Activate.
Flow 2 (Regarding Platform): Flow Designer → New Flow → Name: Regarding Platform → Application: Global → Run As: System User → Trigger: Create/Update Record (Table: Operations Related, Conditions: Issue = Unable to login to platform, 404 Error, Regarding User Expired) → Action: Update Record (Assigned to Group = Platform) → Save & Activate.

📂 Project Structure 
ABC-Ticket-Routing
│


├── Users/


│   ├── Katherine Pierce (Certificates Group)


│   ├── Manne Niranjan (Platform Group)


│


├── Groups/


│   ├── Certificates Group


│   ├── Platform Group


│


├── Roles/


│   ├── Certification_Role


│   ├── Platform_Role


│


├── Tables/


│   ├── u_operations_related


│   │   ├── Issue (Choice field)


│   │   ├── Assigned to Group


│   │   └── Other custom columns


│


├── ACLs/


│   ├── Read Access


│   ├── Write Access


│   ├── Field-Level Restrictions


│


├── Flows/


│   ├── Regarding Certificate → Assigns to Certificates Group


│   └── Regarding Platform → Assigns to Platform Group




Outcome: Automated ticket routing in ServiceNow streamlines support operations, ensures accurate ticket assignment, minimizes resolution delays, improves resource utilization, and enhances overall customer satisfaction.

