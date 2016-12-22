---
title: "Exce&#231;&#245;es geradas pelo compilador (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "exceções [C#], geradas pelo compilador"
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Exce&#231;&#245;es geradas pelo compilador (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Algumas exceções são lançadas automaticamente pelo.NET Framework common language runtime \(CLR\) quando há falhas operações básicas.  Essas exceções e suas condições de erro estão listadas na tabela a seguir.  
  
|Exceção|Descrição|  
|-------------|---------------|  
|<xref:System.ArithmeticException>|Uma classe base para exceções que ocorrem durante operações aritméticas, como <xref:System.DivideByZeroException> e <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Lançada quando uma matriz não pode armazenar um determinado elemento porque o tipo real do elemento é incompatível com o tipo real da matriz.|  
|<xref:System.DivideByZeroException>|Lançada quando é feita uma tentativa para dividir um valor inteiro por zero.|  
|<xref:System.IndexOutOfRangeException>|Lançada quando é feita uma tentativa para indexar uma matriz, quando o índice é menor que zero ou fora dos limites da matriz.|  
|<xref:System.InvalidCastException>|Lançada quando uma conversão explícita de um tipo base para uma interface ou um tipo derivado falha em tempo de execução.|  
|<xref:System.NullReferenceException>|Acionada quando você tenta fazer referência a um objeto cujo valor é  [Nulo](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Lançada quando uma tentativa de alocar a memória usando o  [nova](../../../visual-basic/language-reference/operators/new-operator.md) operador falhar.  Isso indica que a memória disponível para o common language runtime foi esgotada.|  
|<xref:System.OverflowException>|Lançada quando uma operação aritmética em um `checked` estouros de contexto.|  
|<xref:System.StackOverflowException>|Lançada quando a pilha de execução seja esgotada por ter muitas chamadas de método pendente; geralmente indica uma recursão muito profunda ou infinita.|  
|<xref:System.TypeInitializationException>|Lançada quando um construtor estático lança uma exceção e não compatível com o `catch` existe uma cláusula para alcançá\-la.|  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [Manipulação de exceções](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)