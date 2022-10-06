# Logstash input JDBC plugin with one connection. Connection remains open between executions.

Reverting https://github.com/logstash-plugins/logstash-input-jdbc/pull/237

## Developing

### 1. Plugin Development and Testing

#### Code
- To get started, you'll need JRuby.

```sh
export PATH=/jruby/bin:$PATH
```

- Install bundler gem
```sh
gem install bundler
```

- To develop a plugin you need a local clone of Logstash repository.
```sh
git clone --branch 8.1 --single-branch https://github.com/elastic/logstash.git
cd logstash
./gradlew assemble
```

- Point the plugin's environment to it
```sh
export LOGSTASH_PATH=/path/to/logstash/
export LOGSTASH_SOURCE=1
```
- Install vendor JDBC jars
```sh
./gradlew vendor
```

- Install dependencies
```sh
bundle install
```

- Run tests
```sh
bundle exec rspec
```

### 2. Running your unpublished Plugin in Logstash

- Build your plugin gem
```sh
gem build logstash-integration-jdbc.gemspec
```
- Install the plugin from the Logstash home
```sh
bin/logstash-plugin install /my/logstash/plugins/logstash-integration-jdbc/logstash-integration-jdbc-0.1.0.gem
```
- Start Logstash and proceed to test the plugin
