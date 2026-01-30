---
title: Query Builder Predicate Reference
description: Complete predicate reference for the Query Builder API.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Developing,Search,Query Builder
role: Developer
exl-id: c044d541-24d6-4975-9b38-6a4317a16358
---
# Query Builder Predicate Reference{#query-builder-predicate-reference}

>[!CAUTION]
>
>The information on this page is not exhaustive.
>
>For full information, see the list under **Available predicates** on the Query Builder Debugger console; for example, at:
>* [http://localhost:4502/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)
>
>For example, see:
>
>* [http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29](http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29) 

## General {#general}

* [root](#root)
* [group](#group)
* [orderby](#orderby)

## Predicates {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [excludepaths](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [fulltext](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [language](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [mainasset](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [memberOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [nodename](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [path](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [property](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [rangeproperty](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [relativedaterange](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [savedquery](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [similar](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [tag](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [tagid](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagsearch](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [type](/help/sites-developing/querybuilder-predicate-reference.md#type)

### `boolproperty` {#boolproperty}

Matches on JCR BOOLEAN properties. Only accepts the values " `true`" and " `false`." If set to " `false`," it matches if the property has the value " `false`" or if it does not exist at all. Useful for checking for boolean flags that are only set when enabled.

The inherited " `operation`" parameter has no meaning.

It supports facet extraction. Provides buckets for each `true` or `false` value, but only for existing properties.

#### Properties {#properties}

* **boolproperty**
  Relative path to property, for example, `myFeatureEnabled` or `jcr:content/myFeatureEnabled`.

* **value**
  Value to check property for, " `true`" or " `false`."

### `contentfragment` {#contentfragment}

Restricts the result to content fragments.

It does not support filtering.

It does not support facet extraction.

#### Properties {#properties-1}

* **contentfragment**
  It can be used with any value to check for content fragments.

### `dateComparison` {#datecomparison}

Compares two JCR DATE properties with each other. You can test if they are equal, unequal, greater than or greater-than-or-equal.

A filtering-only predicate and cannot use a search index.

#### Properties {#properties-2}

* **property1**

  Path to first date property.

* **property2**

  Path to second date property.

* **operation**

  " `equals`" for exact match, " `!=`" for unequality comparison, " `greater`" for property1 greater than property2, " `>=`" for property1 greater than or equal to property2. The default value is " `equals`."

### `daterange` {#daterange}

Matches JCR DATE properties against a date and time interval. Uses the ISO8601
format for dates and times ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) and allows also partial representations, like `YYYY-MM-DD`. Alternatively, the timestamp can be provided as the number of milliseconds since 1970 in the UTC timezone, the UNIX&reg; time format.

You can look for anything between two timestamps, anything newer or older than a given date, and also chose between inclusive and open intervals.

It supports facet extraction. Provides buckets "today," "this week," "this month," "last 3 months," "this year," "last year" and "earlier than last year."

It does not support filtering.

#### Properties {#properties-3}

* **property**

  Relative path to a `DATE` property, for example, `jcr:lastModified`.

* **lowerBound**

  Lower date bound to check property for, for example, `2014-10-01`.

* **lowerOperation**

  " `>`" (newer) or " `>=`" (at or newer), applies to the `lowerBound`. The default is " `>`."

* **upperBound**

  Upper bound to check property for, for example, `2014-10-01T12:15:00`.

* **upperOperation**

  " `<`" (older) or " `<=`" (at or older), applies to the `upperBound`. The default is " `<`."

* **timeZone**

  ID of timezone to use when it is not given as an ISO-8601 date string. The default is the default timezone of the system.

### `excludepaths` {#excludepaths}

Excludes nodes from the result where their path matches a regular expression.

A filtering-only predicate and cannot use a search index.

It does not support facet extraction.

#### Properties {#properties-4}

* **excludepaths**

  Regular expression matched against result paths, excluding matching ones from the result.

### `fulltext` {#fulltext}

Searches for terms in the fulltext index.

It does not support filtering.

It does not support facet extraction.

#### Properties {#properties-5}

* **fulltext**

  The fulltext search terms.

* **relPath**

  The relative path to search in the property or subnode. This property is optional.

### `group` {#group}

Lets nested conditions be built. Groups can contain nested groups. Everything in a query builder query is implicitly in a root group, which can have `p.or` and `p.not` parameters as well.

Example for matching either one of two properties against a value:

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Conceptually `(1_property` OR `2_property)`.

Example for nested groups:

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

Searches for the term "**Management**" within pages in `/content/geometrixx/en` or in assets in `/content/dam/geometrixx`.

Conceptually `fulltext AND ( (path AND type) OR (path AND type) )`. Such OR joins need good indexes for performance.

#### Properties {#properties-6}

* **p.or**

  If set to " `true`," only one predicate in the group must match. Defaults to " `false`," meaning all must match

* **p.not**

  If set to " `true`," it negates the group (defaults to " `false`").

* **&lt;predicate&gt;**

  Adds nested predicates.

* **N_&lt;predicate&gt;**

  Adds multiple nested predicates of the same time, like `1_property, 2_property, ...`.

### hasPermission {#haspermission}

Restricts the result to items where the current session has the specified [JCR privileges.](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

A filtering-only predicate and cannot use a search index. It does not support facet extraction.

#### Properties {#properties-7}

* **hasPermission**

  Comma-separated JCR privileges that the current user session must ALL have the node in question. For example, `jcr:write`, `jcr:modifyAccessControl`.

### `language` {#language}

Finds CQ pages in a specific language. This looks at both the page language property and the page path which often includes the language or locale in a top-level site structure.

A filtering-only predicate and cannot use a search index.

It supports facet extraction. Provides buckets for each unique language code.

#### Properties {#properties-8}

* **language**

  ISO language code, for example, "`de`."

### `mainasset` {#mainasset}

Checks if a node is a DAM main asset and not a subasset. Basically every node is not inside a "subassets" node. Does not check for the `dam:Asset` node type. To use this predicate, set " `mainasset=true`" or " `mainasset=false`," there are no further properties.

A filtering-only predicate and cannot use a search index.

It supports facet extraction and provides two buckets for main and subassets.

#### Properties {#properties-9}

* **mainasset**

  Boolean, " `true`" for main assets, " `false`" for subassets.

### memberOf {#memberof}

Finds items that are member of a specific [sling resource collection](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/resource/collection/ResourceCollection.html).

A filtering-only predicate and cannot use a search index. It does not support facet extraction.

#### Properties {#properties-10}

* **memberOf**

  Path of Sling resource collection.

### `nodename` {#nodename}

Matches on JCR node names.

It supports facet extraction. Provides buckets for each unique node name (filename).

#### Properties {#properties-11}

* **nodename**

  Node name pattern that allows wildcards: `*` = any or no char, `?` = any char, `[abc]` = only chars in brackets.

### `notexpired` {#notexpired}

Matches items by checking if a JCR DATE property is greater or equal than the current server time. Can be used to check on an " `expiresAt`" like date property and limit to only the ones that have not expired yet ( `notexpired=true`) or that have expired already ( `notexpired=false`).

It does not support filtering.

It supports facet extraction in the same way as the daterange predicate.

#### Properties {#properties-12}

* **notexpired**

  Boolean, " `true`" for not expired yet (date in the future or equal), " `false`" for expired (date in the past) (required).

* **property**

  Relative path to the `DATE` property to check (required).

### `orderby` {#orderby}

Lets the results be sorted. If ordering by multiple properties is required, this predicate must be added multiple times using the number prefix, such as `1_orderby=first`, `2_oderby=second`.

#### Properties {#properties-13}

* **orderby**

  Either JCR property name indicated by a leading @, for example, `@jcr:lastModified` or `@jcr:content/jcr:title`, or another predicate in the query, for example, `2_property`, on which to sort.

* **sort**

  Sort direction, either " `desc`" for descending or " `asc`" for ascending (default).

* **case**

  If set to `ignore`, it makes sorting case insensitive, meaning "a" comes before "B"; if empty or left out, sorting is case-sensitive, meaning "B" comes before "a"

### `path` {#path}

Searches within a given path.

It does not support facet extraction.

#### Properties {#properties-14}

* **path**

  Path pattern. When `exact=false` (default), the search matches the entire subtree under the specified path—similar to appending `//*` in XPath, but it does not include the base path itself. When `exact=true`, the search matches only the exact path, which can include `*` wildcards. If `self` is set, the search includes the base node and its entire subtree.


* **exact**

  If `exact` is true (on), the exact path must match, but it can contain simple wildcards ( `*`), that match names, but not " `/`"; if it is false (default) all descendents are included (optional).

* **flat**

  Searches only the direct children (like appending " `/*`" in `xpath`) (only used if ' `exact`' is not true, optional).

* **self**

  Searches the subtree but includes the base node given as path (no wildcards).

### `property` {#property}

Matches on JCR properties and their values.

It supports facet extraction. Provides buckets for each unique property value in the results.

#### Properties {#properties-15}

* **property**

  Relative path to property, for example, `jcr:title`.

* **value**

  Value to check the property for; follows the JCR property type to string conversions.

* **N_value**

  Use `1_value`, `2_value`, ... to check for multiple values (combined with `OR` by default, with `AND` if and=true) (since 5.3).

* **and**

  Set to true for combining multiple values ( `N_value`) with AND (since 5.3).

* **operation**

  Use `equals` for an exact match (default) and `unequals` for an inequality comparison. Use `like` to apply the optional `jcr:like` XPath function. Use `not` for no match (for example, `not(@prop)` in XPath); in this case, the `value` parameter is ignored. Use `exists` to check whether a property exists: `true` (default) requires the property, and `false` is equivalent to `not`.

* **depth**

  A number of wildcard levels underneath which the property and relative path can exist. For example, `property=size depth=2` checks node and size, node/&ast;/size, and node/&ast;/&ast;/size.

### `rangeproperty` {#rangeproperty}

Matches a JCR property against an interval. Applies to properties with linear types, such as `LONG`, `DOUBLE`, and `DECIMAL`. For `DATE`, see the daterange predicate that has optimized date format input.

You can define a lower bound and an upper bound or only one of them. The operation (for example, "lesser than" or "lesser or equals") can also be specified for lower and upper bound, individually.

It does not support facet extraction.

#### Properties {#properties-16}

* **property**

  Relative path to property.

* **lowerBound**

  Lower bound to check property for.

* **lowerOperation**

  " `>`" (default) or " `>=`," applies to the `lowerValue`

* **upperBound**

  Upper bound to check property for.

* **upperOperation**

  " `<`" (default) or " `<=`," applies to the `lowerValue`

* **decimal**

  " `true`" if the checked property is of type Decimal

### `relativedaterange` {#relativedaterange}

Matches `JCR DATE` properties against a date and time interval using time offsets relative to the current server time. You can specify `lowerBound` and `upperBound` using either a millisecond value or the bugzilla syntax `1s 2m 3h 4d 5w 6M 7y`. Prefix with " `-`" to indicate a negative offset before the current time. If you only specify `lowerBound` or `upperBound`, the other one defaults to 0, meaning the current time.

For example:

* `upperBound=1h` (and no `lowerBound`) would select anything in the next hour
* `lowerBound=-1d` (and no `upperBound`) would select anything in the last 24 hours
* `lowerBound=-6M` and `upperBound=-3M` would select anything 6 months to 3 months old
* `lowerBound=-1500` and `upperBound=5500` would select anything between 1500 milliseconds in the past and 5500 milliseconds in the future
* `lowerBound=1d` and `upperBound=2d` would select anything in the day after tomorrow

It does not take leap years into consideration and all months are 30 days.

It does not support filtering.

It supports facet extraction in the same way as the daterange predicate.

#### Properties {#properties-17}

* **upperBound**

  Upper date bound in milliseconds or `1s 2m 3h 4d 5w 6M 7y` (one second, two minutes, three hours, four days, five weeks, six months, seven years) relative to current server time, use "-" for negative offset.

* **lowerBound**

  Lower date bound in milliseconds or `1s 2m 3h 4d 5w 6M 7y` (one second, two minutes, three hours, four days, five weeks, six months, seven years) relative to current server time, use "-" for negative offset.

### `root` {#root}

Root predicate group. It supports all features of a group and lets you set global query parameters.

The name "root" is never used in a query, it is implicit.

#### Properties {#properties-18}

* **p.offset**

  The number indicating the start of the result page, that is, how many items to skip.

* **p.limit**

  The number indicating the page size.

* **p.guessTotal**

  To avoid the cost of calculating a full result total, do not count all matches. Instead, set a maximum total to count up to (for example, `1000`) to give users a rough size and exact totals for smaller results. Or set it to `true` to count only up to the minimum required: `p.offset + p.limit`.


* **p.excerpt**

  If set to " `true`," include full text excerpt in the result.

* **p.hits**

  (only for the JSON servlet) select the way the hits are written as JSON, with these standard ones (extensible via the ResultHitWriter service):

    * **simple**:

        Minimal items like `path`, `title`, `lastmodified`, `excerpt` (if set).

    * **full**:

        Results are rendered as Sling JSON for each node, with `jcr:path` showing the hit path. By default, the response includes only the node's direct properties; use `p.nodedepth=N` to include deeper content, where `0` returns the entire subtree. Set `p.acls=true` to include the current session's JCR permissions for each item (`create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).


    * **selective**:

        The response includes only the properties listed in `p.properties`, which is a space-separated list of relative paths (use `+` in URLs). If a relative path has a depth greater than 1, the output nests it as child objects. The special `jcr:path` property always includes the hit path.


### `savedquery` {#savedquery}

It includes all predicates of a persisted query builder query into the current query as a subgroup predicate.

It does not run an extra query but extend the current query.

Queries can be persisted programmatically using `QueryBuilder#storeQuery()`. The format can be either a multi-line String property or a `nt:file` node that contains the query as a text file in Java&trade; properties format.

It does not support facet extraction for the predicates of the saved query.

#### Properties {#properties-19}

* **savedquery**

  Path to the saved query (String property or `nt:file` node).

### `similar` {#similar}

Similarity search using JCR XPath's `rep:similar()`.

It does not support filtering. It does not support facet extraction.

#### Properties {#properties-20}

* **similar**
  Absolute path to the node for which to find similar nodes.

* **local**
  A relative path to a descendant node or `.` for the current node (optional, default is " `.`").

### `tag` {#tag}

Searches for content tagged with one or more tags, by specifying tag title paths.

It supports facet extraction. Provides buckets for each unique tag, using their current tag title path.

#### Properties {#properties-21}

* **tag**

  Tag title path to look for, for example, "Asset Properties : Orientation / Landscape."

* **N_value**

  Use `1_value`, `2_value`, ... to check for multiple tags (combined with `OR` by default, with `AND` if and=true) (since 5.6).

* **property**

  Property (or relative path to property) to look at (default " `cq:tags`")

### `tagid` {#tagid}

Searches for content tagged with one or more tags, by specifying tag IDs.

It supports facet extraction. Provides buckets for each unique tag, using their current tag ID.

#### Properties {#properties-22}

* **tagid**

  Tag id so you can look for, for example, " `properties:orientation/landscape`."

* **N_value**

  Use `1_value`, `2_value`, ... to check for multiple `tagids` (combined with `OR` by default, with `AND` if and=true) (since 5.6).

* **property**

  Property (or relative path to property) to look at (default " `cq:tags`").

### `tagsearch` {#tagsearch}

Searches for content tagged with one or more tags, by specifying keywords. Searches first for tags that contain these keywords in their titles, then restricts the result to only tagged items.

It does not support facet extraction.

#### Properties {#Properties-1}

* **tagsearch**

  Keyword to search for in tag titles.

* **property**

  Property (or relative path to property) to look at (default `cq:tags`).

* **lang**

  To search in a certain localized tag title only (for example, `de`).

* **all**

  (bool) Search entire tag fulltext, that is, all titles, description, and so on. Takes precedence over "l `ang`."

### `type` {#type}

Restricts results to a specific JCR node type, both primary node type or mixin type and finds subtypes of that node type. Repository search indexes must cover the node types for efficient execution.

It supports facet extraction. Provides buckets for each unique type in the results.

#### Properties {#Properties-2}

* **type**

  Node type or mixin name to search for, for example, `cq:Page`.
