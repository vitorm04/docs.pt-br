---
title: Portabilidade do .NET Framework para .NET Core
description: Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 10/23/2018
ms.openlocfilehash: 0c0ec3d8ab09e34e8dae24623903ca571f2cca6c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50192766"
---
# <a name="porting-to-net-core-from-net-framework"></a>Portabilidade do .NET Framework para .NET Core

Se você tiver código em execução no .NET Framework, poderá ser útil executá-lo no .NET Core.  Esse artigo aborda uma visão geral do processo de portabilidade e uma lista das ferramentas que podem ser úteis na portabilidade para o .NET Core.

## <a name="overview-of-the-porting-process"></a>Visão geral do processo de portabilidade

O processo recomendado de portabilidade segue a série de etapas a seguir.  Cada uma dessas partes do processo é abordada em mais detalhes nos próximos artigos.

1. Identifique e considere as dependências de terceiros.

   Isso inclui compreender quais são suas dependências de terceiros, como você depende delas, como ver se elas também são executadas no .NET Core e as etapas a ser seguidas caso não sejam.
   
2. Redirecione todos os projetos que você deseja portar para direcionar para a versão mais recente do .NET Framework.

   Isso garante que você possa usar alternativas de API para destinos específicos de .NET Framework nos casos em que o .NET Core não dá suporte a uma determinada API.
   
3. Use o [Analisador de Portabilidade do .NET](../../standard/analyzers/portability-analyzer.md) para analisar seus assemblies e desenvolver um plano de portabilidade com base nos resultados dele.

   A ferramenta Analisador de Portabilidade de API analisará seus assemblies compilados e gerará um relatório que mostra um resumo de portabilidade de alto nível e um detalhamento de cada API usada que não está disponível no .NET Core.  Você pode usar esse relatório junto com uma análise da sua base de código para desenvolver um plano para como você realizará a portabilidade do código.
   
4. Porte seu código de testes.

   Como a portabilidade para o .NET Core é uma grande mudança para sua base de código, é altamente recomendável portar seus testes para poder realizar testes à medida que o código é portado.  No momento, MSTest, xUnit e NUnit são compatíveis com o .NET Core.
   
6. Execute seu plano de portabilidade.

## <a name="tools-to-help"></a>Ferramentas para ajudar

Esta é uma breve lista das ferramentas que serão úteis:

* NuGet – [Cliente Nuget](https://dist.nuget.org/index.html) ou [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), o gerenciador de pacotes da Microsoft para implementações do .NET.
* Analisador de Portabilidade de API – [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases) ou [Extensão do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), uma cadeia de ferramentas que pode gerar um relatório sobre a portabilidade do seu código entre o .NET Framework e .NET Core, com detalhamento dos problemas assembly por assembly.  Consulte [Ferramentas para ajudar no processo](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) para obter mais informações.
* Pesquisa Inversa de Pacotes – Um [serviço Web útil](https://packagesearch.azurewebsites.net) que permite pesquisar por um tipo e localizar os pacotes que contêm esse tipo.

## <a name="next-steps"></a>Próximas etapas

[Analisando dependências de terceiros.](third-party-deps.md)
   
