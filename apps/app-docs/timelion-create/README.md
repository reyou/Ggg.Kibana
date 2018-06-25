https://www.elastic.co/guide/en/kibana/6.3/timelion-create.html

### Creating time series visualizations

This tutorial will be using the time series data from Metricbeat to walk you through a number of
functions that Timelion offers. To get started, download Metricbeat and follow the instructions
here to start ingesting the data locally.

//=============================================================================
http://localhost:5601/app/timelion#?_g=(refreshInterval:(display:Off,pause:!f,value:0),time:(from:now-1h,interval:auto,mode:quick,timezone:America%2FNew_York,to:now))&_a=(columns:2,interval:auto,rows:2,selected:0,sheet:!('.es(index%3Dmetricbeat-*,%20timefield%3D!'@timestamp!',%20metric%3D!'avg:system.cpu.user.pct!')'))
//=============================================================================
