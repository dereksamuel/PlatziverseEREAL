# Platziverse-Agent
## Usage

``` JS

const PlatziverseAgent = require('platziverse-agent');

const agent = new PlatziverseAgent({
  name: 'myhulkApp',
  username: 'pip',
  interval: 2000
});

agent.connect();

agent.addMetric('rss', function getRss () {
  return process.memoryUsage().rss;// tipo de 
});

agent.addMetric('promiseKetric', function getRandomPromise () {
  return Promise.resolve(Math.random());
});

agent.addMetric('callbackMetric', function getRandomCallback (callback) {
  setTimeout(() => {
    callback(null, Math.random());
  }, 1000);
});

//This agent only
agent.on('connected');
agent.on('disconnected');
agent.on('message');

//Other Agents
agent.on('agent/connected');
agent.on('agent/disconnected');
agent.on('agent/message', (payload) => {
  console.log(payload);
});

setTimeout(() => agent.disconnect(), 20000);

```