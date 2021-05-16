# Pubsubhubbub

## Subscribing to a hub.

To subscribe to a hub, one needs to send a subscription request to the hub of the feed and provide a callback url that the hub will send a post request to whenever new content is available with the new content.
<br/>
[Indieweb.org's article](https://indieweb.org/How_to_publish_and_consume_WebSub) on publishing and consuming Websub descibes the process of _discovery_ to be "finding out the hub the feed is using". We can then subscribe to the feed using the hub.
The article goes on to detail that the link for the hub can be found in a HTTP `link` header with `rel="hub"` or a `link` tag with `rel="self"`. If the latter case, then the hub is the `href` link attatched to either tag. For instance:

```html
<link
  rel="self"
  type="application/atom+xml"
  href="http://push-pub.appspot.com/feed"
/>

<link rel="hub" href="https://pubsubhubbub.superfeedr.com" />
```

## Receiving notifications

There are two kinds of notifications:

1. **Standard Notifications**:
   These notifications will not contain a `POST` body. The subscriber will receive an empty notification and is expected, if the subscriber wishes, to go fetch the content themselves and parse _only_ the content that they have not seen before, i.e. get the new content that they want.
2. **Fat Pings**
   > "A "Fat Ping" notification will contain a `POST` body with either the full HTML of the page, or just the HTML of the new entries that the publisher has added since the last notification."
   > However, in receiving the notification, there is no guarantee that the hub has not reformated the data even though the content is the same new content from the publisher.

## Useful links:

### Hubs:

- [Google's PubSub Hub](https://pubsubhubbub.appspot.com)
- [Superfeedr](https://blog.superfeedr.com/)
- [Switchboard](https://indieweb.org/Switchboard)
- [phubb](https://indieweb.org/phubb)

### Tools

- [A real time app](http://push-pub.appspot.com/) that you can subscribe to and push content for testing and [it's feed](https://push-pub.appspot.com/feed)

## Articles and userful Links

- [How to publish and consume WebSub](https://indieweb.org/How_to_publish_and_consume_WebSub) from IndieWeb
- [How to implement PubSubHubbub](https://blog.superfeedr.com/howto-pubsubhubbub/) from Superfeedr's Blog.
  > Describes how to work with pubsub. Though needs more code samples for instance in Node.js.
- [PubSubHubbub Core 0.4 Specifications (draft)](https://pubsubhubbub.github.io/PubSubHubbub/pubsubhubbub-core-0.4.html#rfc.section.4) - describes how pub sub works from discovery, subscribing, unsubscribing, publishing and more.
