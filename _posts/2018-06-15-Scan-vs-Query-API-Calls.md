---
  layout: post
  title: Scan vs Query API Calls
  subtitle: 
  tags: [ scan, query, dynamodb, database ]
  categories: database
  author: Eshan Shafeeq
  header_img: 
---

### What is a query
* A Query operation finds items in a table using only primary key attributes values. You must provide a partition attribute name and a distinct value to search for.
* You can optionally provide a sort key attribute name and value, and use a comparison operator to refine the search results.
* By default, a query returns all of the data attributes for items with the specified primary key(s); however, you can use the **ProjectionExpression** parameter so that the Query only returns some of the attributes, rather than all of them.
* Query results are always sorted by the sort key. If the data type of the sort key is a number, the results are returned in numeric order; otherwise the results are returned in order of ASCII character code values. By default, the sort order is ascending. To reverse the order, set the **ScanIndexForward** parameter to false.
* By default all queries are eventually consistent but can be changed to be strongly consistent.

### What is a Scan ?
* A Scan operation examines every item in the table ( basically a table dump ). By default the scan returns all of the data attributes for every item; however, you can use the **ProjectionExpression** parameter so that the Scan returns only some of them.

### What Should I use, a query or a Scan?
Generally, a Query Operation is more efficient than a Scan operation.

A Scan operation always scans the entire table, then filters out values to provide the desired result, essentially adding the extra step of removing data from the result set. Avoid using a Scan operation on a large table with a filter that removes many results, if possible. Also, as a table grows, the Scan operation slows. The Scan operation examines every item for the requested values, and can use up the provisioned throughput for a large table in a single operation.

For quicker response times, design your tables in a way that can use the Query, *Get* or *BatchGetItem* APIs instead. Alternatively, design your application to use Scan operations in a way that minimizes the impact on your tables request rate.

### Exam Tips
* A Query operation finds the items in a table using only primary key attribute values. You must provide a partition key attribute name and a distinct value to search for.

* A Scan operation examines every item in the table. By default, a Scan returns all of the data attributes for every item; however, you can use the **ProjectionExpression** parameter so that the Scan only returns some of the attributes, rather than all of them.

* Query results are always sorted by the sort key in ascending order. Set **ScanIndexForward** parameter to false to reverse it.

* Try use a Query operation than a scan operation as it is more efficient.

