When a measure references one or more measures, it's known as a *compound measure*.

For this example, you will modify the **Profit** measure by using the following measure definition. Format the measure with two decimal places.

```dax
Profit =
[Revenue] - [Cost]
```

Next, add the **Profit** measure to the matrix visual.

Now that your model provides a way to summarize profit, you can delete the **Profit Amount** calculated column.

By removing this calculated column, you've optimized the data model. It results in a decreased data model size and shorter data refreshes. The **Profit Amount** calculated column wasn't required because the **Profit** measure can directly produce the required result.
