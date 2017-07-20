---
title: Arquitetura das ferramentas de linha de comando do .NET Core | Microsoft Docs
description: "Saiba mais sobre as camadas de ferramentas do .NET Core e o que foi alterado nas versões recentes."
keywords: .NET Core, MSBuild, arquitetura
author: blackdwarf
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 7fff0f61-ac23-42f0-9661-72a7240a4456
ms.translationtype: Human Translation
ms.sourcegitcommit: b64eb0d8f1778a4834ecce5d2ced71e0741dbff3
ms.openlocfilehash: 10e565af67056dee1ea51e4949f32e1e1de54600
ms.contentlocale: pt-br
ms.lasthandoff: 05/27/2017

---

<a id="high-level-overview-of-changes-in-the-net-core-tools" class="xliff"></a>

# Visão geral de alto nível das alterações nas ferramentas do .NET Core

Este documento descreverá em alto nível as alterações causadas pela mudança de *project.json* para o MSBuild e o sistema de projeto *.csproj*. Ele descreverá a nova maneira pela qual as ferramentas são todas colocadas em camadas e quais peças novas estão disponíveis, bem como seus lugares no quadro geral. Depois de ler este artigo, você deverá ter uma compreensão melhor sobre todas as partes que compõem as ferramentas do .NET Core após a mudança para o MSBuild e o *.csproj*. 

<a id="moving-away-from-projectjson" class="xliff"></a>

## Deixando o project.json
A maior alteração nas ferramentas do .NET Core é certamente a [mudança de project.json para csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) como o sistema de projeto. As últimas versões das ferramentas de linha de comando não dão suporte a arquivos *project.json*. Isso significa que ele não pode ser usado para compilar, executar ou publicar aplicativos e bibliotecas baseados no project.json. Para usar essa versão das ferramentas, é necessário migrar os projetos existentes ou iniciar projetos novos. 

Como parte dessa mudança, o mecanismo de build personalizado desenvolvido para compilar projetos project.json foi substituído por um mecanismo de build maduro e totalmente capaz, chamado [MSBuild](https://github.com/Microsoft/msbuild). O MSBuild é um mecanismo conhecido na comunidade do .NET, pois que tem sido uma tecnologia chave desde a primeira versão da plataforma. Naturalmente, como precisa compilar aplicativos .NET Core, o MSBuild foi movido para o .NET Core e pode ser usado em qualquer plataforma que executa o .NET Core. Uma das principais promessas do .NET Core é uma pilha de desenvolvimento de plataforma cruzada e nós garantimos que essa mudança não quebra essa promessa.

> [!NOTE]
> Se você é iniciante no MSBuild e deseja de saber mais sobre ele, comece lendo o artigo [Conceitos do MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-concepts). 

<a id="the-tooling-layers" class="xliff"></a>

## As camadas de ferramentas
Com a mudança do sistema de projeto existente, bem como com a criação de comutadores de mecanismo, a pergunta que surge naturalmente é: essas mudanças alteram as "camadas" gerais do ecossistema de ferramentas do .NET Core? Existem novos bits e componentes?

Vamos começar recapitulando as camadas na Visualização 2, conforme mostrado na figura a seguir:

![A arquitetura de alto nível das ferramentas da Visualização 2](media/cli-msbuild-architecture/p2-arch.png)

As camadas das ferramentas são bastante simples. Na parte inferior, temos as ferramentas de Linha de Comando do .NET Core como base. Todas as outras ferramentas de alto nível, como o Visual Studio ou o Visual Studio Code, dependem e contam com a CLI para criar projetos, restaurar dependências e assim por diante. Isso significa que, por exemplo, se o Visual Studio quisesse executar uma operação de restauração, ele chamaria o comando `dotnet restore` na CLI. 

Com a mudança para o novo sistema de projeto, o diagrama anterior se altera: 

![Arquitetura de alto nível do SDK 1.0.0 do .NET Core](media/cli-msbuild-architecture/p3-arch.png)

A principal diferença é que a CLI não é mais a camada básica; agora, essa função é executada pelo "componente SDK compartilhado". Esse componente SDK compartilhado é um conjunto de destinos e tarefas associadas responsáveis por compilar o seu código, publicá-lo, empacotar pacotes NuGet etc. O SDK em si é aberto e está disponível no GitHub no [repositório SDK](https://github.com/dotnet/sdk). 

> [!NOTE]
> Um "destino" é um termo do MSBuild que indica uma operação nomeada que o MSBuild pode invocar. Normalmente, ele está acoplado com uma ou mais tarefas que executam alguma lógica que o destino deve realizar. O MSBuild oferece suporte a muitos destinos prontos como `Copy` ou `Execute`; ele também permite aos usuários gravar suas próprias tarefas usando código gerenciado e definir metas para executar essas tarefas. Para mais informações, consulte [Tarefas do MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-tasks). 

Todos os conjuntos de ferramentas agora consumem o componente SDK compartilhado e seus destinos, incluindo a CLI. Por exemplo, a próxima versão do Visual Studio não chamará o comando `dotnet restore` para restaurar dependências para projetos do .NET Core, ela usará o destino de "Restauração" diretamente. Como esses são os destinos do MSBuild, também é possível usar o MSBuild bruto para executá-los, usando o comando [dotnet msbuild](dotnet-msbuild.md). 

<a id="cli-commands" class="xliff"></a>

### Comandos da CLI
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
