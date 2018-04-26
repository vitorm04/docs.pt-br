---
title: Novidades no C# – Guia do C#
description: Como a linguagem C# está evoluindo
keywords: C#, recursos mais recentes, novidades, Roslyn
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: d66f835d57f43d2016d3b20e2205e0052d064acb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="whats-new-in-c"></a>Novidades no C# #

Esta página fornece um roteiro de novos recursos em cada versão principal da linguagem C#. Os links a seguir fornecem informações detalhadas sobre os principais recursos adicionados a cada versão.

> [!IMPORTANT]
> A linguagem C# depende de tipos e métodos em uma *biblioteca padrão* para alguns dos recursos. Um exemplo é o processamento de exceção. Cada instrução ou expressão `throw` é verificada para garantir que o objeto que está sendo gerado é derivado de <xref:System.Exception>. Da mesma forma, cada `catch` é verificado para garantir que o tipo que está sendo capturado é derivado de <xref:System.Exception>. Cada versão pode adicionar novos requisitos. Para usar os recursos de linguagem mais recentes em ambientes mais antigos, talvez seja necessário instalar bibliotecas específicas. Essas dependências estão documentadas na página de cada versão específica. Saiba mais sobre as [relações entre linguagem e biblioteca](relationships-between-language-and-library.md) para obter informações sobre essa dependência. 


* [C# 7.2](csharp-7-2.md):
    - Esta página descreve os recursos mais recentes na linguagem C#. O C#7.2 está disponível atualmente no [Visual Studio 2017 versão 15.5](https://www.visualstudio.com/vs/whatsnew/) e no [SDK do .NET Core 2.0](../../core/whats-new/index.md).

* [C# 7.1](csharp-7-1.md):
    - Esta página descreve os recursos no C# 7.1. Esses recursos foram adicionados no [Visual Studio 2017 versão 15.3](https://www.visualstudio.com/vs/whatsnew/) e no [SDK do .NET Core 2.0](../../core/whats-new/index.md).

* [C# 7.0](csharp-7.md):
    - Esta página descreve os recursos adicionados ao C# 7.0. Esses recursos foram adicionados ao [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) e ao [.NET Core 1.0](../../core/whats-new/index.md) e posterior
     
* [C# 6](csharp-6.md):
    - Esta página descreve os recursos que foram adicionados no C# 6. Esses recursos estão disponíveis no Visual Studio 2015 para desenvolvedores do Windows e no .NET Core 1.0 para desenvolvedores explorando o C# no macOS e Linux.

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* [Suporte de plataforma cruzada](../../core/index.md):
    - O C#, por meio do suporte do .NET Core, é executado em várias plataformas. Se estiver interessado em testar o C# no macOS ou em uma das várias distribuições do Linux com suporte, saiba mais sobre o .NET Core.

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a>Versões anteriores
A seguir estão listados as principais funcionalidades que foram introduzidas em versões anteriores da linguagem C# e Visual Studio .NET.  
  
 * Visual Studio .NET 2013: 
     - Esta versão do Visual Studio incluiu correções de bug, aprimoramentos de desempenho e visualizações de tecnologia da Plataforma do Compilador .NET ("Roslyn"), que se tornou o SDK de Plataforma do Compilador .NET<!--Link to ../roslyn/index.md-->.

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
