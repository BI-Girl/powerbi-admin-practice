# Row-Level Security (RLS) Governance

## Rules
- All reports with sensitive data must have RLS applied
- Dynamic RLS preferred over static for roles with 10+ members
- RLS must be tested by impersonating at least 3 user profiles before production

## Dynamic RLS Pattern
- Maintain a UserAccessMap table with columns: UserEmail, Territory
- RLS DAX filter: UserAccessMap[UserEmail] = USERPRINCIPALNAME()
- Adding a new user = data operation only, no model change needed

## Testing Checklist
- Test with a user who has full access
- Test with a user who has partial access (one region only)
- Test with a user who has no access (should see empty report, not an error)
