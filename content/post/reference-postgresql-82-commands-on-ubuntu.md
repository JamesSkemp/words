+++
title = "Reference: PostgreSQL 8.2 commands on Ubuntu"
summary = "Reference of PostgreSQL 8.2 commands, via the command line."
draft = false
comments = true
date = "2007-06-23T08:45:00-05:00"
modified = "2007-07-15T20:23:45-05:00"
slug = "Reference-PostgreSQL-82-commands-on-Ubuntu"
blogengine = "e369ffc6-39c1-4411-9503-7ddbafc38f66"
categories = ["article"]
tags = ["ubuntu", "postgresql"]
+++

<p>
Below are the PostgreSQL 8.2 commands on Ubuntu.<!--more-->
</p>
<p>
These are listed here primarily for my own benefit.
</p>
<pre>
General
\c[onnect] [DBNAME|- USER|- HOST|- PORT|-]
connect to new database (currently &quot;template1&quot;)
\cd [DIR]      change the current working directory
\copyright     show PostgreSQL usage and distribution terms
\encoding [ENCODING]
show or set client encoding
\h [NAME]      help on syntax of SQL commands, * for all commands
\q             quit psql
\set [NAME [VALUE]]
set internal variable, or list all if no parameters
\timing        toggle timing of commands (currently off)
\unset NAME    unset (delete) internal variable
\! [COMMAND]   execute command in shell or start interactive shell
</pre>
<pre>
Query Buffer
\e [FILE]      edit the query buffer (or file) with external editor
\g [FILE]      send query buffer to server (and results to file or |pipe)
\p             show the contents of the query buffer
\r             reset (clear) the query buffer
\s [FILE]      display history or save it to file
\w FILE        write query buffer to file
</pre>
<pre>
Input/Output
\echo [STRING] write string to standard output
\i FILE        execute commands from file
\o [FILE]      send all query results to file or |pipe
\qecho [STRING]
write string to query output stream (see \o)
</pre>
<pre>
Informational
\d [NAME]      describe table, index, sequence, or view
\d{t|i|s|v|S} [PATTERN] (add &quot;+&quot; for more detail)
list tables/indexes/sequences/views/system tables
\da [PATTERN]  list aggregate functions
\db [PATTERN]  list tablespaces (add &quot;+&quot; for more detail)
\dc [PATTERN]  list conversions
\dC            list casts
\dd [PATTERN]  show comment for object
\dD [PATTERN]  list domains
\df [PATTERN]  list functions (add &quot;+&quot; for more detail)
\dg [PATTERN]  list groups
\dn [PATTERN]  list schemas (add &quot;+&quot; for more detail)
\do [NAME]     list operators
\dl            list large objects, same as \lo_list
\dp [PATTERN]  list table, view, and sequence access privileges
\dT [PATTERN]  list data types (add &quot;+&quot; for more detail)
\du [PATTERN]  list users
\l             list all databases (add &quot;+&quot; for more detail)
\z [PATTERN]   list table, view, and sequence access privileges (same as \dp)
</pre>
<pre>
Formatting
\a             toggle between unaligned and aligned output mode
\C [STRING]    set table title, or unset if none
\f [STRING]    show or set field separator for unaligned query output
\H             toggle HTML output mode (currently off)
\pset NAME [VALUE]
set table output option
(NAME := {format|border|expanded|fieldsep|footer|null|
numericlocale|recordsep|tuples_only|title|tableattr|pager})
\t             show only rows (currently off)
\T [STRING]    set HTML &lt;table&gt; tag attributes, or unset if none
\x             toggle expanded output (currently off)
</pre>
<pre>
Copy, Large Object
\copy ...      perform SQL COPY with data stream to the client host
\lo_export LOBOID FILE
\lo_import FILE [COMMENT]
\lo_list
\lo_unlink LOBOID    large object operations
</pre>

