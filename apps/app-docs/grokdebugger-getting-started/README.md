https://www.elastic.co/guide/en/kibana/6.3/grokdebugger-getting-started.html

### Getting Started with the Grok Debugger

The Grok Debugger is automatically enabled in Kibana.
It is located under the DevTools tab in Kibana.

//=============================================================================
Under Sample Data, enter a sample message that is representative of the data
you want to parse. For example:

55.3.244.1 GET /index.html 15824 0.043
//=============================================================================
Under Grok Pattern, enter the grok pattern that you want to apply to the data.

For example, to parse the log line in the example, you use:

%{IP:client} %{WORD:method} %{URIPATHPARAM:request} %{NUMBER:bytes} %{NUMBER:duration}
//=============================================================================
