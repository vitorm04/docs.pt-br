---
title: "Operador ?? (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "??_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador ?? [C#]"
  - "Operador de união [C#]"
  - "Operador AND condicional (&&) [C#]"
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador ?? (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O operador `??` é chamado operador de coalescência nula.  Ele retornará o operando esquerdo se o operando não for nulo; caso contrário, ele retornará o operando direito.  
  
## Comentários  
 Um tipo anulável pode representar um valor de domínio do tipo ou o valor pode ser indefinido \(nesse caso, o valor será nulo\).  Você pode usar a expressividade sintática do operador `??` para retornar um valor apropriado \(o operando direito\) quando o operando esquerdo possuir um tipo anulável cujo valor seja nulo.  Se você tentar atribuir um tipo de valor anulável a um tipo de valor não anulável sem usar o operador `??`, um erro de tempo de compilação será gerado.  Se você usar uma conversão e o tipo de valor anulável estiver atualmente indefinido, uma exceção `InvalidOperationException` será acionada.  
  
 Para obter mais informações, consulte [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md).  
  
 O resultado de um operador ?? não será considerado uma constante mesmo se ambos os seus argumentos forem constantes.  
  
## Exemplo  
 [!CODE [csRefOperators#53](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#53)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores em C\#](../../../csharp/language-reference/operators/index.md)   
 [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)   
 [O que exatamente "levantado" significa? “](http://go.microsoft.com/fwlink/?LinkID=112382)