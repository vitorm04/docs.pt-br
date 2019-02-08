---
title: Portabilidade de código do .NET Framework para o .NET Core
description: Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 870320c8467237e87a2675ec5cfb57647026d8ec
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903564"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>Faça a portabilidade do seu código do .NET Framework para o .NET Core

Se você tiver código em execução no .NET Framework, poderá ser útil executá-lo no .NET Core também. Tenha aqui uma visão geral do processo de portabilidade e uma lista das ferramentas que podem ser úteis na portabilidade do seu código para o .NET Core.

## <a name="overview-of-the-porting-process"></a>Visão geral do processo de portabilidade

Este é o processo que recomendamos que você realize ao fazer a portabilidade do seu projeto para o .NET Core. Cada etapa do processo é abordada em mais detalhes nos próximos artigos.

1. Identifique e considere as dependências de terceiros.

   Essa etapa inclui compreender quais são suas dependências de terceiros, como você depende delas, como verificar se elas também são executadas no .NET Core e as etapas a ser seguidas caso não sejam. Ela também aborda como migrar suas dependências para o formato [PackageReference](/nuget/consume-packages/package-references-in-project-files) que é usado no .NET Core.

2. Redirecione todos os projetos que você deseja portar para o .NET Framework 4.7.2 ou posterior.

   Essa etapa garante que você possa usar alternativas de API para destinos específicos do .NET Framework quando o .NET Core não oferecer suporte a determinada API.

3. Use o [Analisador de Portabilidade do .NET](../../standard/analyzers/portability-analyzer.md) para analisar seus assemblies e desenvolver um plano de portabilidade com base nos resultados dele.

   A ferramenta Analisador de Portabilidade de API analisa seus assemblies compilados e gera um relatório que mostra um resumo de portabilidade de alto nível e um detalhamento de cada API usada que não está disponível no .NET Core. Você pode usar esse relatório junto com uma análise da sua base de código para desenvolver um plano para como você realizará a portabilidade do código.

4. Porte seu código de testes.

   Como a portabilidade para o .NET Core é uma mudança significativa para sua base de código, é altamente recomendável portar seus testes para poder realizar testes à medida que o código é portado. MSTest, xUnit e NUnit são compatíveis com o .NET Core.

5. Execute seu plano de portabilidade.

A lista a seguir mostra as ferramentas que podem ser úteis para usar durante o processo de portabilidade:

* Analisador de Portabilidade do .NET – [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases) ou [Extensão do Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), uma cadeia de ferramentas que pode gerar um relatório sobre a portabilidade do seu código entre o .NET Framework e .NET Core, com detalhamento dos problemas assembly por assembly. Para obter mais informações, consulte [Analisador de Portabilidade do .NET](../../standard/analyzers/portability-analyzer.md).
* Analisador de API do .NET – é um analisador Roslyn que descobre riscos potenciais de compatibilidade para APIs do C# em diferentes plataformas e detecta chamadas a APIs preteridas. Para obter mais informações, confira [Analisador de API do .NET](../../standard/analyzers/api-analyzer.md).
* Pesquisa Inversa de Pacotes – Um [serviço Web útil](https://packagesearch.azurewebsites.net) que permite pesquisar por um tipo e localizar os pacotes que contêm esse tipo.

Além disso, você pode tentar fazer a portabilidade de soluções menores ou projetos individuais para o formato de arquivo de projeto do .NET Core com a ferramenta [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017).

> [!WARNING] 
> CsprojToVs2017 é uma ferramenta de terceiros. Não há nenhuma garantia de que ela funcionará para todos os seus projetos, e isso pode causar alterações sutis no comportamento que dependem de você. CsprojToVs2017 deve ser usada como um _ponto de partida_ que automatize as funções básicas que podem ser automatizadas. Não é uma solução garantida para a migração de formatos de arquivo de projeto.

>[!div class="step-by-step"]
>[Avançar](net-framework-tech-unavailable.md)
