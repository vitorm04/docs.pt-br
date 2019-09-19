---
title: Ferramentas da CLI (Interface de Linha de Comando) do .NET Core
description: Uma visão geral das ferramentas e recursos da CLI (Interface de linha de comando) do .NET Core.
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: 4ff5cfd6c5a70c92387911ab87ddea5cee80275e
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117396"
---
# <a name="net-core-command-line-interface-cli-tools"></a>Ferramentas da CLI (Interface de linha de comando) do .NET Core

A CLI (Interface de linha de comando) do .NET Core é uma nova cadeia de ferramentas de plataforma cruzada para desenvolvimento de aplicativos em .NET Core. A CLI é a base na qual outras ferramentas de nível superior, como IDEs (Ambientes de Desenvolvimento Integrado), editores e orquestradores de build, se baseiam.

## <a name="installation"></a>Instalação

Use os instaladores nativos ou os scripts do shell de instalação:

- Os instaladores nativos são usados principalmente nas máquinas de desenvolvedores e usam o mecanismo de instalação nativo de cada plataforma com suporte, por exemplo, pacotes DEB no Ubuntu ou MSI no Windows. Esses instaladores instalam e configuram o ambiente para uso imediato do desenvolvedor, mas exigem privilégios administrativos no computador. Veja as instruções de instalação no [Guia de instalação do .NET Core](https://aka.ms/dotnetcoregs).
- Os scripts de shell são usados principalmente para configurar servidores de build ou para quando você quiser instalar as ferramentas sem privilégios administrativos. A instalação de scripts não instala os pré-requisitos na máquina, que devem ser instalados manualmente. Para saber mais, veja o [tópico de referência do script de instalação](dotnet-install-script.md). Para saber mais sobre como configurar a CLI no servidor de compilação de CI (integração contínua), confira [Usar o SDK e ferramentas do .NET Core na CI (Integração Contínua)](using-ci-with-cli.md).

Por padrão, a CLI instala lado a lado (SxS), para que várias versões das ferramentas da CLI possam coexistir em um único computador. Veja com mais detalhes como determinar qual versão é usada em um computador no qual várias versões estão instaladas na seção [Driver](#driver).

## <a name="cli-commands"></a>Comandos da CLI

Os comandos a seguir são instalados por padrão:

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Comandos básicos**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [ajuda](dotnet-help.md)
- [repositório](dotnet-store.md)

**Comandos de modificação de projeto**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**Comandos avançados**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Comandos básicos**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)

**Comandos de modificação de projeto**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**Comandos avançados**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

---

A CLI adota um modelo de extensibilidade que permite especificar ferramentas adicionais para seus projetos. Para saber mais, confira o tópico [Modelo de extensibilidade da CLI do .NET Core](extensibility.md).

## <a name="command-structure"></a>Estrutura de comando

A estrutura de comando CLI consiste no [driver ("dotnet")](#driver), [do comando](#command) e possivelmente de [opções](#options) e [argumentos](#arguments) de comando. É possível ver esse padrão na maioria das operações de CLI, como ao criar um novo aplicativo de console e executá-lo a partir da linha de comando, como mostram os comandos a seguir quando executados a partir de um diretório chamado *my_app*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Driver

O driver é chamado [dotnet](dotnet.md) e tem duas responsabilidades, executar um [aplicativo dependente da estrutura](../deploying/index.md) ou executar um comando. 

Para executar um aplicativo dependente da estrutura, especifique o aplicativo após o driver, por exemplo, `dotnet /path/to/my_app.dll`. Ao executar o comando na pasta onde está a DLL do aplicativo, basta executar `dotnet my_app.dll`. Se você quiser usar uma versão específica do .NET Core Runtime, use a opção `--fx-version <VERSION>` (consulte a referência [do comando dotnet](dotnet.md)).

Quando você fornece um comando para o driver, `dotnet.exe` inicia o processo de execução do comando da CLI. Por exemplo:

```dotnetcli
dotnet build
```

Primeiro, o driver determina a versão do SDK a ser usada. Se não houver uma ['global.json'](global-json.md), a versão mais recente do SDK disponível será usada. Isso pode ser uma versão prévia ou estável, dependendo do que há de mais recente no computador.  Depois que a versão do SDK é determinada, ela executa o comando.

### <a name="command"></a>Comando

O comando executa uma ação. Por exemplo, `dotnet build` compila código. `dotnet publish` publica o código. Os comandos são implementados como um aplicativo de console usando uma convenção `dotnet {command}`.

### <a name="arguments"></a>Arguments

Os argumentos que você passa na linha de comando são aqueles do comando invocado. Por exemplo, quando você executa `dotnet publish my_app.csproj`, o argumento `my_app.csproj` indica o projeto a ser publicado e é passado para o comando `publish`.

### <a name="options"></a>Opções

As opções que você passa na linha de comando são aquelas do comando invocado. Por exemplo, quando você executa `dotnet publish --output /build_output`, a opção `--output` e seu valor são passados para o comando `publish`.

## <a name="migration-from-projectjson"></a>Migração do project.json

Se você tiver usado as ferramentas da Visualização 2 para produzir projetos baseados em *project.json*, veja o tópico [dotnet migrate](dotnet-migrate.md) para saber mais sobre como migrar seu projeto para MSBuild/ *.csproj* para uso com as ferramentas de versão. Para projetos do .NET Core criados antes do lançamento das ferramentas da Versão prévia 2, siga as orientações descritas em [Migrando do DNX para a CLI do .NET Core (project.json)](../migration/from-dnx.md) para atualizar o projeto manualmente e, depois, use `dotnet migrate` ou atualize os projetos diretamente.

## <a name="see-also"></a>Consulte também

- [Repositório do GitHub dotnet/CLI](https://github.com/dotnet/cli/)
- [Guia de instalação do .NET Core](https://aka.ms/dotnetcoregs)
