---
title: Visão geral das bibliotecas de tempo de execução
description: Saiba o que está incluído na seção bibliotecas de tempo de execução do Sumário.
author: tdykstra
ms.date: 11/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 64bbc13f8c3df3c0c9a02fee4560c9ee3fcc5d62
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507604"
---
# <a name="runtime-libraries-overview"></a>Visão geral das bibliotecas de tempo de execução

O [tempo de execução do .net](../core/introduction.md#sdk-and-runtimes), que é instalado em um computador para uso por [aplicativos dependentes da estrutura](../core/introduction.md#deployment-models), tem um conjunto padrão extenso de bibliotecas de classes:

* O conjunto principal, incluído no tempo de execução e conhecido como [BCL (bibliotecas de classes base)](glossary.md#bcl).
* O conjunto completo, incluído no tempo de execução e conhecido como bibliotecas de [tempo de execução](glossary.md#runtime) ou [bibliotecas de estruturas](glossary.md#framework).
* Extensões para as bibliotecas de tempo de execução, fornecidas em pacotes NuGet.

Essas bibliotecas fornecem implementações para muitos tipos, algoritmos e funcionalidades de utilitário específicos de aplicativos e gerais.

## <a name="base-class-libraries"></a>Bibliotecas de classes base

A BCL fornece os tipos básicos e a funcionalidade do utilitário e é a base de todas as outras bibliotecas de classes do .NET. Um exemplo é a <xref:System.String?displayProperty=nameWithType> classe, que fornece APIs para trabalhar com cadeias de caracteres.

## <a name="runtime-libraries"></a>Bibliotecas de runtime

Também conhecida como bibliotecas de estruturas, as bibliotecas de tempo de execução se baseiam na BCL para fornecer APIs de utilitário para tarefas comuns. Um exemplo é as [bibliotecas de serialização](serialization/index.md).

## <a name="extensions-to-the-runtime-libraries"></a>Extensões para as bibliotecas de tempo de execução

Algumas das bibliotecas de tempo de execução são fornecidas em pacotes NuGet em vez de internos ao tempo de execução que é instalado para aplicativos dependentes da estrutura. Um exemplo é a [API de log do .net](../core/extensions/logging.md).

## <a name="see-also"></a>Confira também

* [Introdução ao .NET](../core/introduction.md)
* [Instalar o SDK ou tempo de execução do .NET](../core/install/index.yml)
* [Selecione o SDK .NET ou a versão de tempo de execução instalada para usar](../core/versions/selection.md)
* [Publicar aplicativos dependentes da estrutura](../core/deploying/index.md#publish-framework-dependent)
