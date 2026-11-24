# Jira Smart Queries & Scrum Tips

## Useful Jira Query Language (JQL) Filters

### 1. Filter Issues with Zero or Empty Remaining Estimate
Finds active in-progress issues assigned to the current user where estimates have not been updated:

```sql
(remainingEstimate = 0 OR remainingEstimate is EMPTY)
  AND status in ("Development in Progress", "QA in Progress", "DEFECTS FIXING IN PROGRESS", "STAGING IN PROGRESS")
  AND issuetype not in (Epic)
  AND assignee = currentUser()
  AND issuetype not in (Story, "Discussions & Meetings", "Discussions and Meetings", Epic)
```

---

### 2. Filter Active Assigned Issues for a User (by User ID)
Retrieves all open and active issues assigned to a specific user identifier:

```sql
assignee = 5f16e3f2b545e20015d88aa7 AND status not in ("GO LIVE!", CLOSED, Done)
```
