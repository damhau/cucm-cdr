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
