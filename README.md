# Contribution #1: Top-K Precision/Recall Multilabel Metrics for Ranking Task

**Contribution Number:** 1
**Student:** Abdelmageed Abdelmagid
**Issue:** https://github.com/pytorch/ignite/issues/467
**Status:** Phase I Complete

---

## Why I Chose This Issue

The issue focuses on implementing top-k precision and recall metrics for multilabel ranking tasks. I was interested in it because it is a useful metric, directly usable for real ML workflows, and still scoped enough to realistically complete.

This issue aligns well with my learning goals and my skills in AI infrastructure and ML systems. Through this contribution, I hope to learn more about the open source workflow, architecture decisions for large frameworks, and the deep internals of widely used projects.

---

## Understanding the Issue

### Problem Description

Currently there is no official implementation for top-k precision and recall metrics in multilabel ranking. There is only basic precision and recall. 

### Expected Behavior

Users should be able to compute multilabel precision and recall metrics using only the top-k for each sample.

### Current Behavior

No current implementation.

### Affected Components

New files / changes would be added to the metrics folder of the repo, then tests would be added.

---

## Reproduction Process

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

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

### Week 1 Progress

Claimed an issue, cloned the repo and became familiar with its structure.

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
