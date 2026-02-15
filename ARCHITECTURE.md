# pkg-core — Architecture

## Objective

Shared Laravel package that provides the foundational structure and architectural standards used across all platform APIs.

This package must remain **generic, lightweight, and business-agnostic**.

It is not an API service.
It is a reusable internal package.

---

## Responsibilities

### 1. Base Structure

Provide standardized base classes:

- BaseModel
- BaseService
- BaseRepository
- BaseController (if necessary)
- Common reusable Traits

Purpose:
Ensure architectural consistency across all projects.

---

### 2. Contracts & Abstractions

Define interfaces and contracts for:

- Services
- Repositories
- External integrations (contracts only)
- Event dispatching

All consuming APIs must depend on abstractions, not implementations.

---

### 3. Cross-Cutting Concerns

Provide shared technical utilities:

- Base exception classes
- Standard API response structure
- Logging helpers
- Validation base classes
- DTO base structures
- Pagination helpers

No business rules allowed.

---

### 4. Event & History Foundation

Provide structural support for:

- Base Event classes
- Event dispatcher abstraction
- Standardized event payload structure

This supports future AI-ready historical modeling.

Only structure — no domain-specific events.

---

## Architectural Rules

- Strict layer separation:
    - Controller → Service → Repository
- No direct database access outside repositories
- No domain logic inside pkg-core
- No heavy external service integrations
- Keep dependencies minimal

---

## What Must NOT Be Included

The following must NOT exist inside pkg-core:

- Restaurant business rules
- Market business rules
- Payment gateway implementations
- Invoice emission logic
- Email sending implementation
- Tenant management logic

These belong to:

- api-controller
- api-service
- api-food
- api-market

---

## Design Principles

- Minimal
- Stable
- Reusable
- Framework-aligned
- Long-term maintainable
- Independent of any specific business domain

---

## Long-Term Goal

Provide a clean, consistent foundation so every API project starts structured, scalable, and aligned with platform standards without duplicating core architectural logic.
