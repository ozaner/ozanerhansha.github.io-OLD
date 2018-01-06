---
layout: post
title: Binary Prefixes
tags: computer-science
---
### Decimal Prefixes
When dealing with very large or very small amounts it is common to
append one of the SI (metric system) prefixes to whatever unit is being
used. For example, the average human weighs 62000g but because that
number is so big we usually append *kilo* (the SI prefix meaning a
thousand) to the gram unit and say 62kg instead. This system works
just fine for all sorts of units but when it's applied to units of
information, like bits and bytes, a problem arises...

<!--more-->

### Binary Prefixes
You may have bought a hard drive or even a new phone and found that
there is a discrepancy between the amount of storage shown on the
package and the maximum amount displayed when you look in the
settings.

So what causes this disparity?

The difference between a kB (kilobyte) and a kiB (kibibyte).

Historically when a computer scientist wrote kB, for example, they didn't mean 1000 bytes. They meant 1024 bytes. This is because computers operate in binary which is based of powers of 2. In the kilobyte's case, 2<sup>10</sup> = 1024 which is close to 1000 and so close enough for programmer.

This changed around 1998 when the International Electrotechnical Commission (IEC) and other regulatory organizations created a new set of prefixes to be used as binary prefixes. The US National Institute of Standards and Technology (NIST) followed suit and required that the SI prefixes only be used in the decimal sense. Below is a table of the metric prefixes vs the binary ones.

Decimal Prefix (SI) | Value | Value (1000) | Binary Prefix (IEC) | Value | Value (1024)
--|--|--|--|--|--
kilo (k) | 10<sup>3</sup> | 1000 | kibi (ki) | 2<sup>10</sup> | 1024
mega (M) | 10<sup>6</sup> | 1000<sup>2</sup> | mebi (Mi) | 2<sup>20</sup> | 1024<sup>2</sup>
giga (G) | 10<sup>9</sup> | 1000<sup>3</sup> | gibi (Gi) | 2<sup>30</sup> | 1024<sup>3</sup>
tera (T) | 10<sup>12</sup> | 1000<sup>4</sup> | tebi (Ti) | 2<sup>40</sup> | 1024<sup>4</sup>
peta (P\) | 10<sup>15</sup> | 1000<sup>5</sup> | pebi (Pi\) | 2<sup>50</sup> | 1024<sup>5</sup>
exa (E) | 10<sup>18</sup> | 1000<sup>6</sup> | exbi (Ei) | 2<sup>60</sup> | 1024<sup>6</sup>
zetta (Z) | 10<sup>21</sup> | 1000<sup>7</sup> | zebi (Zi) | 2<sup>70</sup> | 1024<sup>7</sup>
yotta (Y) | 10<sup>24</sup> | 1000<sup>8</sup> | yobi (Yi) | 2<sup>80</sup> | 1024<sup>8</sup>

So problem solved, right? Well no. Most people have never heard of a kibibyte (kiB), mebibyte (MiB), or gibibyte (Gib) and probably never will. Hardware manufacturers know this and rather than deal with the consumer's perception of information storage, opt to just use the closest decimal prefix.

That said, there are a growing number of software and hardware applications that make use of binary prefixes.