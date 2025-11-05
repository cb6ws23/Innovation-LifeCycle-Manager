# User Roles & Permissions

## Overview

This document defines the user roles in the Innovation Lifecycle Manager and their respective permissions and capabilities.

---

## Role Hierarchy

```
Administrator
    ↓
Reviewer
    ↓
Employee
```

Higher roles inherit all permissions from lower roles.

---

## Role Definitions

### Employee

**Description**: Standard user role for all company employees.

**Purpose**: Enable all employees to participate in innovation by submitting ideas and viewing initiatives.

**Who Gets This Role**:
- All company employees by default
- No special approval needed

**Key Capabilities**:
- Submit new innovation ideas
- View all initiatives (Kanban board and details)
- View own initiatives with full details
- Edit own initiatives (if not yet approved past Idea stage)
- Add comments to any initiative
- Search and filter initiatives
- Save search queries
- Attach files to own initiatives
- Receive notifications
- Use AI assistant
- View analytics dashboards (company-wide and personal)
- Export own initiatives data

**Limitations**:
- Cannot approve stage transitions
- Cannot edit others' initiatives
- Cannot change initiative ownership
- Cannot delete initiatives
- Cannot access user management
- Cannot configure system settings

---

### Reviewer

**Description**: Trusted users who evaluate and approve initiatives for stage progression.

**Purpose**: Provide governance and ensure quality standards are met before initiatives progress.

**Who Gets This Role**:
- Department heads
- Innovation committee members
- Senior technical leads
- Product managers
- Assigned by administrators

**Key Capabilities**:

*All Employee capabilities, plus:*

**Approval & Review**:
- Review stage transition requests
- Approve or reject stage progressions
- Provide feedback on initiatives
- Request additional information before approval
- View pending reviews queue

**Enhanced Visibility**:
- View all initiatives with full details
- Access detailed metrics and reports
- View audit history for all initiatives
- Export any initiative data

**Initiative Management**:
- Edit any initiative (metadata, not ownership)
- Update initiative status (ongoing, on hold, cancelled)
- Request clarifications from initiative owners
- Add reviewer notes (visible to other reviewers)

**Notifications**:
- Notified of stage transition requests requiring review
- Notified of initiatives pending in stages beyond thresholds
- Dashboard showing review workload

**Limitations**:
- Cannot delete initiatives
- Cannot change system configuration
- Cannot manage users
- Cannot reassign initiatives without owner consent

---

### Administrator

**Description**: System administrators with full access to all features and configuration.

**Purpose**: Manage the system, users, and handle exceptional cases.

**Who Gets This Role**:
- IT administrators
- Innovation program managers
- System owners
- Requires formal approval

**Key Capabilities**:

*All Employee and Reviewer capabilities, plus:*

**User Management**:
- Create, edit, delete user accounts
- Assign and revoke roles
- Deactivate user accounts
- View user activity logs
- Reset user passwords

**Initiative Management**:
- Edit any initiative (full access)
- Delete initiatives (with confirmation)
- Force stage transitions (bypass approval)
- Change initiative ownership
- Merge or split initiatives
- Archive old initiatives
- Bulk operations on initiatives

**System Configuration**:
- Configure lifecycle stages (customize if needed)
- Configure categories and tags
- Set up approval workflows
- Configure notification rules
- Manage AI assistant settings
- Configure integrations
- Set data retention policies
- Configure system-wide settings

**Advanced Analytics**:
- Access all reports and analytics
- Create custom reports
- Export all system data
- View system health metrics
- Access audit logs for all activities

**Data Management**:
- Backup and restore
- Data import/export
- Database maintenance
- Archive management

**Special Permissions**:
- Override business rules when necessary
- Emergency access to resolve issues
- System maintenance mode control

**Limitations**:
- Actions are logged and auditable
- Some destructive actions require secondary confirmation

---

## Detailed Permission Matrix

