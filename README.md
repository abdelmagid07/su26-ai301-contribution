# Contribution #1: Top-K Precision/Recall Multilabel Metrics for Ranking Task

**Contribution Number:** 1
**Student:** Abdelmageed Abdelmagid
**Issue:** https://github.com/pytorch/ignite/issues/467
**Status:** PR open — waiting for review

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

Set up a local fork of PyTorch Ignite. 
Cloned fork and installed dependencies.
Ran existing metric tests to confirm setup was correct
Main challenge was understanding the metric structure and how outputs are accumulated across batches

### Steps to Reproduce

1. Create a synthetic multilabel dataset
2. Pass predictions through standard multilabel metrics 
3. Observe how current metrics do not evaluate ranked top-k outputs

### Reproduction Evidence

Branch: https://github.com/abdelmagid07/ignite/tree/feat/top-k-multilabel-precision-recall

---

## Solution Approach

### Analysis

The root issue is that it does not support ranking-based conversion (top-k selection) before accumulation.
The missing piece is a preprocessing step that converts logits to top-k binary mask per sample before passing to existing metrics logic.

### Proposed Solution

Implement:

- TopKMultilabelPrecision
- TopKMultilabelRecall

They will take raw prediction scores, select top-k indices per sample, convert to binary prediction tensor, reuse current metric logic.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** We have to add support for top-k selection in precision and recall metrics.

**Match:** We can reuse _BasePrecisionRecall's logic and mirror existing implementations, this is an extra feature on top of pre existing metrics, not a from scratch implementation.

**Plan:** 
1. Make new _BaseTopKMultilabelPrecisionRecall
2. Implement _prepare_output() to flatten batch, apply torch.topk, and build binary mask.
3. Create TopKMultilabelPrecision and TopKMultilabelRecall
4. Add tests.

**Implement:** https://github.com/abdelmagid07/ignite/tree/feat/top-k-multilabel-precision-recall

**Review:** Ensure consistency with rest of API, try to match existing metric styles as much as possible.

**Evaluate:** Run unit tests and regression tests.

---

## Testing Strategy

### Unit Tests

- [x] Test invalid inputs (bad shapes, non-binary y, integer y_pred)
- [x] Test all average modes against sklearn reference
- [x] Hand-computed example to confirm top-k per sample semantics

### Integration Tests

- [x] Distributed / Engine integration tests

### Manual Testing

Built docs locally and checked metric pages in browser. Ran pre-commit hooks.

---

## Implementation Notes

### Week 1 Progress

Claimed an issue, cloned the repo and became familiar with its structure.

### Week 2 Progress

Implemented metrics, added tests and docs, ran pre-commit, opened PR to upstream.

### Code Changes

- **Files modified:** `ignite/metrics/top_k_multilabel_precision_recall.py`, `ignite/metrics/__init__.py`, `tests/ignite/metrics/test_top_k_multilabel_precision_recall.py`, `docs/source/metrics.rst`
- **Key commits:** draft implementation, tests/docs, pre-commit formatting fix
- **Approach decisions:** Extended _BasePrecisionRecall instead of building from scratch. Clamped k to num_labels when k is too large.

---

## Pull Request

**PR Link:** https://github.com/pytorch/ignite/pull/3792

**PR Description:** Adds TopKMultilabelPrecision and TopKMultilabelRecall for issue #467. Includes tests, RST docstrings, and metrics.rst updates.

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** Open — awaiting review (CI waiting for maintainer approval)

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
