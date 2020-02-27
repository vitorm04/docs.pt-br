---
title: CLI do .NET Core
titleSuffix: ''
description: Uma visão geral do CLI do .NET Core e de seus recursos.
ms.date: 02/13/2020
ms.openlocfilehash: c491088f26a9aa1c065414e76fb0b80d554380b4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625976"
---
# <a name="net-core-cli-overview"></a>Visão geral de CLI do .NET Core

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

A CLI (interface de linha de comando) do .NET Core é uma ferramentas de plataforma cruzada para o desenvolvimento, a criação, a execução e a publicação de aplicativos .NET Core.

O CLI do .NET Core está incluído no [SDK do .NET Core](../sdk.md). Para saber como instalar o SDK do .NET Core, consulte [instalar o SDK do .NET Core](../install/sdk.md).

## <a name="cli-commands"></a>Comandos de CLI

Os comandos a seguir são instalados por padrão:

### <a name="basic-commands"></a>Comandos básicos

- [novo](dotnet-new.md)
- [restaurar](dotnet-restore.md)
- [build](dotnet-build.md)
- [publicar](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrar](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [ajuda](dotnet-help.md)
- [store](dotnet-store.md)

### <a name="project-modification-commands"></a>Comandos de modificação de projeto

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Comandos avançados

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Comandos de gerenciamento de ferramentas

- [instalação da ferramenta](dotnet-tool-install.md)
- [lista de ferramentas](dotnet-tool-list.md)
- [atualização de ferramenta](dotnet-tool-update.md)
- [restauração de ferramenta](global-tools.md#install-a-local-tool) **disponível a partir do SDK do .NET Core 3,0**
- [execução de ferramenta](global-tools.md#invoke-a-local-tool) **disponível a partir do SDK do .NET Core 3,0**
- [desinstalação de ferramenta](dotnet-tool-uninstall.md)

Ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados no prompt de comando. Você pode escrever ferramentas por conta própria ou instalar ferramentas escritas por terceiros. As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramenta e ferramentas locais. Para obter mais informações, consulte [visão geral das ferramentas do .NET Core](global-tools.md).

## <a name="command-structure"></a>Estrutura de comando

A estrutura de comando CLI consiste no [driver ("dotnet")](#driver), [do comando](#command) e possivelmente de [opções](#arguments) e [argumentos](#options) de comando. É possível ver esse padrão na maioria das operações de CLI, como ao criar um novo aplicativo de console e executá-lo a partir da linha de comando, como mostram os comandos a seguir quando executados a partir de um diretório chamado *my_app*:

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Driver

O driver é chamado [dotnet](dotnet.md) e tem duas responsabilidades, executar um [aplicativo dependente da estrutura](../deploying/index.md) ou executar um comando. 

Para executar um aplicativo dependente da estrutura, especifique o aplicativo após o driver, por exemplo, `dotnet /path/to/my_app.dll`. Ao executar o comando na pasta onde está a DLL do aplicativo, basta executar `dotnet my_app.dll`. Se você quiser usar uma versão específica do .NET Core Runtime, use a opção `--fx-version <VERSION>` (consulte a referência [do comando dotnet](dotnet.md)).

Quando você fornece um comando para o driver, `dotnet.exe` inicia o processo de execução do comando da CLI. Por exemplo:

```dotnetcli
dotnet build
```

Primeiro, o driver determina a versão do SDK a ser usada. Se não houver nenhum arquivo [global. JSON](global-json.md) , a versão mais recente do SDK disponível será usada. Isso pode ser uma versão prévia ou estável, dependendo do que há de mais recente no computador.  Depois que a versão do SDK é determinada, ela executa o comando.

### <a name="command"></a>{1&gt;Comando&lt;1}

O comando executa uma ação. Por exemplo, `dotnet build` compila código. `dotnet publish` publica o código. Os comandos são implementados como um aplicativo de console usando uma convenção `dotnet {command}`.

### <a name="arguments"></a>Argumentos

Os argumentos que você passa na linha de comando são aqueles do comando invocado. Por exemplo, quando você executa `dotnet publish my_app.csproj`, o argumento `my_app.csproj` indica o projeto a ser publicado e é passado para o comando `publish`.

### <a name="options"></a>{1&gt;Opções&lt;1}

As opções que você passa na linha de comando são aquelas do comando invocado. Por exemplo, quando você executa `dotnet publish --output /build_output`, a opção `--output` e seu valor são passados para o comando `publish`.

## <a name="see-also"></a>Consulte também

- [repositório do GitHub do dotnet/SDK](https://github.com/dotnet/sdk/)
- [Guia de instalação do .NET Core](../install/sdk.md)
