Niknak
======

FOSS JSON REST API for digital stores. The ultimate goal is to become the Wordpress of independent online sales.

This repository will include a reference implementation - Python server, client library, and test suite.

http://campadrenalin.github.io/Niknak

## High-level architecture

### Everything is pluggable

Authentication, media transformation, payment mechanisms, backend storage - Niknak is designed to be as agnostic as possible, so you can use it to build something that meets *your* needs, whether that's a very simple test instance running on localhost, or a set of production machines using every bell and whistle available.

#### Planned support

 * Authentication
   * Mozilla Persona (BrowserID)
   * Username/password
   * OAuth*
 * Payment
   * Bitcoin
   * Paypal
   * Ripple*
   * Stripe*
 * Storage
   * SQLite
   * PostGRE*
   * MariaDB/MySQL*
 * Cache layer
   * Redis*
   * Memcached*
 * Media transformation
  * PIL (The Python Image Library)
   * ffmpeg/avconv*
   * ImageMagick*

_\* Eventual support_

### Support for multiple currencies

This is baked in from the beginning. Most people will just want to set this to immediately convert to store currency, of course, but it's nice to have the general case covered.

### Everything is done through, and built from, the API

Niknak is the glue that ties everything together. Your web frontend, your console clients, third-party infrastructure and more. All of it can talk to Niknak in a common "language," and anyone can write software that builds on Niknak, because Niknak is designed to be *easy to build on.*

The great thing about this is that nobody gets left out in the cold. Any feature, if it exists, is available through the API. Which means any external technology can be programmed to use it. No product gets special treatment - or the shaft.

Because Niknak is an open-source project and is designed to enforce modularity in your store design, you can have confidence knowing that the common base of your store is being continually battle-tested by a wide variety of use cases, and developers can enjoy the benefits of a clean, self-contained codebase.

## I want to try Niknak!

Sorry, this is still in the design stages. It will be a long time before Niknak is powering any online stores. I appreciate your enthusiasm, though!

If you have questions, you can email them to philip@roaming-initiative.com. You may even have an effect on the direction and design of Niknak! I love to get outside opinions, and hear how people use (or plan to use) things I've worked on.

## API

### $root/

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Responds with store metadata</td>
    <td>Set store metadata</td>
    <td><i>No action</i></td>
    <td><i>No action</i></td>
  </tr>
</table>
