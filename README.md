# SAP BI Tools

Collection of SAP Business Intelligence tools and APIs for analytics, reporting, and data visualization.

**URL:** https://api.sap.com/bi-tools

## Tags

Analytics, Business Intelligence, Data Visualization, Reporting, SAP

## Timestamps

- **Created:** 2024-01-20
- **Modified:** 2026-05-02

## APIs

### SAP Analytics Cloud API

RESTful API for SAP Analytics Cloud enabling data manipulation, story creation, and model management.

- **Base URL:** https://api.sapanalytics.cloud
- **Version:** 1.0
- **Human URL:** https://help.sap.com/docs/SAP_ANALYTICS_CLOUD
- **OpenAPI:** [openapi/sap-analytics-cloud-api-openapi.yml](openapi/sap-analytics-cloud-api-openapi.yml)

**Properties:** Documentation, OpenAPI, Authentication, Rate Limits, Reference, Getting Started, Change Log

### SAP Analytics Cloud Data Export API

OData-based API for exporting fact data and master data from SAP Analytics Cloud models.

- **Base URL:** https://api.sapanalytics.cloud
- **Human URL:** https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/3ccfab3348dd407db089accb66cff9a2.html
- **OpenAPI:** [openapi/sap-analytics-cloud-data-export-api-openapi.yml](openapi/sap-analytics-cloud-data-export-api-openapi.yml)

### SAP Analytics Cloud Content Network REST API

REST API for managing content in the SAP Analytics Cloud Content Network.

- **Base URL:** https://api.sapanalytics.cloud
- **OpenAPI:** [openapi/sap-analytics-cloud-content-network-api-openapi.yml](openapi/sap-analytics-cloud-content-network-api-openapi.yml)

### SAP BusinessObjects BI Platform RESTful Web Services

REST API for SAP BusinessObjects BI Platform for managing documents, users, and scheduling reports.

- **Base URL:** https://server:port/biprws
- **Version:** 4.3
- **Human URL:** https://help.sap.com/docs/SAP_BUSINESSOBJECTS_BUSINESS_INTELLIGENCE_PLATFORM
- **OpenAPI:** [openapi/sap-businessobjects-bi-platform-api-openapi.yml](openapi/sap-businessobjects-bi-platform-api-openapi.yml)

### SAP Analytics Cloud Analytics Designer API

JavaScript-based API for building interactive analytic applications in SAP Analytics Cloud Analytics Designer.

- **Human URL:** https://help.sap.com/doc/958d4c11261f42e992e8d01a4c0dde25/release/en-US/index.html

### SAP BusinessObjects Web Intelligence RESTful Web Services API

REST API for creating, modifying, and exporting Web Intelligence reports.

- **Human URL:** https://help.sap.com/docs/SAP_BUSINESSOBJECTS_WEB_INTELLIGENCE/58f583a7643e48cf944cf554eb961f5b/45f8735d6e041014910aba7db0e91070.html

### SAP Crystal Reports RESTful Web Services API

RESTful API for SAP Crystal Reports enabling consumption and embedding in web and mobile applications.

- **Human URL:** https://help.sap.com/docs/SAP_BUSINESSOBJECTS_BUSINESS_INTELLIGENCE_PLATFORM/0945312ac81f4b63be258130d2938055/45cecf3f6e041014910aba7db0e91070.html

### SAP Datasphere API

API for SAP Datasphere (formerly SAP Data Warehouse Cloud) for data integration, modeling, and consumption.

- **Base URL:** https://datasphere-api.cfapps.eu10.hana.ondemand.com
- **Human URL:** https://help.sap.com/docs/SAP_DATASPHERE

## Artifacts

### OpenAPI Specifications

