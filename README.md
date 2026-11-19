Database Architecture & Multi-Tenant Isolation

Responsibilities

Responsible for MongoDB database architecture, tenant management, customer management, and strict multi-tenant data isolation.

Technology Stack

Node.js

Express.js

MongoDB

Mongoose

1. Database Architecture

Designed Tenant and Customer schemas using Mongoose.

Implemented schema validation.

Added timestamps for database records.

Created database indexes for efficient queries.

Implemented a compound unique index on tenantId and email.

2. Tenant Management

Created Tenant model.

Implemented tenant context middleware.

Validated tenant ID using MongoDB ObjectId.

Supported tenant identification through authenticated request context.

Supported x-tenant-id header for development and testing.

Restricted default tenant fallback to development mode.

3. Active Tenant Validation

Implemented requireActiveTenant middleware.

Verified tenant existence and active status.

Blocked requests from inactive tenants.

Applied tenant validation before customer operations.

4. Customer Management (CRUD APIs)

Method

Endpoint

Description

POST

/api/v1/customers

Create customer

GET

/api/v1/customers

Get all customers

GET

/api/v1/customers/:id

Get customer by ID

PUT

/api/v1/customers/:id

Update customer

DELETE

/api/v1/customers/:id

Delete customer

5. Multi-Tenant Data Isolation

Filtered customer records using tenantId.

Prevented one tenant from accessing another tenant's customers.

Validated customer ownership before invoice creation.

Restricted customer updates and deletion to the owning tenant.

6. Database Seed Scripts

seedInactiveTenant.js

seedSecondTenant.js

seedTenantCustomers.js

7. Testing

Verified the following security scenarios:

Missing tenant ID – PASS

Valid tenant access – PASS

Inactive tenant protection – PASS

Cross-tenant customer access – PASS

Invalid tenant ID – PASS

Automated Test Results

Total tests: 39

Passed: 39

Failed: 0

Test suites: 10

Implementation Status

Member 2 database architecture, customer CRUD operations, tenant validation, and multi-tenant isolation implemented and tested.