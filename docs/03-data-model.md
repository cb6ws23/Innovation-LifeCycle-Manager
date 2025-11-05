# Data Model

## Overview

This document defines the data structures for the Innovation Lifecycle Manager application.

---

## Core Entities

### Initiative

The central entity representing an innovation idea/project throughout its lifecycle.

#### Fields

| Field Name | Type | Required | Description | Stage Introduced |
|------------|------|----------|-------------|------------------|
| **id** | UUID | Yes | Unique identifier | Idea |
| **title** | String(200) | Yes | Short, descriptive title | Idea |
| **description** | Text | Yes | Detailed description of the innovation | Idea |
| **problemStatement** | Text | Yes | What problem does this solve? | Idea |
| **submitterId** | UUID | Yes | User who submitted the idea | Idea |
| **submissionDate** | DateTime | Yes | When idea was submitted (auto) | Idea |
| **currentStage** | Enum | Yes | Current lifecycle stage | Idea |
| **status** | Enum | Yes | Current status (ongoing, on hold, etc.) | Idea |
| **ownerId** | UUID | Yes | Current owner/champion | Idea |
| **category** | Enum | Yes | Primary category | Idea |
| **expectedBusinessImpact** | Enum | Yes | High/Medium/Low | Idea |
| **targetUsers** | Text | No | Who will benefit? | Concept |
| **solutionApproach** | Text | No | High-level how to solve it | Concept |
| **budgetEstimate** | Decimal | No | Initial budget estimate | Concept |
| **actualSpend** | Decimal | No | Actual money spent (tracked) | POC |
| **expectedROI** | Decimal | No | Expected return on investment | POV |
| **realizedROI** | Decimal | No | Actual ROI achieved | Pilot |
| **targetCompletionDate** | Date | No | Expected completion date | POV |
| **departments** | Array | No | Affected departments | Concept |
| **tags** | Array | No | Free-form tags | Idea |
| **technologyTags** | Array | No | Technology-related tags | Concept |
| **strategicAlignment** | String | No | Link to company strategy | Concept |
| **riskLevel** | Enum | No | High/Medium/Low risk assessment | POV |
| **successMetrics** | Text | No | KPIs and success criteria | POV |
| **createdAt** | DateTime | Yes | Record creation timestamp (auto) | Idea |
| **updatedAt** | DateTime | Yes | Last update timestamp (auto) | Idea |
| **lastStageChangeDate** | DateTime | No | When moved to current stage | Idea |

#### Enumerations

**Stage**:
- IDEA
- CONCEPT
- POV
- PROTOTYPE
- POC
- MVP
- PILOT
- PRODUCT
- SCALED
- RETIRED

**Status**:
- ONGOING
- ON_HOLD
- CANCELLED
- ROLLED_OUT
- UNDER_REVIEW

**Category**:
- TECHNOLOGY_INNOVATION
- PROCESS_IMPROVEMENT
- PRODUCT_DEVELOPMENT
- SERVICE_ENHANCEMENT
- BUSINESS_MODEL_INNOVATION
- OTHER

**BusinessImpact**:
- HIGH
- MEDIUM
- LOW

**RiskLevel**:
- HIGH
- MEDIUM
- LOW

---

### User

Represents system users (employees).

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **email** | String(255) | Yes | Email address (unique) |
| **firstName** | String(100) | Yes | First name |
| **lastName** | String(100) | Yes | Last name |
| **department** | String(100) | No | Department name |
| **role** | Enum | Yes | User role in system |
| **isActive** | Boolean | Yes | Account active status |
| **createdAt** | DateTime | Yes | Account creation date |
| **lastLoginAt** | DateTime | No | Last login timestamp |

#### Enumerations

**Role**:
- EMPLOYEE (can submit ideas, view initiatives)
- REVIEWER (can approve stage transitions)
- ADMIN (full system access)

---

### Comment

Comments and discussions on initiatives.

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **initiativeId** | UUID | Yes | Related initiative |
| **userId** | UUID | Yes | Comment author |
| **content** | Text | Yes | Comment text |
| **commentType** | Enum | No | Type of comment |
| **createdAt** | DateTime | Yes | Creation timestamp |
| **updatedAt** | DateTime | Yes | Last edit timestamp |
| **isEdited** | Boolean | Yes | Whether comment was edited |

#### Enumerations

**CommentType**:
- GENERAL
- APPROVAL_FEEDBACK
- REJECTION_REASON
- STATUS_CHANGE_REASON
- QUESTION
- ANSWER

---

### Attachment

Files attached to initiatives.

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **initiativeId** | UUID | Yes | Related initiative |
| **uploadedBy** | UUID | Yes | User who uploaded |
| **fileName** | String(255) | Yes | Original file name |
| **fileSize** | Integer | Yes | Size in bytes |
| **fileType** | String(100) | Yes | MIME type |
| **storagePath** | String(500) | Yes | Path to file in storage |
| **description** | String(500) | No | File description |
| **uploadedAt** | DateTime | Yes | Upload timestamp |
| **version** | Integer | Yes | Version number (for tracking updates) |

