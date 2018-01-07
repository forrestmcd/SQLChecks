# Database level checks

In all cases if the config value is not present the test will be skipped.

## Max transaction log fixed growth
Reports on any database which has a fixed growth larger than the config value.

As the log is zeroed out before use it can be a time consuming operation.  When the log is full and an auto-grow is requested all no writes can complete until the grow is completed, and so capping the size of the growth to a value less than 1GB is suggested.

```json
"MaxTLogAutoGrowthInKB": 999000
``` 

## Transaction log with percentage growth
Reports on any database with a percentage growth configured.

If the config value is set to false the check will be skipped.

```json
"CheckForPercentageGrowthLogFiles": true
```

## Required DDL trigger
Reports on any database which does not contain the specified DDL trigger.  Excludes system databases and any databases with a memory optimised filegroup.

If you had a trigger which logged all DDL changes, you might mandate its usage in some of your environments and check for compliance with this test.

```json
"MustHaveDDLTrigger": "TR_LogDDLChanges"
``` 

## Oversided indexes
Reports on any database which has oversized indexes (potential key size larger than 1700 bytes).

If the config value is set to false the check will be skipped.

```json
"CheckForOversizedIndexes": true
```