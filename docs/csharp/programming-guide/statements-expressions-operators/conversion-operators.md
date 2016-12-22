---
title: "Operadores de convers&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem c#, os operadores de conversão"
  - "operadores de conversão [C#]"
  - "operadores [c#], conversão"
  - "conversões definidas pelo usuário [C#]"
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operadores de convers&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Permite que desenvolvedores C\# para declarar conversões para classes ou estruturas de modo que os classes ou estruturas podem ser convertidos e\/ou de outras classes ou estruturas, ou tipos básicos.  Conversões são definidas como operadores e chamadas para o tipo que se eles convertem.  O tipo de argumento a ser convertido, ou o tipo do resultado da conversão, mas não ambos, deve ser do tipo recipiente.  
  
 [!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## Visão geral dos operadores de conversão  
 Operadores de conversão têm as seguintes propriedades:  
  
-   Conversões declaradas como `implicit` ocorrem automaticamente quando for necessário.  
  
-   Conversões declaradas como `explicit` requer uma conversão ser chamado.  
  
-   Todas as conversões devem ser declaradas como `static`.  
  
## Seções relacionadas  
 Para mais informações:  
  
-   [Usando operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Como implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## Consulte também  
 <xref:System.Convert>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Conversões explícitas definidos pelo usuário encadeadas em C\#](http://go.microsoft.com/fwlink/?LinkId=112384)