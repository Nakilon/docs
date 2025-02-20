---
sourcePath: en/ydb/ydb-docs-core/en/core/yql/reference/yql-docs-core-2/builtins/_includes/basic/length.md
sourcePath: en/ydb/yql/reference/yql-docs-core-2/builtins/_includes/basic/length.md
---

## LENGTH {#length}

Returns the length of the string in bytes. This function is also available under the `LEN` name .

**Examples**
``` yql
SELECT LENGTH("foo");
```
``` yql
SELECT LEN("bar");
```

{% note info %}

To calculate the length of a string in Unicode characters, you can use the function [Unicode::GetLength](../../../udf/list/unicode.md).<br><br>To get the number of elements in the list, use the function [ListLength](../../list.md#listlength).

{% endnote %}
