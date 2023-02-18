
# Ubuntu - Automatize a configuração Pós Formatação

*******
📚 ÍNDICE

- [⭐ Motivacao](#⭐-motivação-⭐) <br>
  - [⭐ Por Onde Começar?](#por-onde-começar) <br>
  - [⭐ Shebang #!](#shebang) <br>
  - [⭐ Como Organizar meu Post Install?](#-como-organizar-meu-post-install) <br>
  - [⭐ Funções](#funções) <br>
  - [⭐ Dotfiles](#dotfiles) <br>
  - [⭐ Modularize com o Source!](#modularize-com-o-source) <br>
  - [⭐ E o Output?](#modularize-com-o-source) <br>
- [📚 Inicio](#inicio) <br>
  - [📚 Configurações](#configurações) <br>
    - [📚 app.ini](#appini) <br>
    - [📚 bashrc.ini](#bashrcini) <br>
    - [📚 bitbucket.ini](#bitbucketini) <br>
    - [📚 mvn.ini](#mvnini) <br>
    - [📚 zsh.ini](#zshini) <br>
- [📚 Como Executar?](#configurações) <br>
  
*******
## ⭐ Motivação ⭐

O intuito dessa automação é realizar a pré configuração do Sistema Operacional, com base no meu uso diário.

Todo o Script foi modularizado pensando na organização e facilidade de manutenção.

### ⭐ Por onde começar?

Para construir sua automação (post-install), precisamos saber de algumas informações, elas são com base no seu uso diário.

- Lista de Pacotes a serem instalados
- Os pacotes serão instalados via apt ou via snap ou via .deb??
- Preciso automatizar a atualização do meu SO?
- Terei repositórios do tipo Git?
- Como irei restaurar a configuração dos meu programas e conexão ssh?

### ⭐ Shebang #!

Manda instruções ao Kernel informando qual interpretador o mesmo irá chamar durante a execução do seu arquivo.

```
    #!/bin/bash 
    |     |
    |     |> Interpretador
    |> Shebang
```

### ⭐ Como organizar meu Post Install?

- Use e abuse do uso de funções para particionar seu script de acordo com a ação realizada.
- Tanto as variáveis quanto as funções precisam ter nomes de fácil entendimento.
- Documente seu código
- Use indentação
- Use Dotfiles

### ⭐ Funções

Nada mais que um trecho do código que realiza uma tarefa específica, podendo ser chamada em qualquer parte do seu programa / script

- Clareza do Código
- Reutilização
- Independência

![](images/funcoes.png)

### ⭐ Dotfiles

Veio para organizar seus arquivos de configuração ou scripts em um único lugar e utilizando links simbólicos manteremos a estrutura do Sistema Operacional.


- .gitconfig
- .bash
- .bashrc
- .profile
- .m2
- .zsh


![](images/simplescomovoar.png)

### ⭐ Modularize com o Source!

omando utilizado para ler e executar comandos de outros arquivos shell.

- .gitconfig
- .bash
- .bashrc
- .profile
- .m2
- .zsh


![](images/source_example_1.png)

### ⭐ E o Output?

Em **verde** é mostrado o Loglevel (INFO/WARN/ERROR) e a Data/Hora da Execução

Em **vermelho** é mostrado qual é o módulo que está executando estruturado em modules.{nome_modulo}.{nome_funcao}

Em **azul** é mostrado a mensagem da execução, basicamente o que está sendo feito naquele momento


![](images/output.png)


*******
# Inicio

Atualmente o Script foi pensado para ter as seguintes funções

**1)** **PostInstall**, servirá para instalar os pacotes necessários para uso do Sistema Operacional.

 - **packages** - Instalação dos Pacotes do SO.
 - **configure** - Configuração do zsh.

**2)** **System**, servirá para utilitários do sistema

 - **os** - Atualização do SO.
 - **progress_bar** - Barra de Progresso, utilizado no módulo packages.

**3)** **Util**, servirá para utilitários do sistema

 - **bitbucket** - Responsável por realizar o Clone e Atualização Repositorios Bitbucket.
 - **svn** - Responsável por realizar o Clone e Atualização Repositorios SVN Repository.
 - **mvn** - Responsável por realizar o Build dos projetos.

*******
# Configurações

Na pasta config, existe os seguintes arquivos de configuração.

*******
## **app.ini** 

```
REPOSITORY_WORKDIR - Diretorio para onde será realizado root dos repositórios
```

*******
### **bashrc.ini** 

```
BASHRC_ALIAS=() - Array para que você possa colocar os alias que serão cadastrados no bashrc
```

*******
### **bitbucket.ini** 

```
WORKSPACE=  - Nome do workspace no Bitbucket
PROJECTS=() - Array com o nome do projeto/repositorio no Bitbucket.
```
*******
### **mvn.ini** 

```
MVN_PROJECTS=() - Array com o nome do projeto/repositorio do Bitbucket, que você deseja realizar os builds locais utilizando o comando mvn

MVN_NODE_PROJECT - Nome do projeto/repositorio do Bitbucket, que você deseja realizar o build local utilizando o comando npm
```
******* 
### **zsh.ini**


```
ZSHRC_ALIAS=() - Array para que você possa colocar os alias que serão cadastrados no zshrc
```

*******
# Como executar?

