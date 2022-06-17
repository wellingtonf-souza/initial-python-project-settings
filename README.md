
# Configuração inicial para projetos Python

Criado em um ambiente Vagrant, centos/7, com Python 3.7.11.

No centos/7 o comando `import sqlite3` gera o erro `No module named _sqlite3`, sendo necessário realizar os seguintes passos:

1. instalar o sqlite-devel
~~~bash
sudo yum install sqlite-devel
~~~

2. acessar a pasta Python-3.7.11 e executar os seguintes comandos:

~~~bash
./configure
~~~

~~~bash
make
~~~

~~~bash
sudo make altinstall
~~~

A partir dos passos acima o `import sqlite3` deve ocorrer normalmente. O `sqlite3` é necessário para o framework pre-commit.

Para iniciar o projeto basta executar:

~~~bash
virtualenv venv
~~~

~~~bash
source venv/bin/activate
~~~

~~~bash
pip install -r requirements.txt
~~~

~~~bash
pre-commit install
~~~

O arquivo `.pre-commit-config.yaml` executa os seguintes frameworks:
* black: ferramenta para formatar o código Python
* flake8: ferramenta para aplicação do Guia de Estilo Python
* pylint: Outra ferramenta para aplicação do Guia de Estilo Python
* bandit: ferramenta projetada para encontrar problemas comuns de segurança no código Python
* safety: ferramenta para verificar as dependências instaladas quanto a vulnerabilidades de segurança conhecidas
* pytest: ferramenta para execução de testes
* coverage: ferramenta para medir a cobertura do código
