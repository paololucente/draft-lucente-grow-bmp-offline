---
title: "Figures for BMP Snapshots"
category: std
date: 2025

ipr: trust200902
submissiontype: IETF

author:
-
    name: Luuk Hendriks
    organization: NLnet Labs
    email: luuk@nlnetlabs.nl

--- abstract

This is just a helper doc to generate artsets (ascii+svg).


--- middle

# Figures


## Snapshot Message

~~~ aasvg
   0                   1                   2                   3
   0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
  +---------------+
  |   Version=4   |
  +---------------+-----------------------------------------------+
  |                        Message Length >= 6 + 6 + 16           |
  +---------------+-----------------------------------------------+
  | Msg Type=TBD1 |
  +---------------+---------------+-------------------------------+
  |        TLV Type = TBD2        |         Length = 16           |
  +-------------------------------+-------------------------------+
  |        Index = 0x0000         |
  +-------------------------------+-------------------------------+
  |                                                               |
  |                    Snapshot Id (16 octets)                    |
  |                                                               |
  |                                                               |
  +---------------------------------------------------------------+
~~~
{: title="The Snapshot Message wireformat, including the BMP Common Header and
the Snapshot Id TLV."}

## Flow on wire

~~~ aasvg

  (End-of-)                                             (Start-of)

+----------+ +----------+ +----------+ +-------------+ +----------+   
| Snapshot | | RouteMon | | RouteMon | | PeerUpNotif | | Snapshot |   
+----------+ +----------+ +----------+ +-------------+ +----------+   
|  Id TLV  | |          | |          | |             | |  Id TLV  |   
+----------+ |          | |          | |             | +----------+   
             |          | |          | |             | | Meta TLV |   
             +~~~~~~~~~~+ +~~~~~~~~~~+ +~~~~~~~~~~~~~+ +----------+   
             |  Id TLV  | |  Id TLV  | |  Id TLV     | | Meta TLV |   
             +----------+ +----------+ +-------------+ +----------+
------------------------------------------------------------------>

Exporting side                                         Station side

~~~
{: title="Flow of messages in a Snapshot, from exporter to station" }
{: anchor="fig-flow" }

