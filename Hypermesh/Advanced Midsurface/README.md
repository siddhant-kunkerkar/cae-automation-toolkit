# Auto Midsurface

Automatically generates midsurface components, shell properties, and thickness assignments directly from component metadata.

---

## Why I Built This

One feature I consistently missed when working in HyperMesh was automatic midsurface generation based on thickness metadata.

Having previously used ANSA, I became accustomed to workflows where midsurface creation and thickness assignment required significantly less manual effort.

Every time I started a new model in HyperMesh, I found myself repeating the same sequence of operations:

1. Extract midsurface
2. Create component
3. Create property
4. Assign shell thickness
5. Organize entities

After doing this repeatedly across multiple projects, I decided to automate the workflow.

This tool was created to eliminate those repetitive steps and allow more time to be spent on actual engineering work rather than model preparation.

---

## Overview

The Auto Midsurface Tool reads component thickness metadata, generates midsurfaces, creates corresponding shell properties, and automatically assigns thickness values.

The objective is to standardize midsurface creation while reducing preprocessing effort.

---

## Supported Environment

| Item | Version |
|--------|--------|
| HyperMesh | 2022.3 |
| Solver | LS-DYNA |
| Language | Tcl/Tk |

---

## Features

- Reads component thickness metadata
- Automatic midsurface extraction
- Automatic component generation
- SECTION_SHELL property creation
- Automatic thickness assignment
- Standardized naming convention
- Batch processing of multiple components

---

## Metadata Requirements

The tool reads thickness values from:

```text
P_GAUGE
```

component metadata.

Example:

```text
P_GAUGE = 1.2
```

Generated property thickness:

```text
1.2 mm
```

---

## Workflow

### Input

Selected components containing:

- Surface geometry
- Valid P_GAUGE metadata

### Processing

1. Read component metadata
2. Extract thickness value
3. Generate midsurface
4. Create new midsurface collector
5. Create SECTION_SHELL property
6. Assign thickness
7. Assign property to component

### Output

Generated:

- Midsurface component
- Shell property
- Thickness assignment

---

## Naming Convention

Example:

```text
ABC_PANEL_000.002
```

Thickness:

```text
1.2 mm
```

Generated component:

```text
ABC_PANEL_1x2mm
```

---

## Benefits

- Eliminates repetitive preprocessing steps
- Improves workflow consistency
- Reduces manual property creation
- Reduces human error
- Accelerates model preparation

---

## Typical Use Cases

- BIW development
- Crash CAE preprocessing
- Sheet metal models
- Large assembly preparation
- LS-DYNA shell model creation

---

## Future Improvements

- Batch report generation
- Thickness validation
- Material assignment support
- Multi-property templates
- User-configurable naming standards

---

## Author

**Siddhant Hant**

---

## Philosophy

> Automate repetitive engineering work so engineers can focus on analysis, decision-making, and product development rather than manual model setup.
