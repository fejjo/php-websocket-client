WebSocket client
================

[![Build Status](https://travis-ci.org/gavroche/php-websocket-client.png)](https://travis-ci.org/gavroche/php-websocket-client)

A simple WebSocket WAMP client implemented in php.

## Requirements

This library uses PHP 5.3+.

## Install

It is recommended that you install the WebSocket client library [through composer](http://getcomposer.org).

```JSON
{
    "require": {
        "gavroche/websocket-client": "dev-master"
    }
}
```

## Usage

Here is an example of a simple WebSocket client:

```PHP
class Client implements WebSocketClient\WebSocketClientInterface
{
    private $client;

    public function onReceive(array $data, array $header)
    {
        // Do something with the data
    }

    public function subscribe($topic)
    {
        $this->client->subscribe($topic);
    }

    public function unsubscribe($topic)
    {
        $this->client->unsubscribe($topic);
    }

    public function setClient(WebSocketClient $client)
    {
        $this->client = $client;
    }

    public function getClient()
    {
        return $this->client;
    }
}

$loop = React\EventLoop\Factory::create();

$client = new WebSocketClient(new Client, $loop);

$loop->run();
```
