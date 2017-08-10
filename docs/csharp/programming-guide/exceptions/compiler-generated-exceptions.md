---
title: "Exceções geradas pelo compilador (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d8fbae9272b34dd4d010199470c930c846cd1b74
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Exceções geradas pelo compilador (Guia de Programação em C#)
Algumas exceções são geradas automaticamente pelo CLR (Common Language Runtime) do .NET Framework quando as operações básicas falham. Essas exceções e suas condições de erro são listadas na tabela a seguir.  
  
|Exceção|Descrição|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Uma classe base para exceções que ocorrem durante operações aritméticas, tais como <xref:System.DivideByZeroException> e <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Gerada quando uma matriz não pode armazenar um determinado elemento porque o tipo real do elemento é incompatível com o tipo real da matriz.|  
|<xref:System.DivideByZeroException>|Lançada quando é feita uma tentativa de dividir um valor inteiro por zero.|  
|<xref:System.IndexOutOfRangeException>|Lançada quando é feita uma tentativa de indexar uma matriz quando o índice é menor que zero ou fora dos limites da matriz.|  
|<xref:System.InvalidCastException>|Gerada quando uma conversão explícita de um tipo base para uma interface ou um tipo derivado falha em tempo de execução.|  
|<xref:System.NullReferenceException>|Lançada quando você tenta fazer referência a um objeto cujo valor é [null](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Lançada quando uma tentativa de alocar memória usando o operador [new](../../../csharp/language-reference/keywords/new-operator.md) falha. Isso indica que a memória disponível para o Common Language Runtime está esgotada.|  
|<xref:System.OverflowException>|Lançada quando uma operação aritmética em um contexto `checked` estoura.|  
|<xref:System.StackOverflowException>|Lançada quando a pilha de execução acaba tendo muitas chamadas de método pendentes, normalmente indica uma recursão muito profunda ou infinita.|  
|<xref:System.TypeInitializationException>|Lançada quando um construtor estático lança uma exceção e não há nenhuma cláusula `catch` compatível para capturá-la.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Exceções e tratamento de exceções](../../../csharp/programming-guide/exceptions/index.md)   
 [Tratamento de exceções](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)

