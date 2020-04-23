---
title: Arquitetura das ferramentas de linha de comando do .NET Core
description: Saiba mais sobre as camadas de ferramentas do .NET Core e o que foi alterado nas versões recentes.
ms.date: 03/06/2017
ms.openlocfilehash: e1a9fe59225c17d54f6e7213d2b3c3fa70ee58e0
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102873"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Visão geral de alto nível das alterações nas ferramentas do .NET Core

Este documento descreve as alterações associadas à movimentação de *project.json* para o MSBuild e para o sistema de projeto *csproj*, com informações sobre as alterações na camada de ferramentas do .NET Core e a implementação dos comandos da CLI. Essas alterações ocorreram com o lançamento do SDK 1.0 do .NET Core e do Visual Studio 2017 em 7 de março de 2017 (veja o [comunicado](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)), mas foram implementadas inicialmente com o lançamento do SDK Preview 3 do .NET Core.

## <a name="moving-away-from-projectjson"></a>Deixando o project.json

A maior alteração nas ferramentas do .NET Core é certamente a [mudança de project.json para csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) como o sistema de projeto. As últimas versões das ferramentas de linha de comando não dão suporte a arquivos *project.json*. Isso significa que ele não pode ser usado para construir, executar ou publicar aplicativos e bibliotecas baseados em project.json. Para usar esta versão das ferramentas, migre seus projetos existentes ou inicie novos.

Como parte dessa mudança, o mecanismo de build personalizado desenvolvido para compilar projetos project.json foi substituído por um mecanismo de build maduro e totalmente capaz, chamado [MSBuild](https://github.com/Microsoft/msbuild). O MSBuild é um mecanismo bem conhecido na comunidade .NET. Tem sido uma tecnologia fundamental desde o primeiro lançamento da plataforma. Como ele precisa criar aplicativos .NET Core, o MSBuild foi portado para o .NET Core e pode ser usado em qualquer plataforma em que o .NET Core seja executado. Uma das principais promessas do .NET Core é uma pilha de desenvolvimento de plataforma cruzada e nós garantimos que essa mudança não quebra essa promessa.

> [!TIP]
> Se você é novo no MSBuild e gostaria de saber mais sobre ele, você pode começar lendo o artigo de conceitos do [MSBuild.](/visualstudio/msbuild/msbuild-concepts)

## <a name="the-tooling-layers"></a>As camadas de ferramentas

Com a mudança no motor de construção e a mudança do sistema de projeto existente, algumas perguntas seguem naturalmente. Alguma dessas alterações altera a "camada" global do ecossistema de ferramentas .NET Core? Existem novos bits e componentes?

Vamos começar recapitulando as camadas na Visualização 2, conforme mostrado na figura a seguir:

![A arquitetura de alto nível das ferramentas da Visualização 2](media/cli-msbuild-architecture/p2-arch.png)

A camada das ferramentas na Pré-Visualização 2 é simples. Na parte inferior, a base é o .NET Core CLI. Todas as outras ferramentas de nível superior, como visual studio ou visual studio code, dependem e dependem da CLI para construir projetos, restaurar dependências e assim por diante. Por exemplo, se o Visual Studio quisesse realizar uma `dotnet restore` operação de restauração, ele ligaria para o comando na CLI.

Com a mudança para o novo sistema de projeto, o diagrama anterior se altera:

![Arquitetura de alto nível do SDK 1.0.0 do .NET Core](media/cli-msbuild-architecture/p3-arch.png)

A principal diferença é que a CLI não é mais a camada básica; agora, essa função é executada pelo "componente SDK compartilhado". Este componente SDK compartilhado é um conjunto de metas e tarefas associadas que são responsáveis por compilar códigos, publicá-lo, embalar pacotes NuGet e assim por diante. O .NET Core SDK é de código aberto e está disponível no GitHub no [repo SDK](https://github.com/dotnet/sdk).

> [!NOTE]
> Um "alvo" é um termo MSBuild que indica uma operação nomeada que o MSBuild pode invocar. Normalmente, ele está acoplado com uma ou mais tarefas que executam alguma lógica que o destino deve realizar. O MSBuild oferece suporte a muitos destinos prontos como `Copy` ou `Execute`; ele também permite aos usuários gravar suas próprias tarefas usando código gerenciado e definir metas para executar essas tarefas. Para mais informações, consulte [Tarefas do MSBuild](/visualstudio/msbuild/msbuild-tasks).

Todos os conjuntos de ferramentas agora consumem o componente SDK compartilhado e seus destinos, incluindo a CLI. Por exemplo, o Visual Studio 2019 `dotnet restore` não chama o comando para restaurar dependências de projetos .NET Core. Em vez disso, ele usa diretamente o alvo "Restaurar". Como esses são os destinos do MSBuild, também é possível usar o MSBuild bruto para executá-los, usando o comando [dotnet msbuild](dotnet-msbuild.md).

### <a name="cli-commands"></a>Comandos de CLI

O componente SDK compartilhado significa que a maioria dos comandos CLI existentes foram reimplementados como tarefas e alvos do MSBuild. O que isso significa para os comandos CLI e o uso do conjunto de ferramentas?

Do ponto de vista do uso, isso não muda a maneira como você usa a CLI. A CLI ainda tem os comandos principais que existiam na versão .NET Core 1.0 Preview 2:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Esses comandos ainda fazem o que você espera que eles façam (novo projeto, construa-o, publique-o, embale-o, e assim por diante). Você pode consultar a tela de `dotnet <command> --help`ajuda do comando (usando) ou a documentação neste site para se familiarizar com seu comportamento.

Do ponto de vista da execução, os comandos cli tomam seus parâmetros e constroem uma chamada para o MSBuild "cru" que define as propriedades necessárias e executa o alvo desejado. Para ilustrar melhor, considere o seguinte comando:

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

Este comando publica `pub` um aplicativo em uma pasta usando a configuração "Liberar". Internamente, esse comando é convertido na seguinte invocação do MSBuild:

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Notáveis exceções a esta `new` `run` regra são os comandos. Eles não foram implementados como alvos do MSBuild.

### <a name="implicit-restore"></a>Restauração implícita

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
