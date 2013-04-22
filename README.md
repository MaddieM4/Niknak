Niknak
======

![Project Logo](http://campadrenalin.github.io/Niknak/images/NiknakLogo180x127.png)

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

Site metadata is a simple JSON object containing configuration and version information.

### $root/users/

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>User statistics</td>
    <td><i>No action</i></td>
    <td>Create new user</td>
    <td><i>No action</i></td>
  </tr>
</table>

User statistics are currently arbitrary, but may be standardized in the future.

User properties TBD.

### $root/users/$uid

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>User properties</td>
    <td>Update user properties</td>
    <td><i>No action</i></td>
    <td>Delete user</td>
  </tr>
</table>

User properties TBD.

### $root/products

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>List of products. Uses variables to filter and sort.</td>
    <td><i>No action</i></td>
    <td>Create new product.</td>
    <td><i>No action</i></td>
  </tr>
</table>

### $root/products/$product_id

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Product properties</td>
    <td>Update product properties</td>
    <td><i>No action</i></td>
    <td>Delete product</td>
  </tr>
</table>

Product properties TBD.

### $root/payments

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Payment statistics</td>
    <td><i>No action</i></td>
    <td>Create new payment</td>
    <td><i>No action</i></td>
  </tr>
</table>

### $root/payments/$payment_id

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Payment properties</td>
    <td>Update payment properties</td>
    <td>Confirm payment</td>
    <td>Cancel payment</td>
  </tr>
</table>

The properties you can update after confirmation are very limited - basically just the memo.

### $root/specials

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>List all currently available and historical specials</td>
    <td><i>No action</i></td>
    <td><i>No action</i></td>
    <td><i>No action</i></td>
  </tr>
</table>

Specials are things like "Buy one get one free." Unlike most things, they are ID'd by name. They are built into the system, and cannot be custom-defined without modifying the Niknak code, but may have any per-product parameters.

### $root/specials/$special_name

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Description of special, and list of products it currently applies to.</td>
    <td><i>No action</i></td>
    <td><i>No action</i></td>
    <td><i>No action</i></td>
  </tr>
</table>

### $root/purchases

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Purchase statistics</td>
    <td><i>No action</i></td>
    <td>New purchase</td>
    <td><i>No action</i></td>
  </tr>
</table>

A purchase associates a user, a total, a memo, and a list of `[quantity, product_id, specials]` tuples.

### $root/purchases/$purchase_id

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Purchase properties</td>
    <td>Update purchase properties</td>
    <td>Confirm purchase</td>
    <td>Cancel purchase</td>
  </tr>
</table>

Purchase properties cannot be changed after confirmation, but the purchase may be canceled, with server-side logic to determine if the cancellation is successful. Cancelling a purchase reverts ownership of the products, and refunds the customer.

### $root/tags

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>List of all available tags</td>
    <td><i>No action</i></td>
    <td>New tag</td>
    <td><i>No action</i></td>
  </tr>
</table>

Listing includes shallow metadata for each tag (description, image URL, etc.)

### $root/tags/$tag_name

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Tag properties</td>
    <td>Update tag properties</td>
    <td><i>No action</i></td>
    <td>Delete tag</td>
  </tr>
</table>

### $root/permission

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td><i>No action</i></td>
    <td><i>No action</i></td>
    <td>Create new permission</td>
    <td><i>No action</i></td>
  </tr>
</table>

### $root/permission/$permission_id

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Return permission data</td>
    <td>Update permission data</td>
    <td><i>No action</i></td>
    <td>Revoke permission</td>
  </tr>
</table>

Permissions have a few properties.

 * User ID
 * Type (read, write, or both)
 * Method
 * Object ID
 * Scope

Method is an HTTP method (i.e. "PUT") and Object ID is an API URL (i.e. "$root/users"). Scope may be null, or a space-separated list of property names (for restricting what properties can be seen or updated).

The term user ID is a bit disingenuous. All UIDs under 1000 (a configurable number) represent user groups. The two default groups are admin (0) and everyone (1). The admin group can be edited, the everyone group cannot. Thus, permissions with a UID &lt; 1000 are group permissions.

### $root/groups

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>List existing groups</td>
    <td><i>No action</i></td>
    <td>Create new group</td>
    <td><i>No action</i></td>
  </tr>
</table>

A group list is a {"$id":"$groupname"} mapping.

### $root/groups/$group_id

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Return group metadata</td>
    <td>Update group metadata</td>
    <td>Add user to group</td>
    <td>Delete group</td>
  </tr>
</table>

### $root/groups/$group_id/$user_id

<table>
  <tr>
    <td><b>GET</b></td>
    <td><b>POST</b></td>
    <td><b>PUT</b></td>
    <td><b>DELETE</b></td>
  </tr>
  <tr>
    <td>Return 'true' or 'false'</td>
    <td><i>No action</i></td>
    <td><i>No action</i></td>
    <td>Delete user from group</td>
  </tr>
</table>

Can be GET-ed to determine if user is a member of a group. If 'false', response code must also be 404.
