---
title: Novidades no C# – Guia do C#
description: Como a linguagem C# está evoluindo
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 399550178a12ff520dff033f0f1dc4a7cdfb9591
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314666"
---
# <a name="whats-new-in-c"></a>Novidades no C# #

Esta página fornece um roteiro de novos recursos em cada versão principal da linguagem C#. Os links a seguir fornecem informações detalhadas sobre os principais recursos adicionados a cada versão.

> [!IMPORTANT]
> A linguagem C# depende de tipos e métodos em uma *biblioteca padrão* para alguns dos recursos. Um exemplo é o processamento de exceção. Cada instrução ou expressão `throw` é verificada para garantir que o objeto que está sendo gerado é derivado de <xref:System.Exception>. Da mesma forma, cada `catch` é verificado para garantir que o tipo que está sendo capturado é derivado de <xref:System.Exception>. Cada versão pode adicionar novos requisitos. Para usar os recursos de linguagem mais recentes em ambientes mais antigos, talvez seja necessário instalar bibliotecas específicas. Essas dependências estão documentadas na página de cada versão específica. Saiba mais sobre as [relações entre linguagem e biblioteca](relationships-between-language-and-library.md) para obter informações sobre essa dependência. 

Para usar as últimas funcionalidades em uma versão de ponto, você precisa [configurar a versão da linguagem do compilador](../language-reference/configure-language-version.md) e selecionar a versão.

* [C# 7.3](csharp-7-3.md):
  - Esta página descreve os recursos mais recentes na linguagem C#. O C# 7.3 está disponível atualmente no [Visual Studio 2017 versão 15.7](https://visualstudio.microsoft.com/vs/whatsnew/) e no [SDK 2.1.300 do .NET Core 2.1 RC1](../../core/whats-new/index.md).
* [C# 7.2](csharp-7-2.md):
  - Esta página descreve os recursos adicionados na linguagem C#. O C#7.2 está disponível atualmente no [Visual Studio 2017 versão 15.5](https://visualstudio.microsoft.com/vs/whatsnew/) e no [SDK do .NET Core 2.0](../../core/whats-new/index.md).
* [C# 7.1](csharp-7-1.md):
  - Esta página descreve os recursos adicionados em C# 7.1. Esses recursos foram adicionados no [Visual Studio 2017 versão 15.3](https://visualstudio.microsoft.com/vs/whatsnew/) e no [SDK do .NET Core 2.0](../../core/whats-new/index.md).
* [C# 7.0](csharp-7.md):
  - Esta página descreve os recursos adicionados ao C# 7.0. Esses recursos foram adicionados ao [Visual Studio 2017](https://visualstudio.microsoft.com/vs/whatsnew/) e ao [.NET Core 1.0](../../core/whats-new/index.md) e posterior
* [C# 6](csharp-6.md):
  - Esta página descreve os recursos que foram adicionados no C# 6. Esses recursos estão disponíveis no Visual Studio 2015 para desenvolvedores do Windows e no .NET Core 1.0 para desenvolvedores explorando o C# no macOS e Linux.
* [Suporte de plataforma cruzada](../../core/index.md):
  - O C#, por meio do suporte do .NET Core, é executado em várias plataformas. Se estiver interessado em testar o C# no macOS ou em uma das várias distribuições do Linux com suporte, saiba mais sobre o .NET Core.
* [SDK da Plataforma do Compilador .NET](../roslyn-sdk/index.md):
  - O SDK da plataforma do compilador .NET permite que você escreva código que executa a análise estática no código C#. Você pode usar essas APIs para localizar erros em potencial ou práticas inadequadas, sugerir correções e até mesmo implementar essas correções.

## <a name="previous-versions"></a>Versões anteriores

A seguir estão listados as principais funcionalidades que foram introduzidas em versões anteriores da linguagem C# e Visual Studio .NET.

* Visual Studio .NET 2013:
  - Esta versão do Visual Studio incluiu correções de bug, aprimoramentos de desempenho e versões prévias de tecnologia do .NET Compiler Platform ("Roslyn"), que se tornou o [SDK do .NET Compiler Platform](../roslyn-sdk/index.md).
* C# 5, Visual Studio .NET 2012:
  - `Async` / `await`, atributos de [informações do chamador](../programming-guide/concepts/caller-information.md).
* C# 4, Visual Studio .NET 2010:
  - `Dynamic`, [argumentos nomeados](../programming-guide/classes-and-structs/named-and-optional-arguments.md), parâmetros opcionais e [covariância e contravariância](../programming-guide/concepts/covariance-contravariance/index.md) genéricas.
* C# 3, Visual Studio .NET 2008:
  - Inicializadores de objeto e coleção, expressões lambda, métodos de extensão, tipos anônimos, propriedades automáticas, inferência de tipos `var` local e [LINQ (Consulta Integrada à Linguagem)](../programming-guide/concepts/linq/index.md).
* C# 2, Visual Studio .NET 2005:
  - Métodos anônimos, genéricos, tipos anuláveis, iteradores/suspensão, classes `static`, covariância e contravariância para delegados.
* C# 1.1, Visual Studio .NET 2003:
  - Comentários da documentação XML e pragma `#line`.
* C# 1, Visual Studio .NET 2002:
  - A primeira versão do [C#](../csharp.md).
