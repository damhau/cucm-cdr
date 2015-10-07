# Logstash Config to import CUCM CDR/CMR
This is the config file I've used to import the Cisco Callmanager CDR and CMR in Elasticsearch with Logstash
## Installation
Copy the config file in /etc/logstash/conf.d/ and change the folder in cucm.conf
## Usage
TODO: Write usage instructions
## Contributing
1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D
## History
TODO: Write history
## Credits
TODO: Write credits
## License
TODO: Write license
]]></content>
  <tabTrigger>readme</tabTrigger>
</snippet>


Logstash config to import CUCM CDR/CMR

Replace the fiel path and add_field information with the name of your cucm cluster.

If you have only 1 CUCM cluster you can remove the additioanl file {} block you need only two file entry (one for CDR and one for CMR), eg:

input {
        file {
                path =>"/folder with CDR file/cdr*"
                type => "cucm-cdr"
                start_position => "beginning"
        }
        file {
                path =>"/folder with CMR file/cmr*"
                type => "cucm-cmr"
                start_position => "beginning"
        } 
}
