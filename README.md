# lab-puppet
Puppet Tutorials
-------------------
## [Problem Before using CM Tools]
- Configuring a large number of Servers together becomes a daunting task.
- Scaling new servers without a configuration management tool is difficult.
- Development and Deployment environment mismatch halts work.

Configuration Management is all about bringing in consistency in the infrastructure. This is done by ensuring that the current design system, state and environment is known, trusted and agreed upon by everyone. "Configuration Management also helps record all the changes made in the system."

## [Configuration Management]
- Configuration Management tools provide an easier approach to manage and configure servers
- Writing individual scripts for servers time and again just to get a few things done has become obsolete.
- Configuration Management enables users to manage and configure the entire infrastructre and manage and configure the entire infrastructure and its environment.

## [Infrastructure as Code]
- Provisioning servers using infrastructure as code is easier than writing shell scripts
- Shell scripts require workflow definitions whereas CM tool scripts have pre-defined workflows.

A shell script and Configuration Management tool script, both are may adding a user to host, but while the CM tool script is ""easy to understand"" and ""write"", the shell script is hard to understand and you'll have to learn how to write Shell Scripts on you own.

[example - Using Shell Script ]
echo "myuser:*:1010:1010:user:/home/myuser:/bin/sh" >> /etc/passwd

[example- Using CM ToolScript]
user {'myuser': ensure => present, gid => "science", home => "/home/myuser", shell => "/bin/sh"}

## [Puppet]
puppet is a Configuration Managemnt tool that help orchestrate, provison, deploy and configure the entire infrastructure for an organization. Puppet enables users to concentrate more on making delivery faster and more reliable rather than continually fixing mistakes.
- Puppet works in the master slave architecture where one master server controls all the agents nodes.
- After the initial setup everything can be orchestrated and managed on the nodes through puppet.

## Q. Why puppet ??
A. These are some points :
- [Provisioning]: Easy deployment of application on large number of servers. Resources & their configuration can be defined at node level.
-[Consistent]: Maintains consistency across nodes- If a changes is done locally, it is rolled back to the original configuration
- [Ecosystem]: Puppet provides the suitable ecosystem to support and meet the needs of any company irrespective of their size.
- [Scalable]: Scaling across multiple teams and throusands of resources is easily done.

## [Puppet Architecture]
- Puppet works in a Master Slave architecture.
- Working in this model removes the issues faced while scaling.
- The Master Slave Architecture also gives a higher level of automation.

"Based on the facts received from the nodes, Puppet Server compiles a catalogue for the desired state of the nodes"

## [Catalog Compilation]
- To configure a node, the Puppet-agent downloads a Catalog from Puppet-server.
- Catalog holds the information of the desired state of each node.
- The Puppet Server Compiles teh catalog from three main resources i.e. Manifests Agent-Provided Data, External Data.

Agent => Server { => (fetch Node Object) => (set Variable) => (Assess the Main Manifest) => (Load Classes from Modules) => (Assess Classes from node object) => (Server) } ==> Respond back to Agent

## [Installation]
https://puppet.com/docs/pe/2017.3/installing_pe.html
https://puppet.com/docs/puppet/5.4/install_pre.html

$  rpm -vhi http://yum.puppetlabs.com/puppetlabs-release-el-7.noarch.rpm
$  yum update ; yum install puppet-server -y
