# Logstash Config to import CUCM CDR/CMR
This is the config file I've used to import the Cisco Callmanager CDR and CMR in Elasticsearch with Logstash
## Installation
1. Copy the config file in /etc/logstash/conf.d/ and change the folder in cucm.conf
2. Add the Elasticsearch template from the json file in the folder elasticsearch
3. Import the kibana file from the folder kibana (work only with Kibana 4.1)
## Usage
You need to configure the export of CDR/CMR on your Callmanager to the server where logstash is running.
If you have multiple CUCM cluster you can configure logstash to add a tag, just create a folder for each cluster and add new file{} input like this:
```
file {
    path => "/folder with CMR files Cluster 1/cdr*"
    type => "cucm-cdr"
    start_position => "beginning"
	add_field => { "cucm_clustername" => "CUCM_Cluster_1" }
}
file {
	path => "/folder with CMR files Cluster 1/cmr*"
	type => "cucm-cmr"
	start_position => "beginning"
	add_field => { "cucm_clustername" => "CUCM_Cluster_1" }
}
file {
    path => "/folder with CMR files Cluster 2/cdr*"
    type => "cucm-cdr"
    start_position => "beginning"
	add_field => { "cucm_clustername" => "CUCM_Cluster_2" }
}
file {
	path => "/folder with CMR files Cluster 2/cmr*"
	type => "cucm-cmr"
	start_position => "beginning"
	add_field => { "cucm_clustername" => "CUCM_Cluster_2" }
}
```		
## License
Copyright (c) 2015 Damien Hauser

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.