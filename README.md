# APACHE SPARK COM DELTA LAKE E APACHE ICEBERG
> Trabalho de engenharia de dados com o tema: Apache spark com delta lake e apache iceberg

### Tecnologias utilizadas
- Python
- Spark
- Apache Iceberg
- Delta lake
- Jupiter lab

### Pré Requisitos
- Um ambiente virtual linux para que consiga rodar todo o projeto sem mais dificuldades 
#### Recomendados: 
- Wsl para rodar somente por comandos 
- Maquina virtual linux 

Para o desenvolvimento deste projeto foi utilizado o seguinte Linux: Ubuntu 24.04.

![Versão linux](assets/version.png)

### Instalação
Caso não possua algum destes instalados, por favor, faça a instalação e apos isto siga adiante
Será necessario:
- python vers: 3.12 ou mais recente (versao utilizada, 3.12 e 3.13)
- java vers: 8 ou 11 preferencia na mais atualizada (11)
- pipx
- Este projeto utilizou: [Poetry](https://python-poetry.org/docs/)

### Documentação
[Delta Lake Docs](https://docs.delta.io/latest/index.html)

[Apache iceberg Docs](https://iceberg.apache.org/docs/1.5.2/)

## Iniciando as variaveis de ambiente
- Alterando java home
```
echo 'export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"' >> ~/.bashrc
echo 'export PATH="$JAVA_HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## Comandos utilizados para setup do ambiente
- Acessando o shell do poetry
```poetry shell```
- Instalando dependências
```poetry install ```
- Rodando o notebook
```jupyter-lab```
Entrar no link fornecido pelo jupyter

## Dentro do ambiente
Dentro do spark voce deve selecionar o arquivo ipynb e apos escolher o arquivo, rodar as celulas, uma por vez.
![Spark](spark.png)

## Equipe
| [<img src="https://avatars.githubusercontent.com/u/130867213?v=4" width=115><br><sub>Jean Charles Guichard Guichard</sub>](https://github.com/Guichardx2) |  [<img src="https://avatars.githubusercontent.com/u/97752019?v=4" width=115><br><sub>Lucas da Rosa da Silva</sub>](https://github.com/Lorrust) |  [<img src="https://avatars.githubusercontent.com/u/125694923?v=4" width=115><br><sub>Matheus Augusto Daminelli</sub>](https://github.com/daminellis) |
| :---: | :---: | :---: |
