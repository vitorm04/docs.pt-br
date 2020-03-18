---
title: Porta de .NET Framework para .NET Core
description: Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937308"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Visão geral da portação do .NET Framework para .NET Core

Você pode ter um código que atualmente é executado no .NET Framework que você está interessado em portar para .NET Core. Esse artigo fornece:

* Uma visão geral do processo de portação.
* Uma lista de ferramentas que você pode achar úteis quando estiver portando seu código para .NET Core.

## <a name="overview-of-the-porting-process"></a>Visão geral do processo de portabilidade

Recomendamos que você use o seguinte processo ao deportar seu projeto para .NET Core:

1. Redirecione todos os projetos que deseja portar para segmentar o .NET Framework 4.7.2 ou superior.

   Essa etapa garante que você possa usar alternativas de API para destinos específicos do .NET Framework quando o .NET Core não oferecer suporte a determinada API.

2. Use o [Analisador de Portabilidade .NET](../../standard/analyzers/portability-analyzer.md) para analisar seus conjuntos e ver se eles são portáteis para .NET Core.

   A ferramenta Analisador de Portabilidade da API analisa seus conjuntos compilados e gera um relatório. Este relatório mostra um resumo de portabilidade de alto nível e uma análise de cada API que você está usando que não está disponível no NET Core.

3. Instale o [analisador de API .NET](../../standard/analyzers/api-analyzer.md) em <xref:System.PlatformNotSupportedException> seus projetos para identificar APIs que jogam em algumas plataformas e alguns outros problemas potenciais de compatibilidade.

   Esta ferramenta é semelhante ao analisador de portabilidade, mas em vez de analisar se o código pode construir no .NET <xref:System.PlatformNotSupportedException> Core, ele analisa se você está usando uma API de uma maneira que irá jogar um tempo de execução. Embora isso não seja comum se você estiver se movendo do .NET Framework 4.7.2 ou superior, é bom verificar. Para obter mais informações sobre APIs que lançam exceções no .NET Core, consulte [APIs que sempre lançam exceções no .NET Core](../compatibility/unsupported-apis.md).

4. Converta todas `packages.config` as suas dependências para o formato [PackageReference](/nuget/consume-packages/package-references-in-project-files) com a [ferramenta de conversão no Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Esta etapa envolve converter suas dependências do formato legado. `packages.config` `packages.config`não funciona no .NET Core, então essa conversão é necessária se você tiver dependências de pacotes.

5. Crie novos projetos para o .NET Core e copie sobre arquivos de origem ou tente converter seu arquivo de projeto existente com uma ferramenta.

   O .NET Core usa um [formato](../tools/csproj.md) de arquivo de projeto simplificado (e diferente) do que o .NET Framework. Você precisará converter seus arquivos de projeto para este formato para continuar.

6. Porto seu código de teste.

   Como a portação do .NET Core é uma mudança tão significativa na sua base de código, é altamente recomendável portar seus projetos de teste para que você possa executar testes à medida que você porta seu código. MSTest, xUnit e NUnit funcionam no .NET Core.

Além disso, você pode tentar portar soluções menores ou projetos individuais em uma operação para o formato de arquivo de projeto .NET Core com a ferramenta [dotnet try-convert.](https://github.com/dotnet/try-convert) `dotnet try-convert`não é garantido trabalhar para todos os seus projetos, e pode causar mudanças sutis no comportamento que você dependia. Use-o como ponto _de partida_ que automatize as coisas básicas que podem ser automatizadas. Não é uma solução garantida para migrar um projeto.

## <a name="next-steps"></a>Próximas etapas

>[!div class="nextstepaction"]
>[Analisar dependências](third-party-deps.md)
