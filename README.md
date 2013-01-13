DNS-Junkie
==========

DNS and Virtual Hosts helper
Copyright (C) 2012 - John Murowaniecki

DNS-Junie is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.

DNS-Junkie is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with DNS-Junkie. If not, see <http://www.gnu.org/licenses/>.


TODO
-----
- Dinamic localization of bind, apache, init.d and others resources no matter what distribuition you're using;
- Distribution compatibility;
- Filter domains and subdomais with special characters;
- List of saved domains;
- Remotion of saved domains;

Warning
-------
This script uses bind9, named and apache2 to work, be sure that you have them installed and working correctly before continue. Depending on your operational system distribution some paths for configuration files may difefr - and that's a huge problem, this script is slack and dumb. (:

Usage
-----
	dnsjunkie comando [variable=value variable=value variable=value]

### Listing of commands that can be used:
* `help` -- shows help.

* `add` -- Add domains.

### Variables list
* `bind9` -- Defines the path for Bind9 '/etc/bind'.

* `httpd` -- Defines the path Apache2 '/etc/apache2'.

* `named` -- Defines the path to Named 'named.conf'.

* `htdocs` -- Defines the path to htdocs '/var/www'.

* `domain` -- Defines the domain to be added: `dnsjunkie add domain.com`

* `subdomains` ou `subdomain` -- Subdomain list. Also can be used as fourth parameter `dnsjunkie add domínio "cpanel proxy webmail"`
Do not use subdomains with special characters as '_-#$%@!*", and anothers, use only letters and numbers.

Examples of usage
-----------------
This example will create `somedomain.com` with `users`, `admin`, `panel` and `help` as subdomains.

    dnsjunkie add somedomain.com "users admin panel help"

Also you can use 

    dnsjunkie add domain=somedomain.com subdomains="users admin panel help"

To obtain exactly the same result.

If you have customized `htdocs` you'll need declarate the path of your htdoc or the Apache virtual server will brick on restart.

    dnsjunkie add domain=somedomain.com subdomains="users admin panel help" htdocs="/mnt/external_drive/www"
