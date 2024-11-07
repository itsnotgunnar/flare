# Flare 🔥

A comprehensive filesystem analysis tool designed to help you identify potential security vulnerabilities on Linux systems.

## Overview

**Flare** is a bash script that performs a deep dive into your filesystem, uncovering misconfigurations and anomalies that could be exploited by attackers.

## Features

- **Files in Foreign Directories**: Identifies files owned by users located in directories owned by others.
- **Permission Anomalies**: Finds files with permissions differing from their owning directories.
- **Writable Files**: Detects files writable by non-root users.
- **Root Files Accessible by Users**: Lists root-owned files that are readable, writable, or executable by non-root users through group permissions.
- **Non-Root Owned Directories**: Finds directories owned by non-root users.
- **Recently Modified Files**: Lists the most recently modified files.
- **Interesting Files Analysis**: Searches for files likely to contain sensitive information and scans them for potential credentials.

## Getting Started

### Prerequisites

- **Operating System**: Linux
- **Permissions**: Root or sudo privileges to access all files and directories.

### Installation

Clone the repository or copy-paste into a file, then run.

```bash
git clone https://github.com/itsnotgunnar/flare
```

## Output

All results are saved in the `/dev/shm/filesystem_analysis` directory for easy access and quick cleanup upon reboot (since `/dev/shm` is a temporary).

## Understanding the Output

### 1. Files in Foreign Directories

- **What it is**: Files owned by a user but located in directories owned by others.
- **Why it matters**: Could indicate improper file placement or potential security risks.

### 2. Permission Anomalies

- **What it is**: Files with permissions that differ from their owning directories.
- **Why it matters**: If these files aren't located in their typical directories, maybe they aren't typical files with typical configurations and information.

### 3. Writable Files by User

- **What it is**: Files writable by non-root users.
- **Why it matters**: Bad news if any of these files interacts with any code.

### 4. Root Files Accessible by Users

- **What it is**: Root-owned files accessible to users via group permissions.
- **Why it matters**: Surprisingly consistent hail mary for direct privilege escalation.

### 5. Non-Root Owned Directories

- **What it is**: Directories not owned by root.
- **Why it matters**: While it's normal for users to own their home directories, other directories owned by non-root users is an indication that this is unique to the machine, and may contain sensitive information or other vectors worth investigation.

### 6. Recently Modified Files

- **What it is**: The most recently modified files on the system. Filters out a lot of noise, though needs more work in this field.
- **Why it matters**: Any unpredictable files being modified on the system is worth looking into.

### 7. Interesting Files Analysis

- **What it is**: Files likely to contain sensitive information, such as configs or databases.
- **Why it matters**: OG function. Extremely effective.

