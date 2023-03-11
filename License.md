**Mumble itself [is licensed under the very liberal 3-clause BSD
license](https://github.com/mumble-voip/mumble/blob/master/LICENSE).**

Our **Windows installer** distributes Mumble binaries under the more
restrictive **GPL**.

# Libraries

The licensing information of our software libraries **should not concern
end-users**. However, developers and distributors should take note to
conform to them.

| Library                      | License                                            | Exception<sup>?</sup>                                                                   |
| ---------------------------- | -------------------------------------------------- | --------------------------------------------------------------------------------------- |
| ASIO                         | Proprietary                                        |                                                                                         |
| Bonjour                      | Proprietary<sup>?</sup>                            |                                                                                         |
| Boost                        | [Boost 1.0](http://www.boost.org/LICENSE_1_0.txt)  |                                                                                         |
| CELT                         | 2-clause BSD                                       |                                                                                         |
| G15SDK                       | Proprietary                                        |                                                                                         |
| libFLAC                      | 3-clause BSD                                       |                                                                                         |
| libsndfile                   | LGPL                                               |                                                                                         |
| MySQL                        |                                                    | [OSS exception](http://www.mysql.com/about/legal/licensing/foss-exception/)             |
| OGG                          | BSD                                                |                                                                                         |
| OpenSSL                      | Apache 1.0 *(/4-clause BSD)*                       |                                                                                         |
| Opus                         | 3-clause BSD                                       |                                                                                         |
| protobuf                     | 3-clause BSD                                       |                                                                                         |
| Qt                           | LGPL 2.1                                           |                                                                                         |
| Qt translations (Additional) | MIT                                                |                                                                                         |
| speex                        | 3-clause BSD                                       |                                                                                         |
| ZeroC Ice                    | [GPLv2 / Proprietary](https://zeroc.com/licensing) | [Custom License](https://github.com/zeroc-ice/ice/blob/3.7/ICE_LICENSE#L27)<sup>?</sup> |

## Caveats

| Library             | License                     | Notes                                                                                                                                                                                     |
| ------------------- | --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <s>Bonjour Logo</s> | Would have to be negotiated | Not used. This does not affect the bonjour functionality itself. Displaying the Bonjour logo would require additional agreements with apple; thus we do not display it.                   |
| ZeroC Ice           | Custom Agreement            | We do have an agreement with ZeroC that allows us to distribute builds with Ice. If you want to distribute your own, you would have to contact and negotiate with ZeroC yourself as well. |

[Category:Documentation
English](Category:Documentation_English "wikilink")
[Category:Development](Category:Development "wikilink")