---

### StageTransitionRequest

Tracks requests to move initiatives between stages.

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **initiativeId** | UUID | Yes | Related initiative |
| **requestedBy** | UUID | Yes | User requesting transition |
| **fromStage** | Enum | Yes | Current stage |
| **toStage** | Enum | Yes | Requested target stage |
| **justification** | Text | Yes | Why should it move? |
| **requestDate** | DateTime | Yes | When requested |
| **reviewerId** | UUID | No | Assigned reviewer |
| **reviewDate** | DateTime | No | When reviewed |
| **status** | Enum | Yes | Request status |
| **reviewNotes** | Text | No | Reviewer feedback |

#### Enumerations

**RequestStatus**:
- PENDING
- APPROVED
- REJECTED
- WITHDRAWN

---

### AuditLog

Complete history of changes to initiatives.

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **initiativeId** | UUID | Yes | Related initiative |
| **userId** | UUID | Yes | User who made change |
| **eventType** | Enum | Yes | Type of change |
| **fieldChanged** | String(100) | No | Which field changed |
| **oldValue** | Text | No | Previous value |
| **newValue** | Text | No | New value |
| **description** | Text | No | Human-readable description |
| **timestamp** | DateTime | Yes | When change occurred |
| **metadata** | JSON | No | Additional context |

#### Enumerations

**EventType**:
- CREATED
- FIELD_UPDATED
- STAGE_CHANGED
- STATUS_CHANGED
- OWNER_CHANGED
- COMMENT_ADDED
- ATTACHMENT_ADDED
- ATTACHMENT_REMOVED
- TRANSITION_REQUESTED
- TRANSITION_APPROVED
- TRANSITION_REJECTED

---

### Notification

User notifications for various events.

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **userId** | UUID | Yes | Recipient user |
| **initiativeId** | UUID | No | Related initiative (if applicable) |
| **type** | Enum | Yes | Notification type |
| **title** | String(200) | Yes | Notification title |
| **message** | Text | Yes | Notification content |
| **actionUrl** | String(500) | No | Link to related item |
| **isRead** | Boolean | Yes | Read status |
| **createdAt** | DateTime | Yes | Creation timestamp |
| **readAt** | DateTime | No | When marked as read |
| **priority** | Enum | Yes | Notification priority |

#### Enumerations

**NotificationType**:
- INITIATIVE_ASSIGNED
- TRANSITION_REQUESTED
- TRANSITION_APPROVED
- TRANSITION_REJECTED
- STATUS_CHANGED
- COMMENT_ADDED
- OWNERSHIP_TRANSFERRED
- REMINDER

**Priority**:
- HIGH
- MEDIUM
- LOW

---

### Metric

Time-series metrics for initiatives.

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **initiativeId** | UUID | Yes | Related initiative |
| **metricType** | Enum | Yes | Type of metric |
| **value** | Decimal | Yes | Metric value |
| **unit** | String(50) | No | Unit of measurement |
| **recordedAt** | DateTime | Yes | When metric was recorded |
| **recordedBy** | UUID | Yes | User who recorded |
| **notes** | Text | No | Additional context |

#### Enumerations

**MetricType**:
- BUDGET_ESTIMATE
- ACTUAL_SPEND
- EXPECTED_ROI
- REALIZED_ROI
- TIME_IN_STAGE
- USER_COUNT
- CUSTOMER_SATISFACTION
- KPI_ACHIEVEMENT
- CUSTOM

---

### SavedSearch

User's saved search queries.

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **userId** | UUID | Yes | Owner of saved search |
| **name** | String(100) | Yes | Search name |
| **searchQuery** | JSON | Yes | Search parameters |
| **isPublic** | Boolean | Yes | Visible to others? |
| **createdAt** | DateTime | Yes | Creation timestamp |
| **lastUsedAt** | DateTime | No | Last execution timestamp |

---

### AIInteraction

Tracks AI assistant interactions for learning and audit.

#### Fields

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| **id** | UUID | Yes | Unique identifier |
| **userId** | UUID | Yes | User who interacted |
| **initiativeId** | UUID | No | Related initiative (if applicable) |
| **interactionType** | Enum | Yes | Type of AI interaction |
| **userQuery** | Text | Yes | User's question/request |
| **aiResponse** | Text | Yes | AI's response |
| **wasFeedbackPositive** | Boolean | No | User feedback on response |
| **timestamp** | DateTime | Yes | When interaction occurred |

#### Enumerations

**AIInteractionType**:
- DUPLICATE_CHECK
- IMPROVEMENT_SUGGESTION
- SIMILAR_INITIATIVES
- SUCCESS_PREDICTION
- STAKEHOLDER_SUGGESTION
- RISK_ASSESSMENT
- GENERAL_QUERY

---

## Relationships

### Initiative Relationships
- **Initiative** → **User** (submitter): Many-to-One
- **Initiative** → **User** (owner): Many-to-One
- **Initiative** → **Comment**: One-to-Many
- **Initiative** → **Attachment**: One-to-Many
- **Initiative** → **StageTransitionRequest**: One-to-Many
- **Initiative** → **AuditLog**: One-to-Many
- **Initiative** → **Metric**: One-to-Many
- **Initiative** → **Notification**: One-to-Many
- **Initiative** → **AIInteraction**: One-to-Many

