---
title: Estruturas e Destinos
description: "Explica os conceitos de destinos de estrutura ao gravar códigos .NET."
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 09/19/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6ef56a2e-593d-497b-925a-1e25bb6df2e6
translationtype: Human Translation
ms.sourcegitcommit: 38561c2d25c6950d166bf706f4306c867e683b04
ms.openlocfilehash: 82ba6f4abe200dc48158eac1ad3e3609feeda2c9

---

# <a name="frameworks-and-targets"></a>Estruturas e Destinos

O ecossistema do .NET tem um conceito de estruturas. As estruturas de definem a API que você pode usar para uma determinada plataforma de destino. O .NET Framework 4.6 é uma dessas plataformas. Estruturas são usadas no Visual Studio e outros IDEs e editores para fornecer a você o conjunto correto de APIs. Elas também são usadas pelo NuGet para produção e consumo de pacotes do NuGet, para garantir que você produza e use pacotes apropriados (e ativos subjacentes) para sua estrutura de destino. É possível pensar em estruturas como uma das principais moedas no ecossistema do .NET. O conceito está presente para exatidão, para ajudar você e seus clientes evitarem verem @System.MissingMethodException e similares durante o tempo de execução.

## <a name="framework-versions"></a>Versões do Framework

A tabela a seguir define o conjunto de estruturas que podem ser usadas, como elas são chamadas e qual versão da [Biblioteca Padrão do .NET](library.md) elas implementam.

| Framework | Última Versão | TFM (Moniker de Estrutura de Destino) | TFM (Moniker de Estrutura de Destino) Compacto | Versão do .NET Standard | Metapacote |
|:--------: | :--: | :--: | :--: | :--: | :--: | :--: |
| .NET Standard | 1.6 | .NETStandard,Version=1.6 | netstandard1.6 | N/D | [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library)|
| .NET Core Application | 1.0.1 | .NETCoreApp,Version=1.0 | netcoreapp1.0 | 1.6 | [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App)|
| .NET Framework | 4.6.2 | .NETFramework,Version=4.6.2 | net462 | 1.5 | N/A |

> [!NOTE]
> Estas versões do Framework são as versões estáveis mais recentes. Pode haver também versões de pré-lançamento que não são descritas por essa tabela.

## <a name="writing-about-frameworks"></a>Escrevendo sobre estruturas

Há várias maneiras para fazer referência a estruturas na forma escrita, a maioria das quais são usadas nesta documentação. Elas são descritas abaixo, tanto como uma legenda para interpretar a documentação quanto como um guia para o uso em outros documentos.

Usando o .NET Framework 4.6.1 como exemplo, os formatos a seguir podem ser usados:

**Referindo-se a um produto**

Você pode se referir a um tempo de execução ou plataforma .NET.

- ".NET Framework 4.6.1"

**Referindo-se a uma Estrutura**

Você pode se referir a uma estrutura ou ao direcionamento de uma estrutura usando formas longas ou curtas do TFM. Ambas são igualmente válidas nos casos em geral.

- `.NETFramework,Version=4.6.1`
- `net461`

**Referindo-se a uma família de Estruturas**

Você pode se referir a uma família estruturas usando formas longas ou curtas da ID da estrutura. Ambas são igualmente válidas nos casos em geral.

- `.NETFramework`
- `net`



<!--HONumber=Nov16_HO4-->


