Lucene Query Syntax
Kibana’s query language has historically been based on the Lucene query syntax.
The following are some tips that can help get you started.
https://www.elastic.co/guide/en/kibana/6.3/lucene-query.html

- To perform a free text search, simply enter a text string.
  For example, if you’re searching web server logs, you could enter safari to search all
  fields for the term safari. henry

- To search for a value in a specific field, prefix the value with the name of the field.
  For example, you could enter status:200 to find all of the entries that contain the value
  200 in the status field. speech_number:13

- To search for a range of values, you can use the bracketed range syntax,
  [START_VALUE TO END_VALUE]. For example, to find entries that have 4xx status codes,
  you could enter status:[400 TO 499]. speech_number:[13 TO 15]

- To specify more complex search criteria, you can use the Boolean operators AND, OR, and NOT.
  For example, to find entries that have 4xx status codes and have an extension of php or html,
  you could enter status:[400 TO 499] AND (extension:php OR extension:html).

- response:200 will match documents where the response field matches the value 200.

- Quotes around a search term will initiate a phrase search.
  For example, message:"Quick brown fox" will search for the phrase "quick brown fox" in the message field.
  Without the quotes, your query will get broken down into tokens via the message field’s configured analyzer
  and will match documents that contain those tokens, regardless of the order in which they appear.
  This means documents with "quick brown fox" will match, but so will "quick fox brown".
  Remember to use quotes if you want to search for a phrase.

- response:200 and (extension:php or extension:css) will match documents where
  response is 200 and extension is either php or css.

- response:(200 or 404) searches for docs where the response field matches 200 or 404.
  We can also search for docs with multi-value fields that contain a list of terms, for example:
  tags:(success and info and security)

- NOT response:200 will match all documents where response is not 200.

- Entire groups can also be inverted. response:200 and NOT (extension:php or extension:css)

- Ranges are similar to lucene with a small syntactical difference.
  Instead of bytes:>1000, we omit the colon: bytes > 1000.
  "> , >=, <, <=" are all valid range operators.

- Exist queries are simple and do not require a special operator. response:\* will
  find all docs where the response field exists.

- Wildcard queries are available. machine.os:win\* would match docs where the machine.os
  field starts with "win", which would match values like "windows 7" and "windows 10".
