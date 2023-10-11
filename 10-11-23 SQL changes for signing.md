 -- SQL From Ric 
 ```SQL
 INSERT INTO document.Action_CoreObject ( ActionID, CoreObjectID) Values (22, 5)

INSERT INTO document.Action_CoreObject ( ActionID, CoreObjectID) Values (23,6)

INSERT INTO document.Action_CoreObject ( ActionID, CoreObjectID) Values (24,5)

INSERT INTO document.Action_CoreObject ( ActionID, CoreObjectID) Values (25, 5)

​

​

INSERT INTO Document.ACTION_Report(ActionID, ReportID, ReportVersion) Values (22, 9, 1)

INSERT INTO Document.ACTION_Report(ActionID, ReportID, ReportVersion) Values (23, 8, 1)

INSERT INTO Document.ACTION_Report(ActionID, ReportID, ReportVersion) Values (24, 22, 1)

INSERT INTO Document.ACTION_Report(ActionID, ReportID, ReportVersion) Values (25, 19, 1)

​

​

INSERT INTO document.Report_IndexingValue ( IndexingValueID, ReportID, Deleted, FieldID) Values(8, 11, 0, 1)

INSERT INTO document.Report_IndexingValue ( IndexingValueID, ReportID, Deleted, FieldID) Values(8, 15, 0, 1)

INSERT INTO document.Report_IndexingValue ( IndexingValueID, ReportID, Deleted, FieldID) Values(8, 14, 0, 1)

INSERT INTO document.Report_IndexingValue ( IndexingValueID, ReportID, Deleted, FieldID) Values(8, 8, 0, 1)

INSERT INTO document.Report_IndexingValue ( IndexingValueID, ReportID, Deleted, FieldID) Values(5, 23,0,1)

INSERT INTO document.Report_IndexingValue ( IndexingValueID, ReportID, Deleted, FieldID) Values(4, 23, 0, 1)
```
 
--SQL ran to get things working on test
```SQL
CREATE OR ALTER  PROCEDURE Document.GetWarrantApprovedValues

	@DetailsOffenseID INT = NULL

AS

BEGIN

	SET NOCOUNT ON;

​

    SELECT DetailsID, Details_OffenseID AS DetailsOffenseID FROM Warrant.Details_Offense

	WHERE Details_OffenseID = @DetailsOffenseID

​

END

​```

-- Delete postprocess steps for CW Application associated with Warrant approved
```SQL
DELETE FROM [Document].[Action_Report_Postprocess] WHERE ([Action_ReportID] = '21' AND [ExchangeName] = 'attachments.exchange' AND [QueueName] = 'attachments.feithsync.standard' AND [RoutingKey] = 'attachments.feithsync.standard' AND [Ordinal] = '1' AND [ExchangeType] = 'direct') OR ([Action_ReportID] = '21' AND [ExchangeName] = 'warrant.email.exchange' AND [QueueName] = 'warrantapplication.email.queue' AND [RoutingKey] = 'warrantapplication.email.route.standard' AND [Ordinal] = '2' AND [ExchangeType] = 'direct');
```

```SQL

-- delete criminal application as part of warrant approved action DOESNT NEED TO RUN ON DEV

DELETE FROM [Document].[Action_Report] WHERE ([Action_ReportID] = '21');

​```

```SQL
-- CW application SP

CREATE OR ALTER  PROCEDURE Document.GetWarrantApplicationValues

	@DetailsID INT = NULL

AS

BEGIN

	SET NOCOUNT ON;

​

    SELECT DetailsID FROM Warrant.Details

	WHERE DetailsID = @DetailsID

​

END
```

​-- Add Warrant application kickoff action
```SQL
INSERT INTO [Document].[Action] ([Name],[Created],[Alias],[StoredProcedureName]) VALUES (N'Warrant Application Finalized Action','2023-10-11 22:39:10.327',N'WarrantApplicationFinalizedKickoff',N'Document.GetWarrantApplicationValues');
```

-- set CW application SP to use a detailsID centric call vs details offense (if above is not needed)
```SQL
UPDATE [Document].[Action] SET [StoredProcedureName] = N'Document.GetWarrantApplicationValues' WHERE [ActionID] = (SELECT TOP(1) ActionID FROM Document.[Action] WHERE [Name] LIKE 'Warrant approved by Judge')
```

​

-- NOTE: need to remove details offense indexing value from feith FC (PROD)


-- remove details offense as a parameter for CW Application report

```SQL
DECLARE @Param_ReportID INT = (SELECT TOP(1) ID FROM Report.Metadata WHERE [Name] LIKE 'CRIMINAL_APPLICATION')

DECLARE @Param_ParamID INT = (SELECT TOP(1) ParameterID FROM Document.Parameter WHERE [Name] LIKE 'Details Offense ID')

DELETE FROM [Document].[Report_Parameter] WHERE ([Report_ParameterID] = (SELECT TOP(1) Report_ParameterID FROM Document.Report_Parameter WHERE ReportID = @Param_ReportID AND ParameterID = @Param_ParamID));
```


-- remove details offense as indexing value for CW Application

```SQL
DECLARE @Indexing_ReportID INT = (SELECT TOP(1) ID FROM Report.Metadata WHERE [Name] LIKE 'CRIMINAL_APPLICATION')

DECLARE @Indexing_IndexID INT = (SELECT TOP(1) IndexingValueID FROM Document.IndexingValues WHERE [Name] LIKE 'Details Offense ID')

DELETE FROM [Document].[Report_IndexingValue] WHERE ([Report_IndexingValueID] = (SELECT TOP(1) Report_IndexingValueID FROM Document.Report_IndexingValue WHERE ReportID = @Indexing_ReportID AND IndexingValueID = @Indexing_IndexID));
```

​
-- ADD POST PROCESSING STEPS TO CRIMINAL WARRANT APPLICATION

```SQL
DECLARE @ActionID INT = (SELECT TOP(1) ActionID FROM Document.[Action] WHERE [Name] LIKE 'Warrant Application Finalized Action')

DECLARE @ReportID INT = (SELECT TOP(1) ID FROM Report.Metadata WHERE [Name] LIKE 'CRIMINAL_APPLICATION')

​

DECLARE @ActionReportID INT = (SELECT TOP(1) Action_ReportID FROM Document.Action_Report WHERE ReportID = @ReportID AND ActionID = @ActionID)

INSERT INTO Document.Action_Report_Postprocess

(Action_ReportID, ExchangeName, QueueName, RoutingKey, Ordinal)

VALUES

(@ActionReportID, 'attachments.exchange', 'attachments.feithsync.standard', 'attachments.feithsync.standard', 1)
​

INSERT INTO Document.Action_Report_Postprocess

(Action_ReportID, ExchangeName, QueueName, RoutingKey, Ordinal)

VALUES

(@ActionReportID, 'warrant.email.exchange', 'warrant.email.queue', 'warrant.email.route.standard', 2)
```

-- delete upload check entry for warrant application 

-- make sure report_type etc is setup for WARRANT RECALL