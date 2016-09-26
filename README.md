This is a plugin for [Logstash](https://github.com/elastic/logstash)

It will monitor a facebook feed at a regular interval and outut the posts as events

# Usage instructions

1. Clone the repository
   
   `git clone https://github.com/EikeDehling/logstash-input-facebook.git`

2. Install build dependencies (I used ruby 2.3.1)

3. Build the plugin

   `gem2.3 build logstash-input-facebook.gemfile`

4. Install the plugin in your logstash setup

   `bin/logstash-plugin install ../logstash-input-facebook/logstash-input-facebook-0.1.gem`

5. Configure the plugin


    ```
    input {
      facebook {
        oauth_token => "[OAuth token to monitor the page, can be copied from the facebook api explorer]"
        facebook_id => "[Id of the facebook page to monitor]"
      }
    }

    filter {
      fingerprint {
        source => ["id"]
        target => "[@metadata][_id]"
        key => "my-key"
      }
    }

    output {
      stdout { codec => dots }
      elasticsearch {
        hosts => [ "localhost:9200" ]
        index => "facebook"
        document_type => "posting"
        document_id => "%{[@metadata][_id]}"
      }
   }
   ```
