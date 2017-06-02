# Structured Facts
Newer versions of Facter support structured facts which can be arrays or hashes.
These facts are available in Puppet 3.3+, but aren't enabled by default. You can
enable structured facts by setting the *stringify_facts* option to `false` in
**puppet.conf** for master/agent/standalone nodes.

Until structured facts are the default, facts like the FQDN of a node need to be
retrieved through the legacy fact interface:

`$::fqdn`

The structured facts interface nests the FQDN inside the `$::networking` hash along
with other networking facts.

https://docs.puppet.com/facter/3.1/fact_overview.html#writing-structured-facts
