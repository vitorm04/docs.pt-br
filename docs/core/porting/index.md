---
title: Portabilidade do .NET Framework para .NET Core
description: Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: bf4f50ca915f21cdda6b99ae6bdf9e837eca3ae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="porting-to-net-core-from-net-framework"></a>Portabilidade do .NET Framework para .NET Core

Se você tiver código em execução no .NET Framework, poderá ser útil executar seu código no .NET Core 1.0.  Esse artigo aborda uma visão geral do processo de portabilidade e uma lista das ferramentas que podem ser úteis na portabilidade para o .NET Core.

## <a name="overview-of-the-porting-process"></a>Visão geral do processo de portabilidade

O processo recomendado de portabilidade segue a série de etapas a seguir.  Cada uma dessas partes do processo é abordada em mais detalhes nos próximos artigos.

1. Identifique e considere as dependências de terceiros.

   Isso inclui compreender quais são suas dependências de terceiros, como você depende delas, como ver se elas também são executadas no .NET Core e as etapas a ser seguidas caso não sejam.
   
2. Redirecione todos os projetos que você deseja portar para o .NET Framework 4.6.2.

   Isso garante que você possa usar alternativas de API para destinos específicos de .NET Framework nos casos em que o .NET Core não dá suporte a uma determinada API.
   
3. Use a [ferramenta Analisador de Portabilidade de API](https://github.com/Microsoft/dotnet-apiport/) para analisar seus assemblies e desenvolver um plano de portabilidade com base em seus resultados.

   A ferramenta Analisador de Portabilidade de API analisará seus assemblies compilados e gerará um relatório que mostra um resumo de portabilidade de alto nível e um detalhamento de cada API usada que não está disponível no .NET Core.  Você pode usar esse relatório junto com uma análise da sua base de código para desenvolver um plano para como você realizará a portabilidade do código.
   
4. Porte seu código de testes.

   Como a portabilidade para o .NET Core é uma grande mudança para sua base de código, é altamente recomendável portar seus testes para poder realizar testes à medida que o código é portado.  MSTest, xUnit e NUnit dão suporte ao .NET Core 1.0 no momento.
   
6. Execute seu plano de portabilidade.

## <a name="tools-to-help"></a>Ferramentas para ajudar

Esta é uma breve lista das ferramentas que serão úteis:

* NuGet – [Cliente Nuget](https://dist.nuget.org/index.html) ou [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), o gerenciador de pacotes da Microsoft para implementações do .NET.
* Analisador de Portabilidade de API – [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases) ou [Extensão do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), uma cadeia de ferramentas que pode gerar um relatório sobre a portabilidade do seu código entre o .NET Framework e .NET Core, com detalhamento dos problemas assembly por assembly.  Consulte [Ferramentas para ajudar no processo](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) para obter mais informações.
* Pesquisa Inversa de Pacotes – Um [serviço Web útil](https://packagesearch.azurewebsites.net) que permite pesquisar por um tipo e localizar os pacotes que contêm esse tipo.

## <a name="next-steps"></a>Próximas etapas

[Analisando dependências de terceiros.](third-party-deps.md)
   
