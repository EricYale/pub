# **Access Control**

- Access control is protecting important data from being read or changed  
- If an attacker has access to the raw bits of data, you can use cryptography  
- If there’s a layer of software between the attacker and the information, access control techniques can be used

## Access Control Matrix

- Columns: objects (resources, processes, files)  
- Rows: subjects (users, processes, groups)
- Cells: rights

> Common rights:
> - o: own
> - x: execute
> - r: read
> - w: write

Example:

| Subject | Diary | Calendar | Bash Script |
|--|--|--|--|
| Alice | orw | r | xr |
| Bob | rw | owr | xowr |

## Access Control Questions
- Who should be able to manage access control? (ownership model?)
- Should ACLs apply to privileged users?
- How are rights revoked?

## DAC vs MAC
- **Discretionary Access Control (DAC)**: access is determined by an owner of a resource
- **Mandatory Access Control (MAC)**: access is determined by a central authority (company, government, etc)

## Mandatory Access Control (MAC)

### Bell-Lapadula Model
- No read up: a subject can read a resource only if the security level of the object is <= the security level of the subject
- No write down: a subject can write to a resource only if the security level of the object is >= the security level of the subject
- With these two rules, information stays secret

- Each subject/object has a classification (e.g., top secret, secret, unclassified)
- Each subject/object has a set of categories (e.g. EUR, US, etc)
- A security level _dominates_ another if its classification is higher or the same, and if its categories are a superset of the other's

### Biba Model
- Processes and files have **integrity labels**
- No read down: a subject cannot read a resource of a lower integrity label
    - Example purpose: prevent user from running untrusted code
- No write up: a subject cannot write to a resource of a higher integrity label
    - Example purpose: prevent untrusted code from corrupting trusted data

#### Ex. Windows Vista
- Most files are marked with a medium integrity level
- Files downloaded from untrusted programs like Internet Explorer are marked with a low integrity level

## Role-Based Access Control (RBAC)
- Roles are collections of users with similar functions
    - Ex. Student, Staff, Alum
- Roles can be heirarchical, i.e. a role can inherit all permissions and users of another role
    - Senior role inherits junior role
    - Ex. senior role "Manager" inherits junior role "Employee" and gets all rights of "Employee"
- You can have **constrained RBAC**
    - Mutually exclusive roles: user can only be assigned to one role in a set
    - Cardinality: max # users assigned to a role, max # roles assigned to a user
    - Prerequiusite: user must have a role before being assigned to another role
        - Ex. To get role "senior engineer" you must first have role "junior engineer"

## Attribute-Based Access Control (ABAC)
- Access is granted based on attributes of the user, resource, and environment
    - Ex. for a streaming service: user's age, resource's age rating, country of user

## Flaws in Access Control
### Race conditions
- Time Of Check, Time Of Use (TOCTOU) vulnerabilities
- Ex. a malicious program could time the creation of a symlink to a sensitive file, while a privileged program is opening a non-sensitive file
