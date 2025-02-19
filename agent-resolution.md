#Debug And Error Correcting Process

## Overview
This document outlines our systematic approach to debugging and error resolution. The process is designed to be followed consistently by both human developers and LLM agents.

## Debug Process Flow

```
[Error Occurrence] → [Context Gathering] → [Root Cause Analysis] → [Hypothesis Generation] → 
[Solution Implementation] → [Verification] → [Documentation]
```

## Step 1: Context Gathering

First, if there was a previous error, tell the user whether you are making progress fixing the error, or if we are going in circles, dealing with the same error, or creating more compounding errors. You must advise the user if they should perform a reset or other actions to revert to a previous state.

Also, you must tell the user if these are natural errors that we would expect to see as we progress, or if these are new errors introduced by the previous error fix.

Ask your user for the following information if not already supplied, and if you deem it necessary (sometimes we only need a few of these):

### Required Information
1. **Error Details**
   - Exact error message
   - Stack trace (if available)
   - Error code (if applicable)

2. **Environment Context**
   - Operating system
   - Compiler version
   - Build configuration (Debug/Release)
   - Relevant hardware details

3. **Code Context**
   - File and line number where error occurred
   - Function/method involved
   - Relevant class hierarchy
   - Recent code changes

4. **Execution Context**
   - Steps to reproduce
   - Input data/parameters
   - System state at time of error

## Step 2: Root Cause Analysis

### Analysis Process
1. **Error Classification**
   - Compilation error
   - Runtime error
   - Logical error
   - Resource error

2. **Impact Assessment**
   - Severity (Critical/Major/Minor)
   - Scope (Local/System-wide)
   - Frequency (Consistent/Intermittent)

3. **Code Review**
   - Control flow analysis
   - Data flow analysis
   - Memory management review
   - Thread safety assessment

4. **Dependency Check**
   - Library versions
   - External dependencies
   - System requirements

## Step 3: Hypothesis Generation

You will generate two competing hypotheses and then select the one you believe best fully resolves the error.

### Hypothesis Criteria
1. **Plausibility**
   - Consistent with error symptoms
   - Supported by code analysis

2. **Testability**
   - Can be verified through specific tests
   - Has clear success/failure criteria

3. **Impact**
   - Addresses root cause
   - Minimizes side effects

4. **Complexity**
   - Implementation effort
   - Risk of introducing new issues

### Hypothesis Template
```markdown
**Hypothesis #X**
- **Description**: [Brief explanation]
- **Expected Outcome**: [What should happen if correct]
- **Verification Method**: [How to test]
- **Implementation Complexity**: [Low/Medium/High]
- **Risk Assessment**: [Potential downsides and likelihood of new errors]
```

## Step 4: Solution Implementation

### Solution Selection Criteria
1. **Solution 1**
   - Most likely to resolve the issue
   - Minimal impact on existing code
   - Easiest to implement and test

2. **Solution 2**
   - Alternative approach
   - May require more changes
   - Used if Solution 1 fails

### Implementation Process
1. **Code Changes**
   - Implement Solution 1
   - Tellt hs user how to test (but do not write tests)

3. **Verification**
   - Confirm with user that error is resolved
   - Check for regression
   - Validate performance with user

## Step 5: Documentation

### Documentation Requirements - put it all in debug-log.md
1. **Error Report**
   - Error details
   - Root cause
   - Solution implemented

2. **Code Changes**
   - Files modified
   - Functions changed
   - Tests added

3. **Lessons Learned**
   - Prevention strategies
   - Best practices
   - Future considerations


## Debug Process Checklist
- [ ] Gather complete context
- [ ] Analyze root cause
- [ ] Generate hypotheses
- [ ] Select and implement Solution 1
- [ ] Verify solution
- [ ] If Solution 1 fails, implement Solution 2
- [ ] Document the fix
- [ ] Update relevant documentation
