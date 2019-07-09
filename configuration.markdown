## puppetmaster
$ yum install epel-release<br>
$ yum install puppet-server
$ puppet cert generate <hostname><br>
$ cd /var/lib/puppet/ssl { "certs/" "private_keys/"}<br>
$ vim /etc/puppet/puppet.conf <br>
<b>[main]<br>
	dns_alt_name = test.lab<br>
	certname = test.lab<br>
:wq</b> <br>

$ puppet resource service puppetmaster ensure=running<br>
$ systemctl status puppetmaster<br>
$ firewall-cmd --permanent --add-port={8140/tcp,8140/udp}<br>
$ firewall-cmd --reload<br>
$ puppet cert list	{/var/lib/puppet/ssl/ca/requests/}<br>
$ puppet cert sign "test2.lab"<br>
## puppet (Agent)
'/var/lib/puppet/ssl/ca/requests/pagent.pem'<br>
'/var/lib/puppet/ssl/certificate_requests/pagent.pem'<br>

$ yum install epel-release<br>
$ yum install puppet<br>
$ vim /etc/puppet/puppet.conf<br>
[agent]<br>
	server=test.lab<br>
	certname=pagent<br>
:wq<br>
$ puppet resource package puppet ensure=latest enable=true<br>
$ puppet agent -t<br>

$ puppet agent --configprint ssldir <br>
$ mv /var/lib/puppet/ssl /var/lib/puppet/ssl.old2<br>
$ puppet agent --test<br>

## Other links -:
 https://ask.puppet.com/question/4610/ssl-cert-self-signed-error/<br>
 https://puppet.com/docs/puppet/5.3/environments_creating.html<br>
 https://github.com/puppetlabs/docs-archive<br>
 https://github.com/puppetlabs/docs-archive/blob/master/puppet/3.6/ <br>
<br>
https://yum.puppetlabs.com <br>
https://apt.puppetlabs.com

