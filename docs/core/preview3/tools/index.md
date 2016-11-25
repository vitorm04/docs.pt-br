---
title: Ferramentas da CLI (Interface de Linha de Comando) do .NET Core
description: "Uma visão geral do que é a CLI (Interface de Linha de Comando) e seus principais recursos"
keywords: CLI, ferramentas da CLI, .NET, .NET Core
author: blackdwarf
ms.author: mairaw
manager: wpickett
ms.date: 10/06/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b70e9ac0-c8be-49f7-9332-95ab93e0e7bc
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: d9e689524a3100f1c5c129bdf13ed691a850ad2e

---

# <a name="net-core-command-line-interface-tools"></a>Ferramentas da interface de linha de comando do .NET Core

A CLI (interface de linha de comando) do .NET Core é uma nova cadeia de ferramentas de plataforma cruzada fundamental para desenvolver aplicativos .NET Core. Ela é “fundamental”, pois é a camada principal sobre quais outras ferramentas de nível mais elevado, como IDEs (Ambientes de Desenvolvimento Integrado), editores e orquestradores de build, se baseiam. 

Ela também é plataforma cruzada por padrão e tem a mesma área de superfície em todas as plataformas com suporte. Isso significa que, quando você aprender a usar as ferramentas, poderá usá-las da mesma maneira em qualquer uma das plataformas com suporte. 

## <a name="installation"></a>Instalação
Assim como acontece com qualquer ferramenta, o primeiro passo é obtê-la no seu computador. Dependendo do seu cenário, você pode usar instaladores nativos ou o script de shell de instalação para instalar a CLI.

Instaladores nativos destinam-se principalmente a computadores do desenvolvedor. A CLI é distribuída usando o mecanismo de instalação nativo de cada plataforma com suporte, por exemplo com pacotes DEB no Ubuntu ou MSI no Windows. Esses instaladores instalarão e configurarão o ambiente conforme necessário para o usuário utilizar a CLI imediatamente após a instalação. No entanto, eles também exigem privilégios administrativos no computador. Você pode exibir as instruções de instalação na [página de introdução ao .NET Core](https://aka.ms/dotnetcoregs).

Scripts de instalação, por outro lado, não exigem privilégios administrativos. No entanto, eles também não instalarão nenhum pré-requisito no computador. Você precisa instalar todos os pré-requisitos manualmente. Os scripts destinam-se principalmente a configurar servidores de build ou para quando você deseja instalar as ferramentas sem privilégios administrativos (observe as limitações dos pré-requisitos acima). Veja mais informações no [tópico de referência do script de instalação](dotnet-install-script.md). Se você estiver interessado em como configurar a CLI no seu servidor de build de CI (integração contínua), leia o tópico [CLI com servidores de CI](using-ci-with-cli.md). 

Por padrão, a CLI será instalada “lado a lado” (SxS). Isso significa que várias versões das ferramentas de CLI podem coexistir em um determinado momento em um único computador. A maneira como a versão correta é usada é explicada mais detalhadamente na seção [driver](#driver). 

### <a name="what-commands-come-in-the-box"></a>Quais comandos são fornecidos de fábrica?
Os comandos a seguir são instalados por padrão:

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [run](dotnet-run.md)
* [build](dotnet-build.md)
* [test](dotnet-test.md)
* [publish](dotnet-publish.md)
* [pack](dotnet-pack.md)

Também há uma maneira de importar mais comandos por projeto, bem como de adicionar seus próprios comandos. Isso será explicado em mas detalhes na [seção de extensibilidade](#extensibility). 

## <a name="working-with-the-cli"></a>Trabalhando com a CLI

Antes de entrarmos em mais detalhes, vejamos como é trabalhar com a CLI em uma exibição de 10.000 pés. O exemplo a seguir utiliza vários comandos da instalação padrão da CLI para inicializar um novo aplicativo de console simples, restaurar as dependências, compilar o aplicativo e executá-lo. 

```console
dotnet new
dotnet restore
dotnet build --output /stuff
dotnet /stuff/new.dll
```

Como você pode ver no exemplo anterior, há um padrão na maneira que você usa as ferramentas da CLI. Dentro desse padrão, podemos identificar três partes principais de cada comando:

1. [O driver ("dotnet")](#driver)
2. [O comando ou "verbo"](#the-verb)
3. [Argumentos de comando](#the-arguments)

### <a name="driver"></a>Driver
O driver é denominado [dotnet](dotnet.md). Essa é a primeira parte do que você invoca. O driver tem duas responsabilidades:

1. Executar aplicativos portáteis
2. Executar o verbo

O que ele faz depende do que é especificado na linha de comando. No primeiro caso, você deve especificar um aplicativo DLL portátil que o `dotnet` executaria semelhante a este: `dotnet /path/to/your.dll`. 

No segundo caso, o driver tenta invocar o comando especificado. Isso inicia o processo de execução do comando da CLI. Primeiro, o driver determina a versão das ferramentas que você deseja. É possível especificar a versão no arquivo [global.json](global-json.md) usando a propriedade `version`. Se não estiver disponível, o driver localizará a versão mais recente das ferramentas que estão instaladas no disco e usa essa versão. Depois que a versão é determinada, ela executa o comando. 

### <a name="the-verb"></a>O “verbo”
O verbo é simplesmente um comando que executa uma ação. `dotnet build` compila o código. `dotnet publish` publica o código. O verbo é implementado como um aplicativo de console nomeado segundo a convenção: `dotnet-{verb}`. Toda a lógica é implementada no aplicativo de console que representa o verbo. 

### <a name="the-arguments"></a>Os argumentos
Os argumentos que você passar na linha de comando são aqueles do verbo/comando real que está sendo invocado. Por exemplo, quando você digita `dotnet publish --output publishedapp`, o argumento `--output` é passado para o comando `publish`. 

## <a name="types-of-application-portability"></a>Tipos de portabilidade de aplicativo
A CLI habilita que os aplicativos sejam portáteis de duas maneiras principais:

1. Aplicativos totalmente portáteis que podem ser executados em qualquer lugar em que o .NET Core esteja instalado
2. Implantações autocontidas

Você pode aprender mais sobre ambos os tipos no tópico [Implantação de aplicativos .NET Core](../deploying/index.md). 

## <a name="migration-from-preview-3projectjson"></a>Migração da Visualização 3/project.json
Se você usou as ferramentas da Visualização 2 e projetos project.json, será possível consultar os documentos de comando [dotnet migrate](dotnet-migrate.md) para se familiarizar com o comando e saber como migrar seu projeto. 

> **Observação:** atualmente, o comando `dotnet migrate` não migra arquivos project.json da pré-visualização 2. 

## <a name="extensibility"></a>Extensibilidade
É claro que nem todas as ferramentas que você podia usar no seu fluxo de trabalho fará parte das ferramentas principais da CLI. No entanto, a CLI do .NET Core tem um modelo de extensibilidade que permite especificar ferramentas adicionais para seus projetos. Você pode saber mais no tópico [Modelo de extensibilidade da CLI do .NET Core](extensibility.md).

## <a name="summary"></a>Resumo
Essa foi uma breve visão geral dos recursos mais importantes da CLI. Você pode saber mais sobre isso acessando a referência e os tópicos conceituais neste site. Também há outros recursos que você pode usar:
* Repositório do GitHub [dotnet/CLI](https://github.com/dotnet/cli/)
* [Instruções de introdução](https://aka.ms/dotnetcoregs/)



<!--HONumber=Nov16_HO3-->


