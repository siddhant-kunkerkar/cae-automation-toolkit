# Component Renumber Tool

Automatically renumbers displayed HyperMesh components based on CAE naming conventions while preventing duplicate component IDs.

---

## Overview

The Component Renumber Tool standardizes component numbering by extracting the CAE part number from component names and generating consistent component IDs.

The tool is intended to reduce manual renumbering effort, improve model consistency, and support standardized CAE preprocessing workflows.

---

## Features

- Automatic component ID generation
- Duplicate ID detection and resolution
- Optional skip of already-renumbered components
- Processes displayed components only
- CAE naming convention validation
- Automatic skipping of empty component collectors
- Simple HyperMesh GUI interface

---

## Supported Environment

| Item | Version |
|--------|--------|
| HyperMesh | 2022.3 |
| Language | Tcl/Tk |
| Solver Compatibility | LS-DYNA |

---

## Naming Convention

The tool expects component names to contain a CAE part number in the following format:

```text
CAE-58711-xxxx
```

### Standard Component

```text
CAE-58711-xxxx
```

Generated ID:

```text
58701010
```

### Spot Weld Component 1

```text
spot1_CAE-58711-xxxx
```

Generated ID:

```text
58701011
```

### Spot Weld Component 2

```text
spot2_CAE-58711-xxxx
```

Generated ID:

```text
58701012
```

---

## Workflow

### 1. Display Target Components

Display all components that should be processed.

Only displayed components are considered by the tool.

### 2. Configure Options

#### Skip Already Renumbered Components

When enabled:

- Components already using the correct ID will be skipped.
- Re-running the tool is safe.

When disabled:

- All displayed components will be processed regardless of current ID.

### 3. Run Renumbering

The tool performs the following steps:

1. Read displayed components
2. Validate CAE naming format
3. Check for existing elements
4. Generate target ID
5. Resolve duplicate IDs
6. Apply component renumbering

### 4. Review Results

At completion, a summary report is displayed:

```text
Displayed  : 250
Renumbered : 215
Skipped    : 35
```

---

## Duplicate ID Protection

Before assigning a new component ID, the tool checks all existing component IDs in the model.

If the generated target ID already exists:

```text
58701010
```

the tool automatically searches for the next available ID:

```text
58701011
58701012
58701013
...
```

This ensures unique component identifiers throughout the model.

---

## Validation Rules

A component will only be processed if:

### Valid CAE Part Number Exists

Component name contains:

```text
CAE-xxxxx
```

### Component Contains Elements

Empty collectors are skipped automatically.

### Renumbering Is Required

When "Skip Already Renumbered Components" is enabled, components already using the correct target ID are skipped.

---

## Typical Use Cases

### Spot Weld Model Preparation

Renumber spot weld collectors generated during preprocessing.

### Supplier Model Standardization

Apply project numbering rules to imported models.

### Model Quality Checks

Verify that components follow company naming and numbering standards.

### Pre-Release Cleanup

Standardize IDs before model release or handover.

---

## Known Limitations

- Requires component names to contain a CAE part number.
- Processes displayed components only.
- Supports:
  - `spot1_`
  - `spot2_`
- Assumes a five-digit CAE part number format.
- Numbering logic is based on project-specific naming conventions.

---

## Benefits

- Eliminates manual renumbering work
- Enforces numbering consistency
- Reduces human error
- Supports repeatable workflows
- Improves model maintainability

---

## Version History

### v1.1.0

- Refactored code structure
- Added duplicate ID protection
- Added skip option for already-renumbered components
- Improved logging and reporting

### v1.0.0

- Initial release

---

## Future Enhancements

- Additional spot collector patterns
- User-configurable numbering templates
- CSV renumbering report export
- Batch processing across includes
- Rule-based naming validation

---

## Author

**Siddhant Hant**

---

## Philosophy

> Automate repetitive engineering work so engineers can focus on analysis, decision-making, and product development instead of manual data management.
