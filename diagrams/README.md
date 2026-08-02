# Diagrams

## Overview

- This directory contains the architecture and workflow diagrams used throughout the MiniCorp repository.

- The diagrams provide a visual representation of the enterprise environment, Active Directory implementation, authentication workflow, Group Policy processing, and the security assessment methodology.

- Each diagram is maintained in two formats:

    - **`.drawio`** — Editable source file for future modification.
    - **`.svg`** — Rendered vector image used throughout the repository documentation.

- This approach allows diagrams to remain version-controlled while supporting future updates.

---

## Diagram List

| Diagram | Purpose |
|----------|---------|
| `01-enterprise-network.drawio` | Enterprise network topology |
| `02-active-directory.drawio` | Active Directory organizational structure |
| `03-authentication-flow.drawio` | Authentication and authorization workflow |
| `04-group-policy-flow.drawio` | Group Policy processing workflow |
| `05-security-assessment-workflow.drawio` | Security assessment methodology |

---

## Design Principles

- All diagrams within the MiniCorp repository follow the same design principles.

### Consistency

- Every diagram uses:

    - Consistent fonts
    - Consistent spacing
    - Consistent color palette
    - Consistent icon style
    - Consistent connector style

- This creates a uniform appearance throughout the repository.

---

### Simplicity

- Diagrams focus on communicating concepts clearly rather than including every implementation detail.

- Only information relevant to the topic of each diagram is included.

---

### Readability

- Diagrams are designed to remain readable when viewed:

    - On GitHub
    - In PDF exports
    - On desktop browsers
    - On mobile devices

- Layouts prioritize clarity over density.

---

### Accuracy

- Each diagram reflects the implemented MiniCorp environment.

- No systems, services, or workflows are included unless they are documented elsewhere in the repository.

---

## Visual Style Guide

- The following conventions are used throughout the diagrams.

| Element | Style |
|----------|-------|
| Virtual Machine | Rounded rectangle |
| Windows Server | Blue |
| Windows Client | Light blue |
| Ubuntu Server | Orange |
| Network | Gray connector |
| Enterprise Services | Green |
| Assessment Activities | Purple |
| Documentation Flow | Dark gray |

---

## File Naming Convention

- Diagram files follow a numbered naming convention to maintain logical ordering.

- Examples:

```text
01-enterprise-network.drawio
01-enterprise-network.svg

02-active-directory.drawio
02-active-directory.svg

03-authentication-flow.drawio
03-authentication-flow.svg
```

---

## Usage

- The diagrams are referenced throughout the repository, including:

    - `README.md`
    - `docs/02-lab-architecture.md`
    - `docs/03-active-directory.md`
    - `docs/06-group-policy.md`
    - `docs/07-security-assessment.md`
    - `reports/security-assessment-report.md`

- Maintaining consistent filenames ensures these references remain stable.

---

## Editing

- The editable `.drawio` files should always be updated first.

- After modifications:

    1. Save the updated `.drawio` file.
    2. Export the corresponding `.svg`.
    3. Replace the existing SVG within this directory.
    4. Verify that referenced documentation renders correctly.

---

## Summary

- The diagrams contained within this directory provide a visual representation of the MiniCorp enterprise environment and complement the written documentation.

- By maintaining editable source files alongside exported SVG images, the repository remains both maintainable and presentation-ready.
