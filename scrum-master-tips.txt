Smart query:

1. Query to filter out 0 remainingEstimate:
(remainingEstimate = 0 OR remainingEstimate is EMPTY) AND status in ("Development in Progress", "QA in Progress", "DEFECTS FIXING IN PROGRESS", "STAGING IN PROGRESS") AND issuetype not in (Epic) AND assignee = currentUser() AND issuetype not in (Story, "Discussions & Meetings","Discussions and Meetings", Epic)

2. Query to assigneed issues to particular user by just typing name:
assignee = 5f16e3f2b545e20015d88aa7 AND status not in ("GO LIVE!", CLOSED, Done)