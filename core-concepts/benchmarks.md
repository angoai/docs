---
description: Using benchmark tasks in Ango Hub to measure labeler performance
---

# Benchmarks

Project owners and reviewers can set certain labeling tasks as benchmarks. Benchmarks allow reviewers and project owners to measure annotator performance in a non-obtrusive way.

Set as benchmark a labeling [task](tasks.md) you know has been completed correctly. When annotators complete the other labeling tasks associated with the asset, their performance will be measured according to how similar their annotations are to the benchmark.

{% hint style="warning" %}
Currently, performance against benchmarks can only be calculated for labeling tools for which consensus calculation is available. [You can check the list of supported tools here](consensus.md#labeling-tools-for-which-consensus-is-available).

Tools that are not supported will not be included in the benchmark performance calculation.

For example, if your task includes both classifications and drawing with the brush, only classification performance will be calculated.

For more on the limitations of benchmarks, see the warning box in [this section of the Consensus page](consensus.md#labeling-tools-for-which-consensus-is-available), which applies to benchmarking as well.
{% endhint %}

## Benchmarks in Ango Hub <a href="#how-to-set-a-benchmark" id="how-to-set-a-benchmark"></a>

### How to set a benchmark <a href="#how-to-set-a-benchmark" id="how-to-set-a-benchmark"></a>

From your project’s _Assets_ tab, right-click on a circle representing a completed labeling task and click on _Set as Benchmark_.

{% hint style="warning" %}
Ensure there is at least another labeling task (circle) associated with the asset. Otherwise the benchmark will serve no purpose as the asset will not be labeled further.

To add a new labeling task to an existing asset, from the asset's row, click on the three dots to the right and click on _Add Task_.
{% endhint %}

{% hint style="info" %}
It is highly recommended that you only set as benchmark tasks you have confirmed to have been labeled correctly. Failure to do so will result in annotator performance being measured incorrectly.
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2021-12-17 at 15.08.00.png>)

The task will be marked with a small yellow crown on top of the circle.

### How benchmarks work <a href="#how-benchmarks-work" id="how-benchmarks-work"></a>

For each asset, you may set one task as benchmark. Ideally, the task marked as benchmark is the right way to annotate the asset. When another annotator labels the asset, the annotator’s performance will be compared to the benchmark.

If, for example, the annotator’s label is exactly the same as the benchmark, their performance will be calculated as being 100%. If it is completely different, 0%.

Labelers do not know when they are completing a benchmark task. They also do not know whether their own task has been marked as benchmark.

### Measuring annotator performance with benchmarks <a href="#measuring-annotator-performance-with-benchmarks" id="measuring-annotator-performance-with-benchmarks"></a>

From the project’s _Performance_ tab, look at the _Benchmark_ column. You will be able to see how, on average, each annotator has performed in benchmark tasks.

![](<../.gitbook/assets/Screen Shot 2021-12-17 at 15.10.52.png>)

If an annotator does not have a benchmark score, it means that they did not label any assets with benchmarks.

Annotators are shown their own benchmark score in large lettering on their dashboard:

![](<../.gitbook/assets/Screen Shot 2021-12-17 at 15.17.10.png>)

[See this page for more on performance.](labeler-performance.md)
