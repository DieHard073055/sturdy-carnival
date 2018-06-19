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

