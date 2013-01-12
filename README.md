DNS-Junkie
==========

DNS and Virtual Hosts helper
Copyright (C) 2012 - John Murowaniecki

DNS-Junie is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.

DNS-Junkie is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with DNS-Junkie. If not, see <http://www.gnu.org/licenses/>.


TODO
-----
- Localização dinâmica dos caminhos do bind, apache, init.d e outros.
- Compatibilidade entre distribuições e scripts de inicialização.
- Impedir o registro de domínios e subdomínios com underline.
- Listagem de domínios cadastrados.
- Remoção de domínios cadastrados.

Warning
-------
Este script utiliza os serviços BIND9, Named e Apache2 para funcionar, certifique-se de que eles estejam instalados e funcionando corretamente antes de prosseguir. Dependendo do seu sistema operacional ou distribuição os nomes dos caminhos para os arquivos de configuração podem variar - e isso é um problema, visto que esse é um script meio burro. (:

Usage
-----
	dnsjunkie comando [variavel=valor variavel=valor variavel=valor]

### Listagem de comandos que podem ser utilizados:
* `test` -- Para efetuar uma verificação se seu sistema possúi tudo o que é necessário para que esse trapo funcione.

* `help` -- Exibe esse texto.

* `list` -- Lista domínios instalados por este script.

* `add|del` -- Adicionar domínio ao BIND e ao Apache2.

### Listagem de variáveis utilizadas:
* `bind9` -- Define caminho pra a pasta de configuração do Bind9 ou utiliza como padrão '/etc/bind'.

* `httpd` -- Define caminho pra a pasta de configuração do Apache2 ou utiliza como padrão '/etc/apache2'.

* `named` -- Define caminho pra o arquivo de configuração do arquivo Named (arquivo named.conf).

* `htdocs` -- Define caminho pra a pasta htdocs do domínio informado ou utiliza como padrão '/var/www'.

* `domain` -- Define domínio a ser cadastrado. Pode ser utilizado como terceiro parâmetro: `dnsjunkie add domínio`

* `subdomains` ou `subdomain` -- Lista de subdomínios domínios a serem configurados. Pode ser utilizado como quarto parâmetro `dnsjunkie add domínio "cpanel proxy webmail"`
Não utilize subdomínios contendo caracteres especiais como '_-#$%@!*" entre outros, utilize apenas letras e números*

Examples of usage
-----------------
This example will create `somedomain.com` with `users`, `admin`, `panel` and `help` as subdomains.

    dnsjunkie add somedomain.com "users admin panel help"

Also you can use 

    dnsjunkie add domain=somedomain.com subdomains="users admin panel help"

To obtain exactly the same result.

If you have customized `htdocs` you'll need declarate the path of your htdoc or the Apache virtual server will brick on restart.

    dnsjunkie add domain=somedomain.com subdomains="users admin panel help" htdocs="/mnt/external_drive/www"
