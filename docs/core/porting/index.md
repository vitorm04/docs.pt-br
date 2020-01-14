---
title: Porta do .NET Framework para o .NET Core
description: Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937308"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Visão geral da portabilidade do .NET Framework para o .NET Core

Você pode ter um código que atualmente é executado no .NET Framework que você está interessado em portar para o .NET Core. Esse artigo fornece:

* Uma visão geral do processo de portabilidade.
* Uma lista de ferramentas que você pode achar útil quando está portando seu código para o .NET Core.

## <a name="overview-of-the-porting-process"></a>Visão geral do processo de portabilidade

Recomendamos que você use o seguinte processo ao portar seu projeto para o .NET Core:

1. Redirecione todos os projetos que você deseja que a porta direcione .NET Framework 4.7.2 ou superior.

   Essa etapa garante que você possa usar alternativas de API para destinos específicos do .NET Framework quando o .NET Core não oferecer suporte a determinada API.

2. Use o [.net Portability Analyzer](../../standard/analyzers/portability-analyzer.md) para analisar seus assemblies e ver se eles são portáteis para o .NET Core.

   A ferramenta Analisador de portabilidade de API analisa os assemblies compilados e gera um relatório. Este relatório mostra um resumo de portabilidade de alto nível e uma análise de cada API que você está usando e que não está disponível no núcleo da rede.

3. Instale o [.NET API Analyzer](../../standard/analyzers/api-analyzer.md) em seus projetos para identificar as APIs que geram <xref:System.PlatformNotSupportedException> em algumas plataformas e outros problemas de compatibilidade em potencial.

   Essa ferramenta é semelhante ao analisador de portabilidade, mas em vez de analisar se o código pode ser criado no .NET Core, ele analisa se você está usando uma API de uma forma que gerará um <xref:System.PlatformNotSupportedException> em tempo de execução. Embora isso não seja comum se você estiver mudando de .NET Framework 4.7.2 ou superior, é bom verificar. Para obter mais informações sobre APIs que lançam exceções no .NET Core, consulte [APIs que sempre lançam exceções no .NET Core](../compatibility/unsupported-apis.md).

4. Converta todas as suas dependências de `packages.config` para o formato [PackageReference](/nuget/consume-packages/package-references-in-project-files) com a [ferramenta de conversão no Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Esta etapa envolve a conversão de suas dependências do formato herdado `packages.config`. `packages.config` não funciona no .NET Core, portanto, essa conversão será necessária se você tiver dependências de pacote.

5. Crie novos projetos para o .NET Core e copie sobre os arquivos de origem ou tente converter o arquivo de projeto existente com uma ferramenta.

   O .NET Core usa um formato de arquivo de [projeto](../tools/csproj.md) simplificado (e diferente) do que o .NET Framework. Você precisará converter os arquivos de projeto nesse formato para continuar.

6. Portar seu código de teste.

   Como a portabilidade para o .NET Core é uma alteração significativa na base de código, é altamente recomendável portar seus projetos de teste para que você possa executar testes à medida que você portar seu código. MSTest, xUnit e NUnit funcionam no .NET Core.

Além disso, você pode tentar portar soluções menores ou projetos individuais em uma operação para o formato de arquivo de projeto do .NET Core com a ferramenta [dotnet try-Convert](https://github.com/dotnet/try-convert) . Não há garantia de que o `dotnet try-convert` funcione para todos os seus projetos e pode causar alterações sutis no comportamento que você dependou. Use-o como um _ponto de partida_ que automatize as coisas básicas que podem ser automatizadas. Não é uma solução garantida para migrar um projeto.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

>[!div class="nextstepaction"]
>[Analisar dependências](third-party-deps.md)
