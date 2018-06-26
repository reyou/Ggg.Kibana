https://www.elastic.co/guide/en/kibana/6.3/profiler-complicated.html

### Profiling a more complicated query

To understand how the query trees are displayed inside the Search Profiler,
let’s look at a more complicated query.

Index the following data
//=============================================================================
POST test/test/\_bulk
{"index":{}}
{"name":"aaron","age":23,"hair":"brown"}
{"index":{}}
{"name":"sue","age":19,"hair":"red"}
{"index":{}}
{"name":"sally","age":19,"hair":"blonde"}
{"index":{}}
{"name":"george","age":19,"hair":"blonde"}
{"index":{}}
{"name":"fred","age":69,"hair":"blonde"}
//=============================================================================
GET test/test/\_search
{
"query":{
"match_all" : {}
}
}
//=============================================================================
Replace the default match_all query with a query that has two sub-query components and includes a simple aggregation. For example, copy and paste the following query into the query editor.

{
"query": {
"bool": {
"should": [
{
"match": {
"name": "fred"
}
},
{
"terms": {
"name": [
"sue",
"sally"
]
}
}
]
}
},
"aggs": {
"stats": {
"stats": {
"field": "price"
}
}
}
}

//=============================================================================