| API | File |
|-----|------|
| SAP Analytics Cloud API | [openapi/sap-analytics-cloud-api-openapi.yml](openapi/sap-analytics-cloud-api-openapi.yml) |
| SAP Analytics Cloud Data Export API | [openapi/sap-analytics-cloud-data-export-api-openapi.yml](openapi/sap-analytics-cloud-data-export-api-openapi.yml) |
| SAP Analytics Cloud Content Network REST API | [openapi/sap-analytics-cloud-content-network-api-openapi.yml](openapi/sap-analytics-cloud-content-network-api-openapi.yml) |
| SAP BusinessObjects BI Platform API | [openapi/sap-businessobjects-bi-platform-api-openapi.yml](openapi/sap-businessobjects-bi-platform-api-openapi.yml) |

### Capabilities

Workflow-oriented Naftiko capability compositions:

| Workflow | Description |
|----------|-------------|
| [Analytics Content Management](capabilities/analytics-content-management.yaml) | Story lifecycle management, Content Network publishing, and file repository governance (SAC + Content Network) |
| [Data Extraction and Reporting](capabilities/data-extraction-and-reporting.yaml) | Data export pipelines and BusinessObjects report scheduling (Data Export API + BusinessObjects) |
| [User and Access Management](capabilities/user-and-access-management.yaml) | SCIM 2.0 user and team provisioning for analytics platforms |

**Shared per-API definitions (`capabilities/shared/`):**

- [analytics-cloud.yaml](capabilities/shared/analytics-cloud.yaml) — SAP Analytics Cloud API
- [analytics-cloud-content-network.yaml](capabilities/shared/analytics-cloud-content-network.yaml) — Content Network API
- [analytics-cloud-data-export.yaml](capabilities/shared/analytics-cloud-data-export.yaml) — Data Export API
- [businessobjects-bi-platform.yaml](capabilities/shared/businessobjects-bi-platform.yaml) — BusinessObjects BI Platform API

### Rules

- [rules/sap-bi-tools-rules.yml](rules/sap-bi-tools-rules.yml) — Spectral ruleset enforcing SAP BI Tools API conventions

### JSON Schema

- [json-schema/sap-bi-tools-story-schema.json](json-schema/sap-bi-tools-story-schema.json) — SAP Analytics Cloud Story
- [json-schema/sap-bi-tools-user-schema.json](json-schema/sap-bi-tools-user-schema.json) — SAP Analytics Cloud User (SCIM 2.0)
- [json-schema/sap-bi-tools-content-item-schema.json](json-schema/sap-bi-tools-content-item-schema.json) — Content Network Item

### JSON Structure

- [json-structure/sap-bi-tools-story-structure.json](json-structure/sap-bi-tools-story-structure.json)
- [json-structure/sap-bi-tools-user-structure.json](json-structure/sap-bi-tools-user-structure.json)

### JSON-LD

- [json-ld/sap-bi-tools-context.jsonld](json-ld/sap-bi-tools-context.jsonld)

### Examples

- [examples/sap-bi-tools-list-stories-example.json](examples/sap-bi-tools-list-stories-example.json)
- [examples/sap-bi-tools-get-fact-data-example.json](examples/sap-bi-tools-get-fact-data-example.json)
- [examples/sap-bi-tools-list-users-example.json](examples/sap-bi-tools-list-users-example.json)

### Vocabulary

- [vocabulary/sap-bi-tools-vocabulary.yml](vocabulary/sap-bi-tools-vocabulary.yml)

## Common Resources

- **Portal:** https://api.sap.com
- **Getting Started:** https://developers.sap.com/topics/business-technology-platform..html
- **Documentation:** https://help.sap.com/docs/SAP_ANALYTICS_CLOUD
- **Authentication:** https://help.sap.com/docs/authentication
- **Terms of Service:** https://www.sap.com/about/legal/terms-of-use.html
- **Privacy Policy:** https://www.sap.com/about/legal/privacy.html
- **Status:** https://www.sap.com/about/trust-center/cloud-service-status.html
- **Support:** https://support.sap.com
- **Community:** https://community.sap.com
- **GitHub Organization:** https://github.com/SAP
- **Website:** https://www.sap.com
- **Sign Up:** https://developers.sap.com

## Maintainers

- **Kin Lane** — kin@apievangelist.com
