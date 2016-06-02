Properties for CPU Stats Reporting
==================================

These properties are used by the Probe to install the probe, filter and forward CPU usage statistics collected.

Configuration Properties
------------------------

Initialization can use system properties by calling Probe.initialize() or with an explicit Properties argument.

    gumshoe.cpu-usage.period     Reports will be generated at regular intervals (in milliseconds)
    gumshoe.cpu-usage.onshutdown If true, a report will be generated when the JVM exits
    gumshoe.cpu-usage.mbean      If true, enable JMX control of CPU usage probe
    gumshoe.cpu-usage.mbean.name Override name of JMX control
                                 (default is based on fully qualified class name) 
    gumshoe.cpu-usage.enabled    By default, the usage probe is initialized if periodic or shutdown
                                 reporting is enabled.  Override this behavior to install the probe
                                 now but enable/disable the reporting at another time.
    gumshoe.cpu-usage.priority   Thread priority for data collection thread (default value is Thread.MIN_PRIORITY)
    gumshoe.cpu-usage.sample            Thread data collection rate (milliseconds, default 5000)
                                        Generally multiple samples are accumulated into each report.
    gumshoe.cpu-usage.jitter            Collection rate should vary randomly by this 
                                        amount (milliseconds, default 0)
    gumshoe.cpu-usage.use-wait-times    Thread contention monitoring is enabled by default on
                                        JVMs that support it.  If false, contention monitoring
                                        is disabled.  This may reduce overhead, but thread blocked and
                                        waiting times will not be reported.  (Default is true.)

Stacks should generally be [filtered](../filters.md) reduce overhead and simplify later analysis:
                                
    gumshoe.cpu-usage.filter...    See common filter properties [here](filter-properties.md) 

Collected data reports are written to:

    gumshoe.cpu-usage.output=none   Do not write reports (ie, when your program is
                                    adding its own explicit Listener to receive reports)
    gumshoe.cpu-usage.output=stdout Write to System.out (the default)
    gumshoe.cpu-usage.output=file:/some/path    Write to a text file.
