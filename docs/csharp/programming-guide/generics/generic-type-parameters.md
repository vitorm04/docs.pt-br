---
title: "Par&#226;metros de tipo gen&#233;rico (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "genéricos [C#], parâmetros de tipo"
  - "parâmetros de tipo [C#]"
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Par&#226;metros de tipo gen&#233;rico (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em um tipo genérico ou definição de método, os tipos de parâmetros é um espaço reservado para um tipo específico de que um cliente Especifica quando eles instanciar uma variável do tipo genérico.  Classe de um genérico, como `GenericList<T>` listados na [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md), não pode ser usado como\-é porque ele não é realmente um tipo; é mais semelhante a uma cópia de um tipo.  Para usar `GenericList<T>`, código do cliente deve declarar e criar uma instância de um tipo construído, especificando um argumento de tipo dentro dos colchetes angulares.  O argumento de tipo para esta classe em particular pode ser qualquer tipo reconhecido pelo compilador.  Qualquer número de instâncias do tipo construído pode ser criado, cada um usando um argumento de tipo diferente, como segue:  
  
 [!code-cs[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 Em cada uma dessas instâncias de `GenericList<T>`, cada ocorrência de `T` na classe será substituída em tempo de execução com o argumento de tipo.  Por meio dessa substituição, criamos três tipo seguro e eficientes objetos separados usando uma única definição de classe.  Para obter mais informações sobre como essa substituição é executada pelo CLR, consulte [Genéricos em tempo de execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## Diretrizes de nomeação de parâmetro de tipo  
  
-   **Fazer** nomear os parâmetros de tipo genérico com nomes descritivos, a menos que o nome de um única letra é totalmente auto\-explicativo e um nome descritivo não adicionaria valor.  
  
     [!code-cs[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **Considere a possibilidade de** usando t como o nome do parâmetro de tipo para tipos com um parâmetro de tipo de letra único.  
  
     [!code-cs[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **Fazer** nomes de parâmetro de tipo descritivo com "T" de prefixo.  
  
     [!code-cs[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **Considere a possibilidade de** indicando restrições colocadas em um parâmetro de tipo, o nome do parâmetro.  Por exemplo, um parâmetro é restrita a `ISession` pode ser chamado de `TSession`.  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Diferenças entre modelos C\+\+ e genéricos C\#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)