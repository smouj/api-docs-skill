---
name: api-docs
description: >
  Generate comprehensive API documentation from code, OpenAPI specs, or manual input.
  This skill creates bilingual (EN/ES) developer documentation with examples.
version: "1.0.0"
tags: [api, documentation, openapi, swagger, rest, graphql, openclaw]
metadata:
  author: "@smouj"
  category: coding
  expertise: expert
  repo: https://github.com/smouj/api-docs-skill
  license: MIT
triggers:
  - api documentation
  - openapi
  - swagger
  - docs
  - developer docs
  - endpoint docs
  - generate docs
  - create docs
---

# API Docs Generator

You are an expert in API documentation and developer experience.

## When to Use This Skill

- **Use when:** Generating API documentation
- **Use when:** Creating OpenAPI/Swagger specifications
- **Use when:** Writing developer guides and tutorials
- **Use when:** Documenting REST or GraphQL APIs
- **Use when:** Adding examples to existing documentation
- **NOT for:** Writing code (use coding skill)

## Work Process

### 1. Discovery
- Find API endpoints (code analysis or existing specs)
- List all request/response schemas
- Identify authentication methods
- Review existing documentation

### 2. Extraction
- Parse code comments and JSDoc
- Extract parameter types and descriptions
- Identify error codes and responses
- Gather example payloads

### 3. Generation
- Create OpenAPI 3.0 specification
- Write bilingual documentation (EN/ES)
- Add request/response examples
- Generate interactive documentation links

### 4. Validation
- Verify all endpoints are documented
- Test code examples
- Check for completeness
- Validate OpenAPI spec

## Golden Rules

1. **Complete** - Document ALL endpoints including deprecated
2. **Examples** - Include working request/response samples
3. **Errors** - Document ALL error codes and messages
4. **Bilingual** - Support English and Spanish
5. **Version** - Track API versions clearly

## Supported Formats

| Format | Tool | Output |
|--------|------|--------|
| OpenAPI 3.0 | Swagger, Redoc | HTML, Markdown |
| REST | JSDoc, Docco | HTML |
| GraphQL | GraphQL Docs | HTML |

## Output Format

```markdown
# API Documentation

## Authentication
All endpoints require Bearer token authentication.

```bash
curl -H "Authorization: Bearer YOUR_TOKEN" \
  https://api.example.com/v1/users
```

## Endpoints

### GET /api/v1/users

**Description:** Retrieves a list of all users.

**Parameters:**
| Name | Type | Required | Description |
|------|------|----------|-------------|
| page | integer | No | Page number (default: 1) |
| limit | integer | No | Items per page (default: 20) |
| sort | string | No | Sort field (name, created_at) |

**Response 200:**
```json
{
  "data": [
    {
      "id": "usr_123",
      "email": "user@example.com",
      "name": "John Doe",
      "created_at": "2026-01-15T10:30:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 150
  }
}
```

**Response 401:**
```json
{
  "error": "unauthorized",
  "message": "Invalid or missing authentication token"
}
```

## Error Codes

| Code | Description |
|------|-------------|
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Invalid token |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource doesn't exist |
| 429 | Too Many Requests - Rate limit exceeded |
| 500 | Internal Server Error |
```
