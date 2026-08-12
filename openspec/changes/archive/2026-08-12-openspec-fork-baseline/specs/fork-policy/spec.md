# Delta for fork-policy

## ADDED Requirements

### Requirement: Empty applied-delta baseline

The fork SHALL document that no IDR protocol deltas are applied at baseline.

#### Scenario: Current baseline
- GIVEN the delta registry
- WHEN checked for applied patches
- THEN the applied set is empty
