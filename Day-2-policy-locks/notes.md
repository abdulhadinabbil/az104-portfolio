# Lab02b: Azure Policy & Resource Locks - Notes

## Summary
- Listed built-in policies that require tags.
- Showed details of the "Require a tag on resources" policy.
- Assigned the policy to a resource group enforcing the "Environment" tag.
- Tested compliance by trying to create a storage account without the tag (failed).
- Created a storage account with the required tag (succeeded).
- Created a resource lock on the resource group.
- Tried deleting the locked resource group and was blocked.
- Removed the lock and deleted the resource group successfully.


## Learnings
- Azure Policy enforces compliance by blocking resources that don’t meet set rules.
- Resource locks prevent accidental deletion or modification of critical resources.
- Using tags like "Environment" can help organize and control resources across teams and projects.

## Error Example
- When trying to create a storage account without the required "Environment" tag, the request was disallowed by policy with error code `RequestDisallowedByPolicy`.