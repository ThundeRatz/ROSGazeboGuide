---
layout: default
title: Executar em Docker
parent: Como executar o projeto
nav_order: 3
---

# Como executar o projeto em Docker

Além das opções previamente exploradas sobre como executar seus projetos com o WSL e com o Ubuntu, agora iremos conhecer uma terceira ferramenta: o Docker. Esta ferramenta consiste basicamente em uma espécie de máquina virtual que contém todos os *softwares* necessários para que você execute seu projeto.
Neste tutorial, iremos ensinar como rodar o seu projeto no Docker. Mas antes de tudo, uma das exigências do Docker é o WSL2. Se você ainda não o instalou, **[clique aqui](/InstalationGuides/WSL.md)**.

## Como Instalar o Docker

## Como configurar o Docker para rodar seu projeto

Primeiramente, é necessário fazer o *download* do *Dockerfile*. Este arquivo será o responsável por conter as dependências do seu projeto. O arquivo pode ser baixado por meio **[deste link]()**.

Após fazer o *download* deste arquivo, abra o **prompt de comando**/*PowerShell* e redirecione para a pasta que o arquivo está. O modo mais fácil de fazer isso é copiando o caminho do arquivo e digitando no prompt de comando:

```
cd [caminho do arquivo]
```

![GIF caminho do arquivo]()

Após isso, execute o comando abaixo para construir a imagem do projeto na sua máquina.

```
docker build -t dockercarrinhos .
```

e quando este processo estiver completo, execute em seguida:

```
docker run -it -p 7681:7681 -p 8080:8080 dockercarrinhos
```

![GIF executando Docker]()

Agora, para ver a simulação do seu projeto, basta abrir seu **navegador** e digitar na barra de URL 

```
http://localhost:8080/
```

![GIF localhost browser]()

Pronto! A simulação do seu projeto foi executada com sucesso utilizando o Docker.

![Simulação Docker]()

___
Caso os resultados sejam diferentes do tutorial ou existam dúvidas, não hesite em contatar um dos monitores da matéria!
