nagios-plugin-graphite-target
=============================

Nagios plugin to perform simple check against targets in graphite.

Requirements
------------

Nagios::Plugin from CPAN
Access to Graphite webapp

Synopsis
--------

    check_graphite_target -m delta -t mysql.slow_queries.db1 -w 5 -c 10 -f -1h -h http://graphite.host.com

         -m MODE            see modes below
         -t TARGET          comma separate list of graphite targets
         -w THRESHOLD       standard nagios warning threshold (eg. -w 5 warns if over 5)
         -c THRESHOLD       standard nagios critical threshold
         -f TIME            AT-STYLE time spec (only useful in delta or percent mode)
         -h GRAPHITE_HOST   Graphite host

Modes
-----

###Raw mode (default mode)

Enable with `-m raw`

Warns if the raw value is outside given threshold. Good for metrics like CPU load,
IO utilisation etc that are not dependent on time.

###Delta mode

Enable with `-m delta`

Warns if the absolute change in a target is outside a given threshold. Useful for targets
that accumulate approximately linearly over time like MySQL counters.

###Percentage mode

Enable with `-m percent`

Warns if the absolute percentage change of a target is outside a given threshold. Unsuitable for targets that start at 0 or do not fluctuate much.

More info
---------

 * http://graphite.wikidot.com/url-api-reference
 * http://search.cpan.org/perldoc?Nagios%3A%3APlugin