| Permission | Employee | Reviewer | Administrator |
|------------|----------|----------|---------------|
| **Initiatives - View** |
| View all initiatives (board) | ✓ | ✓ | ✓ |
| View own initiative details | ✓ | ✓ | ✓ |
| View others' initiative details | ✓ | ✓ | ✓ |
| View initiative metrics | Limited | ✓ | ✓ |
| View audit history (own) | ✓ | ✓ | ✓ |
| View audit history (all) | ✗ | ✓ | ✓ |
| **Initiatives - Create/Edit** |
| Submit new initiative | ✓ | ✓ | ✓ |
| Edit own initiative | ✓ | ✓ | ✓ |
| Edit others' initiatives | ✗ | Limited | ✓ |
| Delete initiative | ✗ | ✗ | ✓ |
| Change initiative ownership | ✗ | ✗ | ✓ |
| Bulk edit initiatives | ✗ | ✗ | ✓ |
| **Stage Transitions** |
| Request stage transition | ✓ (own) | ✓ (own) | ✓ |
| Approve stage transition | ✗ | ✓ | ✓ |
| Reject stage transition | ✗ | ✓ | ✓ |
| Force stage transition | ✗ | ✗ | ✓ |
| **Status Management** |
| Update status (own) | ✓ | ✓ | ✓ |
| Update status (others) | ✗ | ✓ | ✓ |
| Override status rules | ✗ | ✗ | ✓ |
| **Comments & Collaboration** |
| Add comments | ✓ | ✓ | ✓ |
| Edit own comments | ✓ | ✓ | ✓ |
| Delete own comments | ✓ | ✓ | ✓ |
| Delete others' comments | ✗ | ✗ | ✓ |
| Add reviewer notes | ✗ | ✓ | ✓ |
| **Attachments** |
| Upload attachments | ✓ | ✓ | ✓ |
| Download attachments | ✓ | ✓ | ✓ |
| Delete own attachments | ✓ | ✓ | ✓ |
| Delete others' attachments | ✗ | ✗ | ✓ |
| **Search & Filters** |
| Basic search | ✓ | ✓ | ✓ |
| Advanced search | ✓ | ✓ | ✓ |
| Save searches | ✓ | ✓ | ✓ |
| Share searches | ✓ | ✓ | ✓ |
| **Analytics & Reports** |
| View personal dashboard | ✓ | ✓ | ✓ |
| View company dashboard | ✓ | ✓ | ✓ |
| View executive dashboard | ✗ | ✓ | ✓ |
| Export own data | ✓ | ✓ | ✓ |
| Export all data | ✗ | ✓ | ✓ |
| Create custom reports | ✗ | ✗ | ✓ |
| **AI Assistant** |
| Use AI assistant | ✓ | ✓ | ✓ |
| View AI suggestions | ✓ | ✓ | ✓ |
| Provide AI feedback | ✓ | ✓ | ✓ |
| Configure AI settings | ✗ | ✗ | ✓ |
| **Notifications** |
| Receive notifications | ✓ | ✓ | ✓ |
| Configure own preferences | ✓ | ✓ | ✓ |
| Configure system notifications | ✗ | ✗ | ✓ |
| **User Management** |
| View user list | ✗ | ✗ | ✓ |
| Create users | ✗ | ✗ | ✓ |
| Edit users | ✗ | ✗ | ✓ |
| Delete users | ✗ | ✗ | ✓ |
| Assign roles | ✗ | ✗ | ✓ |
| **System Administration** |
| Configure stages | ✗ | ✗ | ✓ |
| Configure workflows | ✗ | ✗ | ✓ |
| Configure categories | ✗ | ✗ | ✓ |
| System settings | ✗ | ✗ | ✓ |
| View system logs | ✗ | ✗ | ✓ |
| Database management | ✗ | ✗ | ✓ |

---

## Role Assignment Rules

### Default Assignment
- All new users automatically get **Employee** role
- Users can request role upgrades through admin

### Reviewer Assignment Criteria
Candidates should have:
- At least 1 year with company
- Leadership or senior technical position
- Understanding of innovation process
- Demonstrated judgment and decision-making
- Availability to review initiatives promptly

### Administrator Assignment Criteria
Candidates should have:
- Formal responsibility for innovation program or IT systems
- Training on system administration
- Understanding of data privacy and security
- Approval from program sponsor

### Role Changes
- Role upgrades require administrator approval
- Role downgrades can be self-requested or admin-initiated
- Role changes are logged in audit trail
- Users notified of role changes

---

## Approval Workflows by Role

### Stage Transition Approvals

