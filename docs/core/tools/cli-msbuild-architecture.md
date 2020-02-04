---
title: Arquitetura das ferramentas de linha de comando do .NET Core
description: Saiba mais sobre as camadas de ferramentas do .NET Core e o que foi alterado nas versões recentes.
ms.date: 03/06/2017
ms.openlocfilehash: 0064e7354f073be618bcf6a79962ab495927fadd
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980204"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Visão geral de alto nível das alterações nas ferramentas do .NET Core

Este documento descreve as alterações associadas à movimentação de *project.json* para o MSBuild e para o sistema de projeto *csproj*, com informações sobre as alterações na camada de ferramentas do .NET Core e a implementação dos comandos da CLI. Essas alterações ocorreram com o lançamento do SDK 1.0 do .NET Core e do Visual Studio 2017 em 7 de março de 2017 (veja o [comunicado](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)), mas foram implementadas inicialmente com o lançamento do SDK Preview 3 do .NET Core.

## <a name="moving-away-from-projectjson"></a>Deixando o project.json

A maior alteração nas ferramentas do .NET Core é certamente a [mudança de project.json para csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) como o sistema de projeto. As últimas versões das ferramentas de linha de comando não dão suporte a arquivos *project.json*. Isso significa que ele não pode ser usado para compilar, executar ou publicar aplicativos e bibliotecas com base em Project. JSON. Para usar esta versão das ferramentas, migre seus projetos existentes ou inicie novos.

Como parte dessa mudança, o mecanismo de build personalizado desenvolvido para compilar projetos project.json foi substituído por um mecanismo de build maduro e totalmente capaz, chamado [MSBuild](https://github.com/Microsoft/msbuild). O MSBuild é um mecanismo bem conhecido na Comunidade do .NET. Ele tem sido uma tecnologia fundamental desde o primeiro lançamento da plataforma. Como ele precisa criar aplicativos .NET Core, o MSBuild foi portado para o .NET Core e pode ser usado em qualquer plataforma em que o .NET Core seja executado. Uma das principais promessas do .NET Core é uma pilha de desenvolvimento de plataforma cruzada e nós garantimos que essa mudança não quebra essa promessa.

> [!TIP]
> Se você for novo no MSBuild e quiser saber mais sobre ele, poderá começar lendo o artigo [conceitos do MSBuild](/visualstudio/msbuild/msbuild-concepts) .

## <a name="the-tooling-layers"></a>As camadas de ferramentas

Com a mudança do sistema de projeto existente, bem como com a criação de comutadores de mecanismo, a pergunta que surge naturalmente é: essas mudanças alteram as "camadas" gerais do ecossistema de ferramentas do .NET Core? Existem novos bits e componentes?

Vamos começar recapitulando as camadas na Visualização 2, conforme mostrado na figura a seguir:

![A arquitetura de alto nível das ferramentas da Visualização 2](media/cli-msbuild-architecture/p2-arch.png)

As camadas das ferramentas são bastante simples. Na parte inferior, a base é a CLI do .NET Core. Todas as outras ferramentas de nível superior, como o Visual Studio ou o Visual Studio Code, dependem e contam com a CLI para criar projetos, restaurar dependências e assim por diante. Por exemplo, se o Visual Studio quisesse executar uma operação de restauração, ele chamaria o comando `dotnet restore` ([ver observação](#dotnet-restore-note)) na CLI.

Com a mudança para o novo sistema de projeto, o diagrama anterior se altera:

![Arquitetura de alto nível do SDK 1.0.0 do .NET Core](media/cli-msbuild-architecture/p3-arch.png)

A principal diferença é que a CLI não é mais a camada básica; agora, essa função é executada pelo "componente SDK compartilhado". Esse componente SDK compartilhado é um conjunto de destinos e tarefas associadas que são responsáveis por compilar código, publicá-lo, empacotar pacotes do NuGet e assim por diante. The .NET Core SDK is open-source and is available on GitHub on the [SDK repo](https://github.com/dotnet/sdk).

> [!NOTE]
> A "target" is an MSBuild term that indicates a named operation that MSBuild can invoke. Normalmente, ele está acoplado com uma ou mais tarefas que executam alguma lógica que o destino deve realizar. O MSBuild oferece suporte a muitos destinos prontos como `Copy` ou `Execute`; ele também permite aos usuários gravar suas próprias tarefas usando código gerenciado e definir metas para executar essas tarefas. Para mais informações, consulte [Tarefas do MSBuild](/visualstudio/msbuild/msbuild-tasks).

Todos os conjuntos de ferramentas agora consumem o componente SDK compartilhado e seus destinos, incluindo a CLI. For example, Visual Studio 2019 doesn't call into the `dotnet restore` ([see note](#dotnet-restore-note)) command to restore dependencies for .NET Core projects. Instead, it uses the "Restore" target directly. Como esses são os destinos do MSBuild, também é possível usar o MSBuild bruto para executá-los, usando o comando [dotnet msbuild](dotnet-msbuild.md).

### <a name="cli-commands"></a>Comandos da CLI

O componente SDK compartilhado significa que a maioria dos comandos CLI existentes foram reimplementados como destinos e tarefas do MSBuild. O que isso significa para os comandos CLI e o uso do conjunto de ferramentas?

From a usage perspective, it doesn't change the way you use the CLI. The CLI still has the core commands that existed in the .NET Core 1.0 Preview 2 release:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

These commands still do what you expect them to do (new up a project, build it, publish it, pack it, and so on). You can consult either the command's help screen (using `dotnet <command> --help`) or documentation on this site to get familiar with their behavior.

From an execution perspective, the CLI commands take their parameters and construct a call to "raw" MSBuild that sets the needed properties and runs the desired target. Para ilustrar melhor, considere o seguinte comando:

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

This command publishes an application into a `pub` folder using the "Release" configuration. Internamente, esse comando é convertido na seguinte invocação do MSBuild:

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Notable exceptions to this rule are the `new` and `run` commands. They have not been implemented as MSBuild targets.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
