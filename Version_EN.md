# Complete Guide to Version Numbering Rules

## Table of Contents
1. [Basic Structure](#1-basic-structure)  
2. [Pre-release Tags](#2-pre-release-tags)  
3. [Build Metadata](#3-build-metadata)  
4. [Date-based Versioning](#4-date-based-versioning)  
5. [Special Letters and Scenarios](#5-special-letters-and-scenarios)  
6. [Industry Standards and Tools](#6-industry-standards-and-tools)  
7. [Letter Usage Summary Table](#7-letter-usage-summary-table)  
8. [Best Practices](#8-best-practices)  
9. [Appendix](#9-appendix)  

---

## 1. Basic Structure
The core version number consists of three parts in the **`Major.Minor.Patch`** format:

| Field      | Description                                                                 | Update Rules                           |
|------------|-----------------------------------------------------------------------------|----------------------------------------|
| **Major**  | Indicates major changes or backward-incompatible updates.                  | Incremented for breaking changes; resets Minor and Patch to `0`. |
| **Minor**  | Indicates backward-compatible feature additions.                           | Incremented for new features; resets Patch to `0`.              |
| **Patch**  | Indicates bug fixes or optimizations without functional changes.           | Incremented only for fixes or optimizations.                    |

**Examples**:  
- `1.0.0`: Initial stable release.  
- `2.3.1`: Major version 2, third feature iteration, first bug fix.  

---

## 2. Pre-release Tags
Pre-release versions use a hyphen `-` followed by identifiers, ordered by development stage:

### 2.1 Alpha (Internal Testing)
- **Identifier**: `alpha` or `a`  
- **Scenario**: Early internal testing; unstable features.  
- **Examples**:  
  - `1.0.0-alpha`  
  - `2.3a` (shortened)  
  - `3.0.0-alpha.2` (with iteration number)  

### 2.2 Beta (Public Testing)
- **Identifier**: `beta` or `b`  
- **Scenario**: Feature-complete but requiring user testing.  
- **Examples**:  
  - `1.0.0-beta`  
  - `2.4.0b3` (third Beta version)  

### 2.3 RC (Release Candidate)
- **Identifier**: `rc`  
- **Scenario**: Final testing phase before stable release.  
- **Examples**:  
  - `1.0.0-rc.1`  
  - `2.5rc2` (shortened)  

### 2.4 Other Pre-release Identifiers
| Identifier    | Description                   | Example               |
|---------------|-------------------------------|-----------------------|
| `dev`         | Development version           | `1.0.0-dev`           |
| `snapshot`    | Temporary build (Maven)       | `1.0-SNAPSHOT`        |
| `nightly`     | Daily automated build         | `2023.07-nightly`     |

---

## 3. Build Metadata
Append build information with `+`; does not affect version precedence:

**Examples**:  
- `1.0.0-alpha+20230715` (build date)  
- `2.3.1+build.89a4f2d` (Git commit hash)  

---

## 4. Date-based Versioning
Common in rapidly iterating projects (e.g., firmware):

### 4.1 Pure Date Formats
- **Year-Month-Day**: `YYYYMMDD`  
  - Example: `20230715`  
- **Year.Week**: `YYYY.WW`  
  - Example: `2023.28` (Week 28 of 2023)  

### 4.2 Combined Formats
- Semantic version + date: `1.2.3-20230715`  
- Date + build number: `20230715.1`  

---

## 5. Special Letters and Scenarios
### 5.1 Platform/Environment Identifiers
| Letter  | Platform          | Example           |
|---------|-------------------|-------------------|
| `w`     | Web               | `2.0w`            |
| `m`     | Mobile            | `3.1m`            |
| `d`     | Desktop           | `4.2d`            |
| `s`     | Server            | `5.0s`            |

### 5.2 Customized Versions
| Identifier | Description                   | Example                   |
|------------|-------------------------------|---------------------------|
| `ga`       | General Availability          | `5.0-ga`                  |
| `sp`       | Service Pack (Microsoft)      | `Windows10-SP2`           |
| `LTS`      | Long-Term Support             | `Node.js 18.17.1 LTS`     |

### 5.3 Build Frequency Identifiers
| Identifier | Description           | Example           |
|------------|-----------------------|-------------------|
| `w`        | Weekly build          | `3.5.0w12`        |
| `d`        | Daily build           | `2023.07d15`      |

---

## 6. Industry Standards and Tools
### 6.1 Semantic Versioning (SemVer)
- **Standard**: `Major.Minor.Patch[-Pre-release][+Metadata]`  
- **Rules**:  
  - Reset Minor and Patch to `0` when Major increments.  
  - Public APIs must follow SemVer (e.g., npm, PyPI).  

### 6.2 Other Standards
| Standard    | Example             | Use Case                |
|-------------|---------------------|-------------------------|
| **CalVer**  | `2023.07.1`         | Ubuntu, firmware        |
| **ZeroVer** | `0.12.3`            | Unstable projects       |

### 6.3 Tool-specific Implementations
| Tool        | Example                      | Description              |
|-------------|------------------------------|--------------------------|
| **Python**  | `1.0a1`, `1.0.post1`         | PEP 440 compliant        |
| **Maven**   | `1.0-SNAPSHOT`, `2.3-rc1`    | Strict version matching  |
| **Docker**  | `nginx:1.23-alpine`          | Tagging with versions    |

---

## 7. Letter Usage Summary Table
| Letter/Identifier | Description              | Example               | Use Case                   |
|--------------------|--------------------------|-----------------------|----------------------------|
| `a`                | Alpha version            | `1.0.0a`              | Internal testing phase     |
| `b`                | Beta version             | `2.3.0b2`             | Public testing phase       |
| `rc`               | Release Candidate        | `3.0-rc.1`            | Final testing              |
| `w`                | Weekly build/Web version | `4.5.0w12`            | CI/CD or platform-specific |
| `m`                | Mobile version           | `2.0m`                | Cross-platform projects    |
| `LTS`              | Long-Term Support        | `Node.js 18.17.1 LTS` | Enterprise stable releases |
| `snapshot`         | Snapshot version         | `1.0-SNAPSHOT`        | Maven temporary builds     |

---

## 8. Best Practices
1. **Define Version Stages Clearly**:  
   - Follow the sequence: Alpha → Beta → RC → Stable.  
2. **Automate Versioning**:  
   - Use CI/CD tools (e.g., GitHub Actions) for build numbers or date versions.  
3. **Document Rules**:  
   - Record versioning policies in `CHANGELOG.md` or `VERSIONING.md`.  
4. **Manage Dependencies Strictly**:  
   - Lock versions (e.g., `package-lock.json`) to avoid compatibility issues.  

---

## 9. Appendix
### 9.1 Version Comparison Rules
- **Precedence Order**:  
  `1.0.0` < `1.0.0-alpha` < `1.0.0-beta` < `1.0.0-rc` < `1.0.0`  
- **Tool Support**:  
  - npm: `semver` library  
  - Python: `packaging.version.parse`  

### 9.2 Reference Links
- [Semantic Versioning 2.0.0](https://semver.org/)  
- [Python PEP 440](https://peps.python.org/pep-0440/)  
- [Maven Versioning](https://maven.apache.org/ref/3.9.5/maven-artifact/apidocs/org/apache/maven/artifact/versioning/VersionRange.html)  