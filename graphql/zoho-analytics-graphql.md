# Zoho Analytics GraphQL Schema

## Overview

This conceptual GraphQL schema models the Zoho Analytics REST API (v2) domain for business intelligence and self-service analytics. Zoho Analytics provides workspaces, databases, tables, views, reports, dashboards, data import/export, sharing, embedding, alerting, and user/organization management through its REST API.

Reference: https://www.zoho.com/analytics/api/

## Schema Design

The schema covers the following major domain areas:

### Workspace and Organization
- `Workspace`, `WorkspaceDetails`, `WorkspaceOwner`, `WorkspaceStat`
- `OrganizationDetails`, `APIKey`, `OAuthToken`

### Database and Tables
- `Database`, `DatabaseDetails`, `DatabaseTable`
- `Table`, `TableDetails`, `TableRow`, `TableMeta`
- `Column`, `ColumnDetails`, `DataType`

### Views and Reports
- `View`, `ViewQuery`
- `Report`, `ReportDetails`, `ChartType`
- `PivotTable`, `SummaryWidget`, `KPIWidget`, `Tabular`

### Dashboards
- `Dashboard`, `DashboardDetails`, `DashboardSlide`, `DashboardURL`

### Formulas and Aggregation
- `Formula`, `AggregateFormula`, `RelatedColumn`
- `BaseAggregation`, `AggregateFunction`

### Filtering, Sorting, and Joins
- `Filter`, `FilterCriteria`, `ConditionalFilter`
- `Join`, `JoinDetails`, `SortOrder`

### Data Import and Export
- `ImportConfig`, `ImportResult`

### Sharing and Embedding
- `ShareConfig`, `ShareURL`
- `EmbedURL`, `EmbedConfig`, `Permission`

### Alerts and Webhooks
- `DataAlert`, `AlertConfig`, `AlertSchedule`, `AlertNotification`
- `Webhook`

### Miscellaneous
- `TrashBin`

## Key Queries

- `workspace(workspaceId: ID!)` — Fetch a single workspace by ID
- `workspaces` — List all workspaces
- `database(workspaceId: ID!, dbId: ID!)` — Fetch a database within a workspace
- `table(workspaceId: ID!, dbId: ID!, tableId: ID!)` — Fetch a table
- `report(workspaceId: ID!, dbId: ID!, reportId: ID!)` — Fetch a report
- `dashboard(workspaceId: ID!, dbId: ID!, dashboardId: ID!)` — Fetch a dashboard
- `view(workspaceId: ID!, dbId: ID!, viewId: ID!)` — Fetch a view
- `organization` — Fetch organization details
- `dataAlerts(workspaceId: ID!, dbId: ID!)` — List data alerts

## Key Mutations

- `createWorkspace(input: CreateWorkspaceInput!)` — Create a new workspace
- `createDatabase(workspaceId: ID!, input: CreateDatabaseInput!)` — Create a database
- `createTable(workspaceId: ID!, dbId: ID!, input: CreateTableInput!)` — Create a table
- `addColumn(workspaceId: ID!, dbId: ID!, tableId: ID!, input: AddColumnInput!)` — Add a column
- `importData(workspaceId: ID!, dbId: ID!, tableId: ID!, input: ImportDataInput!)` — Import data into a table
- `createReport(workspaceId: ID!, dbId: ID!, input: CreateReportInput!)` — Create a report
- `createDashboard(workspaceId: ID!, dbId: ID!, input: CreateDashboardInput!)` — Create a dashboard
- `shareView(workspaceId: ID!, dbId: ID!, viewId: ID!, input: ShareConfigInput!)` — Share a view
- `createDataAlert(workspaceId: ID!, dbId: ID!, input: CreateDataAlertInput!)` — Create a data alert
- `generateEmbedURL(workspaceId: ID!, dbId: ID!, viewId: ID!, input: EmbedConfigInput!)` — Generate embed URL

## Authentication

Zoho Analytics uses OAuth 2.0. The `OAuthToken` type represents access tokens. Regional endpoints are supported across eight data centers (US, EU, IN, AU, JP, CA, CN, SA).

## Source

- API Documentation: https://www.zoho.com/analytics/api/v2/
- OpenAPI Reference: https://github.com/zoho/analytics-oas