### User Relationships
- **User** → **Initiative** (owned): One-to-Many
- **User** → **Comment**: One-to-Many
- **User** → **Notification**: One-to-Many
- **User** → **SavedSearch**: One-to-Many
- **User** → **StageTransitionRequest** (reviewer): One-to-Many

---

## Calculated Fields

These fields are computed on-the-fly, not stored:

| Field Name | Calculation | Description |
|------------|-------------|-------------|
| **ageInDays** | Current Date - Submission Date | How old is the initiative? |
| **timeInCurrentStage** | Current Date - Last Stage Change Date | Days in current stage |
| **stageConversionRate** | Initiatives advanced / Total in stage | Success rate per stage |
| **averageTimePerStage** | Sum of time in stage / Count | Typical duration per stage |
| **totalBudgetSpent** | Sum of actual spend records | Total money invested |
| **budgetVariance** | Budget Estimate - Actual Spend | Over/under budget |

---

## Data Validation Rules

### Initiative
- Title: 10-200 characters, required
- Description: 50-5000 characters, required
- Problem Statement: 20-2000 characters, required
- Budget Estimate: Must be positive number
- Expected ROI: Must be number (can be negative)
- Target Completion Date: Must be future date
- Departments: At least one if multi-department impact

### Stage Transitions
- Cannot skip stages (except with special approval)
- Must meet stage-specific requirements
- Requires approval from appropriate role

### Comments
- Content: 1-2000 characters, required
- Cannot be empty or whitespace-only

### Attachments
- File size: Max 50MB per file
- Allowed types: PDF, DOC, DOCX, XLS, XLSX, PPT, PPTX, PNG, JPG, JPEG, GIF
- Total attachments per initiative: Max 20

---

## Indexing Strategy

For optimal query performance:

### Initiative Indexes
- Primary Key: `id`
- Foreign Keys: `submitterId`, `ownerId`
- Common Filters: `currentStage`, `status`, `category`, `submissionDate`
- Search: Full-text index on `title`, `description`, `problemStatement`
- Composite: `(currentStage, status)`, `(ownerId, currentStage)`

### Audit Log Indexes
- Primary Key: `id`
- Foreign Keys: `initiativeId`, `userId`
- Time-based: `timestamp` (descending)
- Composite: `(initiativeId, timestamp)`

### Notification Indexes
- Primary Key: `id`
- Foreign Key: `userId`
- Common Filters: `isRead`, `createdAt`
- Composite: `(userId, isRead, createdAt)`

---

## Data Retention Policy

| Entity | Retention Period | Archive Strategy |
|--------|------------------|------------------|
| Initiative | Indefinite | None (historical value) |
| Comment | Indefinite | None (part of initiative history) |
| Attachment | Indefinite | Archive to cold storage after 2 years |
| AuditLog | 7 years | Archive to cold storage after 1 year |
| Notification | 90 days | Delete after 90 days |
| AIInteraction | 1 year | Aggregate and anonymize for ML training |

---

## Example Initiative JSON

```json
{
  "id": "123e4567-e89b-12d3-a456-426614174000",
  "title": "AI-Powered Customer Support Chatbot",
  "description": "Develop an intelligent chatbot to handle common customer inquiries...",
  "problemStatement": "Customer support team is overwhelmed with repetitive questions...",
  "submitterId": "user-123",
  "submissionDate": "2024-01-15T10:30:00Z",
  "currentStage": "POC",
  "status": "ONGOING",
  "ownerId": "user-456",
  "category": "TECHNOLOGY_INNOVATION",
  "expectedBusinessImpact": "HIGH",
  "targetUsers": "Customer support team and end customers",
  "solutionApproach": "Build chatbot using Claude AI with knowledge base integration",
  "budgetEstimate": 75000.00,
  "actualSpend": 45000.00,
  "expectedROI": 2.5,
  "targetCompletionDate": "2024-09-30",
  "departments": ["Customer Support", "IT", "Product"],
  "tags": ["automation", "customer-experience", "efficiency"],
  "technologyTags": ["AI", "Claude", "NLP", "API"],
  "strategicAlignment": "Digital Transformation Initiative 2024",
  "riskLevel": "MEDIUM",
  "successMetrics": "Reduce support ticket volume by 30%, improve response time to under 2 minutes",
  "createdAt": "2024-01-15T10:30:00Z",
  "updatedAt": "2024-06-20T14:22:00Z",
  "lastStageChangeDate": "2024-05-15T09:00:00Z"
}
```

---

## Summary

This data model provides:
- **Comprehensive tracking** of all initiative information
- **Flexible categorization** through tags and categories
- **Complete audit trail** for governance
- **Metric tracking** for data-driven decisions
- **Scalable structure** that can grow with needs
- **Performance optimization** through proper indexing

The model balances detail with simplicity, capturing essential information at each lifecycle stage while remaining manageable for a demo application.
