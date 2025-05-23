---
acl_categories:
- '@tdigest'
- '@read'
arguments:
- name: key
  type: key
- multiple: true
  name: value
  type: double
categories:
- docs
- develop
- stack
- oss
- rs
- rc
- oss
- kubernetes
- clients
complexity: O(N) where N is the number of values specified.
description: Returns, for each input value, an estimation of the fraction (floating-point)
  of (observations smaller than the given value + half the observations equal to the
  given value)
group: tdigest
hidden: false
linkTitle: TDIGEST.CDF
module: Bloom
since: 2.4.0
stack_path: docs/data-types/probabilistic
summary: Returns, for each input value, an estimation of the fraction (floating-point)
  of (observations smaller than the given value + half the observations equal to the
  given value)
syntax_fmt: TDIGEST.CDF key value [value ...]
syntax_str: value [value ...]
title: TDIGEST.CDF
---
Returns, for each input value, an estimation of the fraction (floating-point) of (observations smaller than the given value + half the observations equal to the given value).

Multiple fractions can be retrieved in a single call.

## Required arguments

<details open><summary><code>key</code></summary>
is key name for an existing t-digest sketch.
</details>

<details open><summary><code>value</code></summary>
is value for which the CDF (Cumulative Distribution Function) should be retrieved.
</details>

## Return value

[Array reply]({{< relref "/develop/reference/protocol-spec#arrays" >}}) - the command returns an array of floating-points populated with fraction_1, fraction_2, ..., fraction_N. 

All values are 'nan' if the sketch is empty.

## Examples

{{< highlight bash >}}
redis> TDIGEST.CREATE t COMPRESSION 1000
OK
redis> TDIGEST.ADD t 1 2 2 3 3 3 4 4 4 4 5 5 5 5 5
OK
redis> TDIGEST.CDF t 0 1 2 3 4 5 6
1) "0"
2) "0.033333333333333333"
3) "0.13333333333333333"
4) "0.29999999999999999"
5) "0.53333333333333333"
6) "0.83333333333333337"
7) "1"
{{< / highlight >}}
