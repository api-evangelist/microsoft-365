# Microsoft 365 GraphQL Schema

## Overview

This conceptual GraphQL schema represents the Microsoft 365 productivity suite APIs as exposed through Microsoft Graph, the unified REST API endpoint at `https://graph.microsoft.com/v1.0`. The schema covers identity and user management, mail, calendar, files, Teams, SharePoint, OneNote, Planner, To Do, Excel, security, and admin services.

## Source

- **API**: Microsoft Graph API
- **Base URL**: `https://graph.microsoft.com/v1.0`
- **Documentation**: https://learn.microsoft.com/en-us/graph/overview
- **API Reference**: https://learn.microsoft.com/en-us/graph/api/overview
- **Graph Explorer**: https://developer.microsoft.com/graph/graph-explorer

## Authentication

Microsoft Graph uses OAuth 2.0 and OpenID Connect for authentication via Microsoft Entra ID (formerly Azure Active Directory). Applications must register in the Azure portal and request appropriate permission scopes (delegated or application permissions) before calling the API.

## Schema Design Notes

The schema models the primary resource types surfaced by Microsoft Graph across all Microsoft 365 workloads. Key design decisions:

- **User** is the central entity; most resources belong to or are accessed through a user or group context.
- **DriveItem** represents files and folders in OneDrive and SharePoint document libraries using a unified model.
- **Teams** resources (Team, Channel, Chat, ChatMessage, Meeting) reflect the collaboration workload.
- **Mail**, **Calendar**, and **Contacts** resources mirror the Outlook workload.
- **Planner**, **ToDoList**, and **ToDoTask** cover task management.
- **WorkBook**, **WorkSheet**, **WorkRange**, **WorkTable**, **WorkChart**, and **WorkPivotTable** model Excel Online.
- **Notebook**, **Section**, **SectionGroup**, and **NotebookPage** model OneNote.
- **Application**, **ServicePrincipal**, **AppRole**, and **OAuth2Permission** model Entra ID app registrations.
- **Policy**, **ConditionalAccess**, and **Compliance** cover governance and security.
- **ActivityReport** covers usage analytics.

## Types Summary

| Category | Types |
|---|---|
| Identity & Users | User, UserPresence, Manager, DirectReport, Photo, LicenseDetail, ServicePlan, SubscribedSku, Organization, Domain, DomainDns, DirectoryObject, Group |
| Mail | Mail, Message, MessageBody, Recipient, EmailAddress, Attachment |
| Calendar | Event, CalendarView, Calendar, CalendarGroup, Occurrence, Recurrence, Room, RoomList, Reminder |
| Files | DriveItem, Drive, DriveSharedItem |
| OneNote | Notebook, NotebookPage, Section, SectionGroup, Onenote |
| Teams | TeamsApp, Chat, ChatMessage, Team, Channel, ChannelMessage, Meeting, OnlineMeeting, CallRecord, Segment, Session, Participant |
| Tasks | Planner, PlannerTask, PlannerBucket, PlannerPlan, ToDoTask, ToDoList |
| Excel | WorkBook, WorkSheet, WorkRange, WorkTable, WorkChart, WorkPivotTable |
| App Registration | Application, ServicePrincipal, OAuth2Permission, AppRole |
| Security & Admin | Policy, ConditionalAccess, Compliance, Admin, ActivityReport, APIKey, Token |

## Schema File

See `microsoft-365-schema.graphql` for the full type definitions.
