---
title: Ferramentas da CLI (Interface de Linha de Comando) do .NET Core
description: "Uma visão geral das ferramentas e recursos da CLI (Interface de linha de comando)."
keywords: CLI, ferramentas da CLI, .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/20/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 7c5eee9f-d873-4224-8f5f-ed83df329a59
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a8c91621095ea187dd4236db7533520556840c59
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-command-line-interface-cli-tools"></a>Ferramentas da CLI (Interface de linha de comando) do .NET Core

A CLI (Interface de linha de comando) do .NET Core é uma nova cadeia de ferramentas de plataforma cruzada para desenvolvimento de aplicativos em .NET Core. A CLI é a base na qual outras ferramentas de nível superior, como IDEs (Ambientes de Desenvolvimento Integrado), editores e orquestradores de build, se baseiam.

## <a name="installation"></a>Instalação

Use os instaladores nativos ou os scripts do shell de instalação:

* Os instaladores nativos são usados principalmente nas máquinas de desenvolvedores e usam o mecanismo de instalação nativo de cada plataforma com suporte, por exemplo, pacotes DEB no Ubuntu ou MSI no Windows. Esses instaladores instalam e configuram o ambiente para uso imediato do desenvolvedor, mas exigem privilégios administrativos no computador. Veja as instruções de instalação no [Guia de instalação do .NET Core](https://aka.ms/dotnetcoregs).
* Os scripts de shell são usados principalmente para configurar servidores de build ou para quando você quiser instalar as ferramentas sem privilégios administrativos. A instalação de scripts não instala os pré-requisitos na máquina, que devem ser instalados manualmente. Para saber mais, veja o [tópico de referência do script de instalação](dotnet-install-script.md). Para saber mais sobre como configurar a CLI no servidor de compilação de CI (integração contínua), confira [Usar o SDK e ferramentas do .NET Core na CI (Integração Contínua)](using-ci-with-cli.md).

Por padrão, a CLI instala lado a lado (SxS), para que várias versões das ferramentas da CLI possam coexistir em um único computador. Veja com mais detalhes como determinar qual versão é usada em um computador no qual várias versões estão instaladas na seção [Driver](#driver).

## <a name="cli-commands"></a>Comandos da CLI

Os comandos a seguir são instalados por padrão:

### <a name="basic-commands"></a>Comandos básicos

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [build](dotnet-build.md)
* [publish](dotnet-publish.md)
* [run](dotnet-run.md)
* [test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [migrate](dotnet-migrate.md)
* [clean](dotnet-clean.md)
* [sln](dotnet-sln.md)

### <a name="project-modification-commands"></a>Comandos de modificação de projeto

* [add package](dotnet-add-package.md)
* [add reference](dotnet-add-reference.md)
* [remove package](dotnet-remove-package.md)
* [remove reference](dotnet-remove-reference.md)
* [list reference](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Comandos avançados

* [nuget delete](dotnet-nuget-delete.md)
* [nuget locals](dotnet-nuget-locals.md)
* [nuget push](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [dotnet install script](dotnet-install-script.md)

A CLI adota um modelo de extensibilidade que permite especificar ferramentas adicionais para seus projetos. Para saber mais, confira o tópico [Modelo de extensibilidade da CLI do .NET Core](extensibility.md).

## <a name="command-structure"></a>Estrutura de comando

A estrutura de comando da CLI é composta pelo [driver ("dotnet")](#driver), [o comando (ou "verbo")](#command-verb) e [argumentos](#arguments) e [opções](#options) possíveis do comando. É possível ver esse padrão na maioria das operações de CLI, como ao criar um novo aplicativo de console e executá-lo a partir da linha de comando, como mostram os comandos a seguir quando executados a partir de um diretório chamado *my_app*:

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Driver

O driver é chamado [dotnet](dotnet.md) e tem duas responsabilidades, executar um [aplicativo dependente da estrutura](../deploying/index.md) ou executar um comando. A única vez em que `dotnet` é usado sem um comando é para iniciar um aplicativo.

Para executar um aplicativo dependente da estrutura, especifique o aplicativo após o driver, por exemplo, `dotnet /path/to/my_app.dll`. Ao executar o comando na pasta onde está a DLL do aplicativo, basta executar `dotnet my_app.dll`.

Quando você fornece um comando para o driver, `dotnet.exe` inicia o processo de execução do comando da CLI. Primeiro, o driver determina a versão das ferramentas a ser usada. Se a versão não for especificada nas opções de comando, o driver usará a versão mais recente disponível. Para especificar uma versão diferente da versão instalada mais recentemente, use a opção `--fx-version <VERSION>` (veja a referência ao [comando dotnet](dotnet.md)). Depois que a versão do SDK for determinada, o driver executará o comando.

### <a name="command-verb"></a>Comando ("verbo")

O comando (ou "verbo") é simplesmente um comando que executa uma ação. Por exemplo, `dotnet build` compila seu código. `dotnet publish` publica o código. Os comandos são implementados como um aplicativo de console usando uma convenção `dotnet-{verb}`. 

### <a name="arguments"></a>Arguments

Os argumentos que você passa na linha de comando são aqueles do comando invocado. Por exemplo, quando você executa `dotnet publish my_app.csproj`, o argumento `my_app.csproj` indica o projeto a ser publicado e é passado para o comando `publish`.

### <a name="options"></a>Opções

As opções que você passa na linha de comando são aquelas do comando invocado. Por exemplo, quando você executa `dotnet publish --output /build_output`, a opção `--output` e seu valor são passados para o comando `publish`. 

## <a name="migration-from-projectjson"></a>Migração do project.json

Se você tiver usado as ferramentas da Visualização 2 para produzir projetos baseados em *project.json*, veja o tópico [dotnet migrate](dotnet-migrate.md) para saber mais sobre como migrar seu projeto para MSBuild/*.csproj* para uso com as ferramentas de versão. Para projetos do .NET Core criados antes do lançamento das ferramentas do Preview 2, atualize manualmente o projeto seguindo as orientações em [Migrar do DNX para a CLI do .NET Core (Project)](../migration/from-dnx.md) e, em seguida, use `dotnet migrate` ou atualize diretamente seus projetos.

## <a name="additional-resources"></a>Recursos adicionais

* [Repositório do GitHub dotnet/CLI](https://github.com/dotnet/cli/)
* [Guia de instalação do .NET Core](https://aka.ms/dotnetcoregs)

