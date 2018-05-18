---
title: Arquitetura das ferramentas de linha de comando do .NET Core
description: Saiba mais sobre as camadas de ferramentas do .NET Core e o que foi alterado nas versões recentes.
author: blackdwarf
ms.date: 03/06/2017
ms.openlocfilehash: 50ccaa490f079c62901c57eb9cf91690ee655bf2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Visão geral de alto nível das alterações nas ferramentas do .NET Core

Este documento descreve as alterações associadas à movimentação de *project.json* para o MSBuild e para o sistema de projeto *csproj*, com informações sobre as alterações na camada de ferramentas do .NET Core e a implementação dos comandos da CLI. Essas alterações ocorreram com o lançamento do SDK 1.0 do .NET Core e do Visual Studio 2017 em 7 de março de 2017 (veja o [comunicado](https://blogs.msdn.microsoft.com/dotnet/2017/03/07/announcing-net-core-tools-1-0/)), mas foram implementadas inicialmente com o lançamento do SDK Preview 3 do .NET Core.

## <a name="moving-away-from-projectjson"></a>Deixando o project.json
A maior alteração nas ferramentas do .NET Core é certamente a [mudança de project.json para csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) como o sistema de projeto. As últimas versões das ferramentas de linha de comando não dão suporte a arquivos *project.json*. Isso significa que ele não pode ser usado para compilar, executar ou publicar aplicativos e bibliotecas baseados no project.json. Para usar essa versão das ferramentas, é necessário migrar os projetos existentes ou iniciar projetos novos. 

Como parte dessa mudança, o mecanismo de build personalizado desenvolvido para compilar projetos project.json foi substituído por um mecanismo de build maduro e totalmente capaz, chamado [MSBuild](https://github.com/Microsoft/msbuild). O MSBuild é um mecanismo conhecido na comunidade do .NET, pois que tem sido uma tecnologia chave desde a primeira versão da plataforma. Naturalmente, como precisa compilar aplicativos .NET Core, o MSBuild foi movido para o .NET Core e pode ser usado em qualquer plataforma que executa o .NET Core. Uma das principais promessas do .NET Core é uma pilha de desenvolvimento de plataforma cruzada e nós garantimos que essa mudança não quebra essa promessa.

> [!NOTE]
> Se você é iniciante no MSBuild e deseja de saber mais sobre ele, comece lendo o artigo [Conceitos do MSBuild](/visualstudio/msbuild/msbuild-concepts). 

## <a name="the-tooling-layers"></a>As camadas de ferramentas
Com a mudança do sistema de projeto existente, bem como com a criação de comutadores de mecanismo, a pergunta que surge naturalmente é: essas mudanças alteram as "camadas" gerais do ecossistema de ferramentas do .NET Core? Existem novos bits e componentes?

Vamos começar recapitulando as camadas na Visualização 2, conforme mostrado na figura a seguir:

![A arquitetura de alto nível das ferramentas da Visualização 2](media/cli-msbuild-architecture/p2-arch.png)

As camadas das ferramentas são bastante simples. Na parte inferior, temos as ferramentas de Linha de Comando do .NET Core como base. Todas as outras ferramentas de alto nível, como o Visual Studio ou o Visual Studio Code, dependem e contam com a CLI para criar projetos, restaurar dependências e assim por diante. Isso significa que, por exemplo, se o Visual Studio quisesse executar uma operação de restauração, ele chamaria o comando `dotnet restore` ([confira a observação](#dotnet-restore-note)) na CLI. 

Com a mudança para o novo sistema de projeto, o diagrama anterior se altera: 

![Arquitetura de alto nível do SDK 1.0.0 do .NET Core](media/cli-msbuild-architecture/p3-arch.png)

A principal diferença é que a CLI não é mais a camada básica; agora, essa função é executada pelo "componente SDK compartilhado". Esse componente SDK compartilhado é um conjunto de destinos e tarefas associadas responsáveis por compilar o seu código, publicá-lo, empacotar pacotes NuGet etc. O SDK em si é aberto e está disponível no GitHub no [repositório SDK](https://github.com/dotnet/sdk). 

> [!NOTE]
> Um "destino" é um termo do MSBuild que indica uma operação nomeada que o MSBuild pode invocar. Normalmente, ele está acoplado com uma ou mais tarefas que executam alguma lógica que o destino deve realizar. O MSBuild oferece suporte a muitos destinos prontos como `Copy` ou `Execute`; ele também permite aos usuários gravar suas próprias tarefas usando código gerenciado e definir metas para executar essas tarefas. Para mais informações, consulte [Tarefas do MSBuild](/visualstudio/msbuild/msbuild-tasks). 

Todos os conjuntos de ferramentas agora consumem o componente SDK compartilhado e seus destinos, incluindo a CLI. Por exemplo, a próxima versão do Visual Studio não chamará o comando `dotnet restore` ([confira a observação](#dotnet-restore-note)) para restaurar dependências para projetos do .NET Core, ela usará diretamente o destino "Restore". Como esses são os destinos do MSBuild, também é possível usar o MSBuild bruto para executá-los, usando o comando [dotnet msbuild](dotnet-msbuild.md). 

### <a name="cli-commands"></a>Comandos da CLI
O componente SDK compartilhado significa que a maioria dos comandos CLI existentes foram reimplementados como destinos e tarefas do MSBuild. O que isso significa para os comandos CLI e o uso do conjunto de ferramentas? 

De uma perspectiva de uso, ele não altera a maneira de usar a CLI. A CLI ainda tem os comandos principais que existem na versão da Visualização 2:

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

Esses comandos ainda fazem o que você espera que eles façam (criar um projeto, compilá-lo, publicá-lo, empacotá-lo e assim por diante). A maioria das opções não foi alterada e ainda está disponível. Além disso, é possível consultar as telas de ajuda dos comandos (usando `dotnet <command> --help`) ou a documentação neste site para se familiarizar com as alterações. 

De uma perspectiva de execução, os comandos CLI assumirão seus parâmetros e construirão uma chamada para o MSBuild "bruto" que defina as propriedades necessárias e execute o destino desejado. Para ilustrar melhor, considere o seguinte comando: 

   `dotnet publish -o pub -c Release`
    
Esse comando está publicando um aplicativo em uma pasta `pub` usando a configuração de "Versão". Internamente, esse comando é convertido na seguinte invocação do MSBuild: 

   `dotnet msbuild /t:Publish /p:OutputPath=pub /p:Configuration=Release`

A exceção notável a essa regra são os comandos `new` e `run`, pois eles não foram implementados como destinos do MSBuild.

<a name="dotnet-restore-note"></a> [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]