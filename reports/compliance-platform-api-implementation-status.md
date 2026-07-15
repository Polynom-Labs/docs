# Compliance Platform API implementation status

Source baseline: backend `main` at `159b867e91873084101d172884e75e3ec3ef6094`
(2026-07-13).

Legend: 🟩 implemented in the backend; 🟨 documented integration contract, not
implemented in the backend.

| Status | API | Area | Method | Path | Current behavior |
| --- | --- | --- | --- | --- | --- |
| 🟨 Not implemented | User | External OAuth | `GET` | `/.well-known/openid-configuration` | Planned authorization-server metadata. No controller exists. |
| 🟨 Not implemented | User | External OAuth | `GET` | `/oauth/authorize` | Planned Authorization Code + PKCE entry point. No controller exists. |
| 🟨 Not implemented | User | External OAuth | `POST` | `/oauth/token` | Planned code exchange and refresh endpoint. No controller exists. |
| 🟨 Not implemented | User | External OAuth | `POST` | `/oauth/revoke` | Planned refresh-token revocation endpoint. No controller exists. |
| 🟩 Implemented | User | User context | `GET` | `/auth/me` | Returns the WorkOS-authenticated user's permission buckets and organization context. |
| 🟩 Implemented | User | Applications | `GET` | `/api/applications` | Lists organization Applications. |
| 🟩 Implemented | User | Applications | `POST` | `/api/applications` | Registers an Application. |
| 🟩 Implemented | User | Applications | `GET` | `/api/applications/{applicationId}` | Retrieves an Application by numeric ID. |
| 🟩 Implemented | User | Applications | `PATCH` | `/api/applications/{applicationId}` | Updates Application metadata. |
| 🟩 Implemented | User | Applications | `DELETE` | `/api/applications/{applicationId}` | Soft-deletes an Application. |
| 🟩 Implemented | User | Asset catalog | `GET` | `/api/assets` | Lists the existing configured asset catalog. This is not the Service API Asset model. |
| 🟩 Implemented | User | Contracts | `GET` | `/api/contracts` | Lists token and pool contracts with filters and pagination. |
| 🟩 Implemented | User | Contracts | `POST` | `/api/contracts` | Registers a contract and makes the caller its administrator. |
| 🟩 Implemented | User | Audits | `GET` | `/api/audit/contract/{contractId}` | Lists indexed audit events for a contract. |
| 🟩 Implemented | User | Organisation | `GET` | `/api/admin/org` | Returns the current WorkOS organization. |
| 🟩 Implemented | User | Organisation | `GET` | `/api/admin/team/organizations-by-email` | Lists the signed-in user's organization memberships and role labels. |
| 🟩 Implemented | User | Team | `GET` | `/api/admin/team/analytics` | Returns organization team analytics. |
| 🟩 Implemented | User | Team | `GET` | `/api/admin/team/members` | Lists team members. |
| 🟩 Implemented | User | Team | `GET` | `/api/admin/team/members/filter-options` | Lists Application and status filters for team members. |
| 🟩 Implemented | User | Team | `POST` | `/api/admin/team/invite/member` | Invites a member with optional Application access and expiry. |
| 🟩 Implemented | User | Team | `POST` | `/api/admin/team/invite/external-auditor` | Invites an external auditor with time-limited access. |
| 🟩 Implemented | User | Team | `PATCH` | `/api/admin/team/members/{id}/suspend` | Suspends a membership. |
| 🟩 Implemented | User | Team | `PATCH` | `/api/admin/team/members/{id}/reactivate` | Reactivates a membership. |
| 🟩 Implemented | User | Team | `PATCH` | `/api/admin/team/members/{id}/extend-access` | Extends external-auditor access. |
| 🟩 Implemented | User | Team | `GET` | `/api/admin/team/members/{id}/access-assignments` | Lists organization and Application permission assignments. |
| 🟩 Implemented | User | Team | `PATCH` | `/api/admin/team/members/{id}/permissions` | Updates member permissions. |
| 🟩 Implemented | User | Case requests | `GET` | `/api/applications/{foreignId}/disclosure-registry` | Lists disclosure requests for an Application. |
| 🟩 Implemented | User | Case requests | `POST` | `/api/applications/{foreignId}/case-requests/{id}/approve` | Approves a request and creates the Case when approvals are complete. |
| 🟩 Implemented | User | Case requests | `POST` | `/api/applications/{foreignId}/case-requests/{id}/close` | Rejects and closes a pending request. |
| 🟩 Implemented | User | Cases | `GET` | `/api/applications/{foreignId}/cases/worklist-summary` | Returns worklist counts. |
| 🟩 Implemented | User | Cases | `GET` | `/api/applications/{foreignId}/cases/assignable-auditors` | Lists auditors eligible for a new Case. |
| 🟩 Implemented | User | Cases | `GET` | `/api/applications/{foreignId}/cases` | Lists visible Cases and pending requests. |
| 🟩 Implemented | User | Cases | `GET` | `/api/applications/{foreignId}/cases/approved` | Lists approved Cases for an Application administrator. |
| 🟩 Implemented | User | Cases | `POST` | `/api/applications/{foreignId}/cases` | Creates a pending Case request. |
| 🟩 Implemented | User | Cases | `GET` | `/api/applications/{foreignId}/cases/{id}` | Retrieves a Case. |
| 🟩 Implemented | User | Evidence | `GET` | `/api/applications/{foreignId}/cases/{id}/transactions` | Lists interpreted transactions in the Case boundary. |
| 🟩 Implemented | User | Evidence | `GET` | `/api/applications/{foreignId}/cases/{id}/analytics` | Returns Case transaction analytics. |
| 🟩 Implemented | User | Case assignments | `GET` | `/api/applications/{foreignId}/cases/{id}/auditors` | Lists active and removed auditor assignments. |
| 🟩 Implemented | User | Case assignments | `GET` | `/api/applications/{foreignId}/cases/{id}/auditors/assignable` | Lists auditors eligible to be assigned. |
| 🟩 Implemented | User | Case assignments | `POST` | `/api/applications/{foreignId}/cases/{id}/auditors` | Adds or restores an auditor assignment. |
| 🟩 Implemented | User | Case assignments | `DELETE` | `/api/applications/{foreignId}/cases/{id}/auditors/{assignmentId}` | Soft-removes an assignment. |
| 🟩 Implemented | User | Case requests | `POST` | `/api/applications/{foreignId}/cases/requests/{id}/withdraw` | Withdraws a pending Case request. |
| 🟩 Implemented | User | Reports | `GET` | `/api/reports` | Lists organization reports. |
| 🟩 Implemented | User | Reports | `GET` | `/api/reports/{reportId}/download` | Downloads an organization report. |
| 🟩 Implemented | User | Reports | `GET` | `/api/applications/{foreignId}/reports` | Lists Application reports. |
| 🟩 Implemented | User | Reports | `GET` | `/api/applications/{foreignId}/reports/{reportId}/download` | Downloads an Application report. |
| 🟩 Implemented | User | Reports | `POST` | `/api/applications/{foreignId}/case-reports` | Generates a Case transaction-summary CSV. |
| 🟩 Implemented | User | Reports | `POST` | `/api/auditors-log/reports` | Generates an organization activity-log report. |
| 🟩 Implemented | User | Reports | `POST` | `/api/applications/{foreignId}/auditors-log/reports` | Generates an Application activity-log report. |
| 🟩 Implemented | User | Reports | `POST` | `/api/applications/{foreignId}/cases/{caseId}/auditors-log/reports` | Generates a Case activity-log report. |
| 🟩 Implemented | User | Activity log | `GET` | `/api/auditors-log` | Lists organization activity entries. |
| 🟩 Implemented | User | Activity log | `GET` | `/api/auditors-log/export.csv` | Exports organization activity as CSV. |
| 🟩 Implemented | User | Activity log | `GET` | `/api/applications/{foreignId}/auditors-log` | Lists Application activity entries. |
| 🟩 Implemented | User | Activity log | `GET` | `/api/applications/{foreignId}/auditors-log/export.csv` | Exports Application activity as CSV. |
| 🟩 Implemented | User | Activity log | `GET` | `/api/applications/{foreignId}/cases/{caseId}/auditors-log` | Lists Case activity entries. |
| 🟩 Implemented | User | Activity log | `GET` | `/api/applications/{foreignId}/cases/{caseId}/auditors-log/export.csv` | Exports Case activity as CSV. |
| 🟩 Implemented | User | API keys | `GET` | `/api/api-keys` | Lists organization key metadata without secrets. |
| 🟩 Implemented | User | API keys | `POST` | `/api/api-keys` | Creates an organization API key and returns its secret once. |
| 🟩 Implemented | User | API keys | `DELETE` | `/api/api-keys/{id}` | Revokes an organization API key. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/oauth/google/start` | Starts the Arcane interface's Google sign-in flow. Not the external OAuth authorization endpoint. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/oauth/google/complete` | Completes Google sign-in. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/oauth/google/redirect-complete` | Completes hosted redirect authentication. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/workos/organization-selection` | Completes sign-in after organization selection. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/workos/logout` | Revokes the current WorkOS session. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/magic/send` | Sends a WorkOS Magic Auth code. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/magic/verify` | Verifies a WorkOS Magic Auth code. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/reta/google/start` | Starts the Reta-specific Google sign-in flow. |
| 🟩 Implemented | User | Platform sign-in | `POST` | `/auth/reta/google/complete` | Completes the Reta-specific Google sign-in flow. |
| 🟩 Implemented | Service | Assets | `POST` | `/v1/assets` | Creates a confidential Asset and returns one per-organization auditor ElGamal public key. |
| 🟩 Implemented | Service | Assets | `GET` | `/v1/assets/{id}` | Retrieves an organization-owned confidential Asset. |
| 🟩 Implemented | Service | Assets | `PATCH` | `/v1/assets/{id}/mint` | Stores the supplied mint data, marks the Asset active, and attempts indexer registration. It does not verify the mint on-chain. |
| 🟩 Implemented | Service | Assets | `GET` | `/v1/assets/{id}/indexer-status` | Returns registration state, indexed count, and latest indexed transaction signals. |
| 🟨 Not implemented on `main` | Service | Transactions | `GET` | `/v1/assets/{id}/transactions` | Documented target contract. An organization-scoped implementation exists on `origin/conf`, but it is not merged into backend `main`. |
| 🟨 Not implemented | Service | Transactions | `GET` | `/v1/transactions/{transactionId}` | Documented target contract. No current Service API controller exists on backend `main`. |
| 🟨 Not implemented | Service | Disclosures | `POST` | `/v1/disclosures` | Documented target contract for requesting scoped disclosure. No current Service API controller exists. |
| 🟨 Not implemented | Service | Disclosures | `GET` | `/v1/disclosures/{disclosureId}` | Documented target contract for retrieving disclosure status and authorized results. No current Service API controller exists. |

## High-impact implementation gaps

1. The four external OAuth methods are not implemented. The existing Google,
   Magic Auth, organization-selection, and logout routes are Arcane-interface
   sign-in flows and do not provide an external OAuth authorization server.
2. Four of the eight documented Service API methods are not implemented on
   backend `main`. Transaction listing exists only on `origin/conf`; transaction
   retrieval and the Disclosure API remain implementation work.
3. Service API keys select an organization, but the implemented Service API
   methods do not enforce per-method API-key permissions.
4. `PATCH /v1/assets/{id}/mint` trusts the submitted mint address and deployment
   status. It does not verify the Token-2022 configuration or auditor public
   key on-chain. Indexer-registration failures are logged but do not fail the
   binding request.
5. `metadataCid` is present in the create request DTO but is not stored or
   returned by the current Asset implementation.
