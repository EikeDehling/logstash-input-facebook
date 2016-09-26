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
