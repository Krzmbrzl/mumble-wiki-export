## What services are offered

The client can make use of a number of service offered by our
infrastructure. Namely things like:

  - Retrieving the **public server list**
  - Submitting anonymous **usage statistics**
  - Retrieving **overlay updates**
  - Retrieving **positional audio plugin updates**
  - Submitting **crash reports**
  - Polling for **client updates**
  - Retrieving client updates

## With whom and how does the client communicate

Mumble uses either *https* or *http* over standard ports for talking to
our services. Hosts that might be contacted are: *mumble.info*,
*\*.mumble.info* . Currently these domains are assigned to the following
IPs (might change in the future):

| IP             | Host(s)                                         |
| -------------- | ----------------------------------------------- |
| 52.201.18.254  | mumble.info / \*.mumble.info (exceptions below) |
| 46.253.206.249 | se.mumble.info / de.mumble.info                 |
| 50.97.218.234  | us.mumble.info                                  |

  - Usage statistics are submitted via a *http* post request to
    <http://mumble.info/usage.cgi> on port 80.
  - Crashreports are submitted as *https* post requests to
    <https://mumble.info/crashreport.php> on port 443
  - The channel list, overlay-, plugin- and client updates are retrieved
    via a http get request to mumble.info on port 80 on first try or as
    a fallback. During later exchanges the regional mirrors
    \*.mumble.info will be used. If all of these are unreachable
    panic.mumble.info is tried.

[Category:Documentation
English](Category:Documentation_English "wikilink")