| From Stage | To Stage | Required Approver Role | Typical Approver |
|------------|----------|------------------------|------------------|
| Idea | Concept | Reviewer | Department Lead |
| Concept | POV | Reviewer | Innovation Committee Member |
| POV | Prototype | Reviewer | Technical Lead + Budget Owner |
| Prototype | POC | Reviewer | Technical Review Board |
| POC | MVP | Reviewer | Steering Committee Member |
| MVP | Pilot | Reviewer | Executive Sponsor |
| Pilot | Product | Reviewer | Executive Leadership |
| Product | Scaled | Administrator | Program Director |

### Special Approvals

**Budget Thresholds**:
- < $10K: Single Reviewer
- $10K - $50K: Two Reviewers
- > $50K: Reviewer + Administrator

**Status Changes**:
- Ongoing → On Hold: Owner (with reason)
- Ongoing → Cancelled: Reviewer approval (with reason)
- On Hold → Cancelled: Reviewer approval
- Any → Rolled Out: Reviewer approval

---

## Initiative Ownership Rules

### Owner Capabilities
Regardless of role, initiative owners have enhanced permissions for their initiatives:
- Full edit access (within stage constraints)
- Request stage transitions
- Add/remove attachments
- Update metrics
- Change status (with rules)
- Assign team members (future feature)

### Ownership Transfer
- Current owner can transfer to anyone
- Reviewers can suggest transfer
- Administrators can force transfer
- Both parties notified of transfer
- Transfer logged in audit trail

### Ownership Scenarios

**Employee as Owner**:
- Can manage initiative
- Cannot self-approve transitions
- Must follow standard approval workflow

**Reviewer as Owner**:
- Can manage initiative
- Cannot self-approve own transitions (conflict of interest)
- Another reviewer must approve

**Administrator as Owner**:
- Full management capabilities
- Can force transitions (logged)
- Should still follow workflow for governance

---

## Security & Access Control

### Authentication
- All users must authenticate
- Session management (30-minute timeout)
- Password complexity requirements
- Multi-factor authentication (optional, recommended for admins)

### Authorization
- Role-based access control (RBAC)
- Permissions checked on every action
- API endpoints protected by role
- Database queries filtered by permissions

### Data Privacy
- Users can only see data they have permission to access
- Personal data protected
- Audit logs track all data access
- GDPR compliance considerations for user data

### Audit Trail
- All privileged actions logged
- Administrator actions specially flagged
- Logs include: who, what, when, why
- Logs retained per retention policy

---

## Role-Based Dashboards

### Employee Dashboard
- My submitted initiatives
- Initiatives I'm watching
- Recent activity feed
- Notifications
- Quick submit button
- Personal statistics (ideas submitted, success rate)

### Reviewer Dashboard
- Pending reviews (priority)
- Recent approvals/rejections
- Initiatives I'm tracking
- Department initiatives
- Review workload statistics
- Escalations and overdue reviews

### Administrator Dashboard
- System health metrics
- User activity statistics
- Initiative pipeline overview
- Recent system changes
- Pending administrative tasks
- Data quality issues
- System alerts

---

## Special Considerations

### Guest/External Access (Future)
For demo purposes, consider:
- Read-only guest accounts
- External partner accounts (limited scope)
- Public portfolio view (sanitized data)

### Delegation
- Reviewers can delegate reviews to others
- Administrators can assign administrative tasks
- Delegation is logged

### Emergency Access
- Administrators can access any data in emergencies
- Emergency access is specially logged
- Requires post-incident review

### Role Combinations
Users can potentially have multiple roles:
- Primary role determines default permissions
- Special assignments can grant temporary additional permissions
- All permissions logged

---

## Implementation Notes

### For Development
- Use established authentication library (e.g., Auth0, Firebase Auth)
- Implement role checks at both API and UI levels
- Cache permissions for performance
- Test permission boundaries thoroughly
- Implement least-privilege principle

### For Testing
- Create test users for each role
- Test permission boundaries (try to do unauthorized actions)
- Test role transitions
- Test edge cases (ownership scenarios, etc.)

### For Demo
- Pre-create users in each role
- Demo account: admin/reviewer/employee credentials
- Sample data showing different ownership scenarios
- Clear visual indication of role in UI

---

## Summary

This role model provides:
- **Clear separation** of capabilities and responsibilities
- **Security** through least-privilege access
- **Flexibility** for different organizational structures
- **Scalability** as organization grows
- **Governance** through approval workflows
- **Accountability** through audit trails

The three-tier role structure balances simplicity with necessary governance for innovation management.
