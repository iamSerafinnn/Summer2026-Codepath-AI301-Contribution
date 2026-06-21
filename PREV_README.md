# Contribution [#]: Add documentation on how to run the Burr UI server

**Contribution Number:** [1 / 2 / 3]  
**Student:** Serafin O. Gargantiel III.
**Issue:** https://github.com/apache/burr/issues/272 
**Status:** Phase 2

---

## Why I Chose This Issue

Simply because it doesn't sound too complicated. According to the github description, there is no documentation of how the Burr UI Server works and thus needs documentation for new users coming in and learn how to run the server. This takes time learning the program of the UI Server hoping to learn some web development skills and we just have to document its functionality and purpose. I have done some web development before so its nice to continue that!

---

## Understanding the Issue

### Problem Description

The Burr library includes a UI server for visualizing and monitoring application state, but there is no documentation covering how to install it, run it, or use its features. New users have no reference point for getting the UI up and running.

### Expected Behavior

There should be some sort of documentation that includes:
- How to install the UI server?
- How to launch the UI server?
- What port it runs on and how to access it in the browser?
- Optional command documentatations like like demo data?
- What features are available in the UI?

### Current Behavior

There are no instructions and documentations of how to install, what to install, what the burr UI do, and how to use it.
Only mention of the UI server in the docs is a single line in install.rst saying running 'burr' will "open up Burr's telemetry UI."

### Affected Components

- `docs/getting_started/` — new file `ui.rst` needs to be created
- `docs/getting_started/index.rst` — needs `ui` added to its toctree

---

## Reproduction Process

### Environment Setup

1. Forked "apache/burr" and cloned locally in terminal
2. Created a virtual environment with "python3 -m venv venv && source venv/bin/activate" to help access burr UI server
3. Attempted to install with "pip install "burr[tracking]". The server launched but crashed due to missing frontend build directory ("build/static" does not exist when running from source)
4. Installed "pip install "burr[start]"" to get the correct dependencies including "loguru"
5. Note that the correct package name is now "apache-burr", not "burr". This is itself undocumented for new users

### Steps to Reproduce

1. Install Burr and attempt to find documentation on running the UI server
2. Check "docs/getting_started/" and there is no UI specific documentation exists
3. The only reference is one line in "install.rst" with no further explanation of what to do after running "burr"
4. Run "burr" from a cloned repo and it crashes with "RuntimeError: Directory 'build/static' does not exist"
5. Run "burr" from the installed package and the server starts on port 7241 but new users have no documentation telling them this

### Reproduction Evidence

- **Commit showing reproduction:** https://github.com/iamSerafinnn/burr/tree/fix-issue-272
- **Screenshots/logs:** [If applicable]
- **My findings:** The documentation gap is confirmed. "docs/getting_started/index.rst" has no entry for the UI server. The setup process itself involves multiple undocumented steps such as correct install target, package name change from "burr" to "apache-burr", running from installed package vs. source clone.

---

## Solution Approach

### Analysis

The root cause of the issue is that no one has yet written a documentation of the Burr UI server. Though the "docs/getting_started/" does walk users through on installation with a simple example, it does not explain the UI server. The "index.rst" toctree has no entry for the docs, meaning even if a page existed, it wouldn't appear in the navigation.

### Proposed Solution

My proposed approach for the solution is to first create a new file on "docs/getting_started/ui.rst", serving as a reference to the documentaion of the Burr UI server. I will then add it to the "docs/getting_started/index.rst" toctree so it appears in the navigation.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** The Burr UI server does not have any documentation page. New users will find it confusing on how to install, launch, and use the Burr UI server. The only mention of the server is on a single line in "install.rst".

**Match:** The existing "docs/getting_started/install.rst" servers as a format reference of RST syntac, Apache license header , and ".. code-block:: bash" for commands. I plan for the new page to follow the same structure and style as well.

**Plan:**
1. Create the "docs/getting_started/ui.rst" documentation highlight the following sections:
    - Overview of what the Burr UI server is.
    - How to install the server using (pip install "apache-burr[start]").
    - How to launch the server using the "burr" command that runs on port 7241.
    - How to access the server in the browser using the url "http://localhost:7241".
    - Overview of some optional command like demo data and custom port.
    - Overview of the features of the Burr UI server like projects, demos, and telemtry.
2. Add ui to the toctree in docs/getting_started/index.rst

**Implement:** https://github.com/iamSerafinnn/burr/tree/fix-issue-272

**Review:**
This contribution must:
1. Follow RST formatting conventions that are referenced in the existing docs.
2. Include an Apache license header that are required for all files in the project.
3. Match the tone and structure of "install.rst" and "simple-example.rst".
4. Checked "CONTRIBUTING.rst" for any doc-specific contribution guidelines.

**Evaluate:**
To verify if my contribution worked, I will:
- Build the documents locally using Sphinx and confirm the new page renders correctly
- Verify that the Burr UI appears in the Getting Started navigation.
- Confirm that all code blocks and commands are accurate by testing them manually.

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
