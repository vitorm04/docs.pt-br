---
title: Criando imagens do Docker do .NET Core
description: "Noções básicas de imagens do Docker e do .NET Core"
keywords: .NET, .NET Core, Docker
author: spboyer
ms.author: shboyer
ms.date: 08/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 038a67e3e7c3c9c120d76faa82cfc046233ab5df
ms.lasthandoff: 03/02/2017

---
 

#<a name="building-docker-images-for-net-core-applications"></a>Criando imagens do Docker para .NET Core Applications

Para entender como usar o .NET Core e o Docker juntos, precisamos primeiro conhecer as diferentes imagens do Docker que são oferecidas e quando é o caso de uso ideal para usá-las. Percorreremos aqui as variações oferecidas, compilaremos uma API Web do ASP.NET Core, usaremos as ferramentas do Yeoman Docker para criar um contêiner depurável e veremos como o Visual Studio Code pode ajudar no processo. 

## <a name="docker-image-optimizations"></a>Otimizações de imagem de Docker

Ao criar imagens do Docker para desenvolvedores, nos concentramos em três cenários principais:

- Imagens usadas para desenvolver aplicativos .NET Core
- Imagens usadas para compilar aplicativos .NET Core
- Imagens usadas para executar aplicativos .NET Core

Por que três imagens?
Ao desenvolver, compilar e executar aplicativos em contêineres, temos prioridades diferentes.
- **Desenvolvimento:** quanto tempo você leva para iterar alterações e a capacidade de depurá-las. O tamanho da imagem não é tão importante, pois você pode fazer alterações em seu código e observá-las rapidamente. Algumas das nossas ferramentas, como o [yo docker](https://aka.ms/yodocker) para uso no VS Code, usam essa imagem durante o tempo de desenvolvimento. 
- **Compilação:** o que é necessário para compilar seu aplicativo. Isso inclui o compilador e as outras dependências para otimizar os binários. Essa imagem não é aquela que você implanta, mas sim uma imagem que você usa para compilar o conteúdo incluído em uma imagem de produção. Essa imagem deve ser usada na integração contínua ou no ambiente de build. Por exemplo, em vez de instalar todas as dependências diretamente em um agente de build, este criaria instâncias de uma imagem para compilar o aplicativo com todas as dependências necessárias para compilar o aplicativo contido na imagem. O agente de build precisa saber apenas como executar essa imagem do Docker. 
- **Produção:** em quanto tempo você pode implantar e iniciar sua imagem. Essa imagem é pequena, por isso ela pode trafegar rapidamente pela rede do seu Registro do Docker para os hosts do Docker. O conteúdo está pronto para ser executado e habilitar o tempo mais rápido possível da execução do Docker até o processamento de resultados. A compilação dinâmica do código não é necessária no modelo de Docker imutável. O conteúdo colocado nesta imagem ficaria limitado aos binários e conteúdos necessários para executar o aplicativo. Por exemplo, a saída publicada usa `dotnet publish`, que contém os binários compilados, imagens, arquivos e arquivos.js e .css. Com o passar do tempo, você verá imagens que contém pacotes pré-compilados com JIT.  

Embora haja várias versões da imagem do .NET Core, todas elas compartilham uma ou mais camadas. A quantidade de espaço em disco necessário para armazenar ou para o delta obter o Registro é muito menor do que no todo, pois todas as imagens compartilham a mesma camada base e potencialmente outras.  

## <a name="docker-image-variations"></a>Variações de imagem do Docker

Para atingir os objetivos descritos acima, fornecemos variantes de imagem em [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/).

- `microsoft/dotnet:<version>-sdk`: isto é, **microsoft/dotnet:1.0.0-preview2-sdk**, essa imagem contém o SDK do .NET Core que inclui o .NET Core e a CLI (Ferramentas de Linha de Comando). Essa imagem é mapeada para o **cenário de desenvolvimento**. Ela seria usada para o desenvolvimento, depuração e teste de unidade local. Por exemplo, todo o desenvolvimento realizado antes de inserir o código. Essa imagem também pode ser usada para cenários **de build**.

- `microsoft/dotnet:<version>-core`: isto é, **microsoft/dotnet:1.0.0-core**, a imagem que executa [aplicativos .NET Core portáteis](../deploying/index.md) e é otimizada para executar seu aplicativo em **produção**. Ela não contém o SDK e tem por objetivo levar a saída otimizada do `dotnet publish`. O tempo de execução portátil é adequado para cenários de contêiner Docker, pois a execução de vários contêineres tira vantagem das camas de imagem compartilhadas.  

## <a name="alternative-images"></a>Imagens alternativas

Além dos cenários otimizados de desenvolvimento, build e produção, fornecemos imagens adicionais:

- `microsoft/dotnet:<version>-onbuild`: isto é, **microsoft/dotnet:1.0.0-preview2-onbuild**, contém gatilhos [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild). O build realizará a [COPY](https://docs.docker.com/engine/reference/builder/#/copy) do seu aplicativo, executará `dotnet restore` e criará uma instrução [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` para executar o aplicativo quando a imagem do Docker for executada. Embora não seja uma imagem otimizada para produção, ela pode ser útil para alguns simplesmente para copiar seu código-fonte em uma imagem e executá-lo. 

- `microsoft/dotnet:<version>-core-deps`: isto é, **microsoft/dotnet:1.0.0-core-deps**, use essa imagem se você desejar executar os aplicativos autocontidos. Ela contém o sistema operacional com todas as dependências nativas exigidas pelo .NET Core. Essa imagem também pode ser usada como uma imagem-base para suas próprias compilações CoreFX ou CoreCLR personalizadas. Enquanto a variante **onbuild** é otimizada para simplesmente colocar seu código em uma imagem e executá-lo, essa imagem é otimizada para ter apenas as dependências do sistema operacional necessárias para executar aplicativos .NET Core com o Tempo de Execução .NET empacotado com o aplicativo. Essa imagem geralmente não é otimizada para executar vários contêineres .NET Core no mesmo host, visto que cada imagem traz o tempo de execução do .NET Core dentro do aplicativo e as camadas de imagem não trazem qualquer benefício.   

Versões mais recentes de cada variante:

- `microsoft/dotnet` ou `microsoft/dotnet:latest` (inclui o SDK)
- `microsoft/dotnet:onbuild`
- `microsoft/dotnet:core`
- `microsoft/dotnet:core-deps`

Veja aqui uma lista das imagens após um `docker pull <imagename>` em um computador de desenvolvimento para mostrar os diversos tamanhos. Observe que a variante de desenvolvimento/compilação, `microsoft/dotnet:1.0.0-preview2-sdk`, é maior, pois contém o SDK para desenvolver e compilar seu aplicativo. A variante de produção, `microsoft/dotnet:core`, é menor, pois contém apenas o tempo de execução do .NET Core. A imagem mínima capaz de ser usada no Linux, `core-deps`, é muito menor, mas seu aplicativo precisará trazer uma cópia particular do Tempo de Execução .NET consigo. Como os contêineres já são barreiras de isolamento particular, você perderá essa otimização ao executar vários dotnet baseados em contêineres. 

```
REPOSITORY          TAG                     IMAGE ID            SIZE
microsoft/dotnet    1.0.0-preview2-onbuild  19b6a6c4b1db        540.4 MB
microsoft/dotnet    onbuild                 19b6a6c4b1db        540.4 MB
microsoft/dotnet    1.0.0-preview2-sdk      a92c3d9ad0e7        540.4 MB
microsoft/dotnet    core                    5224a9f2a2aa        253.2 MB
microsoft/dotnet    1.0.0-core-deps         c981a2eebe0e        166.2 MB
microsoft/dotnet    core-deps               c981a2eebe0e        166.2 MB
microsoft/dotnet    latest                  03c10abbd08a        540.4 MB
microsoft/dotnet    1.0.0-core              b8da4a1fd280        253.2 MB
```

## <a name="prerequisites"></a>Pré-requisitos

Para compilar e executar, você precisará de alguns itens instalados:

- [.NET Core](http://dot.net)
- [Docker](https://www.docker.com/products/docker) para executar seus contêineres Docker localmente 
- [Gerador Yeoman para ASP.NET](https://github.com/omnisharp/generator-aspnet) para criar o aplicativo da API Web
- [Gerador Yeoman para Docker](http://aka.ms/yodocker) da Microsoft

Instale os geradores Yeoman para ASP.NET Core e Docker usando npm 

```
npm install -g yo generator-aspnet generator-docker
```

> [!NOTE]
> Este exemplo usará o [Visual Studio Code](http://code.visualstudio.com) como editor.

## <a name="creating-the-web-api-application"></a>Criando o aplicativo da API Web

Para um ponto de referência, antes de colocarmos o aplicativo em contêineres, primeiro devemos executá-lo localmente. 

O aplicativo concluído está localizado no [repositório dotnet/core-docs no GitHub](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images).

Crie um diretório para seu aplicativo.

Abra um comando ou sessão de terminal nesse diretório e use o gerador Yeoman do ASP.NET digitando o seguinte:
```
yo aspnet
```

Selecione **Aplicativo da API Web** e digite **api** para o nome do aplicativo e pressione Enter.  Depois que o aplicativo é esboçado, mude para o diretório `/api` e restaure as dependências NuGet usando `dotnet restore`.

```
cd api
dotnet restore
```

Teste o aplicativo usando `dotnet run` e navegando até **http://localhost:5000/api/values**

```javascript
[
    "value1",
    "value2"
]
```

Use `Ctrl+C` para interromper o aplicativo.

## <a name="adding-docker-support"></a>Adicionando suporte ao Docker

A adição de suporte ao Docker para o projeto é realizada usando o gerador Yeoman da Microsoft. No momento, ele dá suporte a projetos do .NET Core, Node.js e Go criando um Dockerfile e scripts que ajudam a criar e executar projetos dentro de contêineres. Arquivos específicos do Visual Studio Code também são adicionados (launch.json, tasks.json) para depuração do editor e suporte à paleta de comandos.

```console
$ yo docker

     _-----_     ╭──────────────────────────╮
    |       |    │   Welcome to the Docker  │
    |--(o)--|    │        generator!        │
   `---------´   │     Let's add Docker     │
    ( _´U`_ )    │  container magic to your │
    /___A___\   /│           app!           │
     |  ~  |     ╰──────────────────────────╯
   __'.___.'__
 ´   `  |° ´ Y `

? What language is your project using? (Use arrow keys)
❯ .NET Core
  Golang
  Node.js

```

- Selecione `.NET Core` como o tipo de projeto
- `rtm` para a versão do .NET Core
- `Y` o projeto usa um servidor Web
- `5000` é a porta que o aplicativo da API Web está escutando em (http://localhost:5000)
- `api` para o nome da imagem
- `api` para o nome do serviço
- `api` para o projeto de composição 
- `Y` para substituir o Dockerfile atual

Quando o gerador estiver concluído, os seguintes arquivos são adicionados ao projeto

- .vscode/launch.json
- Dockerfile.debug
- Dockerfile
- docker-compose.debug.yml
- docker-compose.yml
- dockerTask.ps1
- dockerTask.sh
- .vscode/tasks.json

O gerador cria dois Dockerfiles.

**Dockerfile.Debug** – Este arquivo se baseia na imagem **microsoft/dotnet:1.0.0-preview2-sdk**, a qual podemos observar na lista de variantes que inclui o SDK, a CLI e o .NET Core, e será a imagem usada para desenvolvimento e depuração (F5). Incluir todos esses componentes gera uma imagem maior com um tamanho de aproximadamente 540 MB.

**Dockerfile** – Essa é a imagem de lançamento baseada em **microsoft/dotnet:1.0.0-core** e deve ser usada para produção. Essa imagem compilada tem aproximadamente 253 MB.

### <a name="creating-the-docker-images"></a>Criar as imagens do Docker
Usando o script `dockerTask.sh` ou `dockerTask.ps1`, podemos criar ou compor a imagem e o contêiner para o aplicativo **api** para um ambiente específico. Crie a imagem de **depuração** executando o comando a seguir.

```bash
./dockerTask.sh build debug
```

A imagem compilará o aplicativo ASP.NET, executará `dotnet restore`, adicionará o depurador à imagem, definirá um `ENTRYPOINT` e, por fim, copiará o aplicativo para a imagem. O resultado é uma imagem do Docker chamada *api* com um `TAG` de *depuração*.  Veja as imagens no computador usando `docker images`.

```bash
docker images

REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        a few seconds ago   779.8 MB
```

Outra maneira de gerar a imagem e executar o aplicativo dentro do contêiner Docker é abrir o aplicativo no Visual Studio Code e usar as ferramentas de depuração. 

Selecione o ícone de depuração na Barra de Exibição no lado esquerdo do VS Code.

![ícone de depuração vscode](./media/building-net-docker-images/debugging_debugicon.png)

Em seguida, toque no ícone de reprodução ou F5 para gerar a imagem e iniciar o aplicativo dentro do contêiner. A API Web será iniciada usando seu navegador da Web padrão em http://localhost:5000.

![Depuração de Ferramentas do VSCode Docker](./media/building-net-docker-images/docker-tools-vscode-f5.png)

Você pode definir pontos de interrupção em seu aplicativo, percorrê-los, etc., como se o aplicativo fosse executado localmente em seu computador de desenvolvimento em vez de dentro do contêiner. A vantagem da depuração dentro do contêiner é que essa é a mesma imagem que seria implantada em um ambiente de produção.

Criar a imagem de lançamento ou de produção requer simplesmente executar o comando do terminal passando o nome do ambiente do `release`.

```bash
./dockerTask build release
```

O comando cria a imagem com base na menor imagem de base **microsoft / dotnet:core**, [EXPÕE](https://docs.docker.com/engine/reference/builder/#/expose) a porta 5000, define o [PONTO DE ENTRADA](https://docs.docker.com/engine/reference/builder/#/entrypoint) para `dotnet api.dll` e o copia para o diretório `/app`. Não há nenhum depurador, o SDK ou `dotnet restore`, resultando em uma imagem muito menor. A imagem é denominada **api** com um `TAG` de **mais recente**.

```
REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        1 hour ago        779.8 MB
api                 latest               ef17184c8de6        1 hour ago        260.7 MB
```

## <a name="summary"></a>Resumo

Usando o gerador de Docker para adicionar os arquivos necessários ao aplicativo da API Web simplificou o processo de criar as versões de desenvolvimento e produção das imagens.  As ferramentas são plataforma cruzada, fornecendo também um script do PowerShell para obter os mesmos resultados no Windows, enquanto a integração do Visual Studio Code fornece um passo a passo de depuração do aplicativo dentro do contêiner. Compreendendo as variantes de imagem e os cenários de destino, você pode otimizar seu processo de desenvolvimento de loop interno, obtendo imagens otimizadas para implantações de produção.  



