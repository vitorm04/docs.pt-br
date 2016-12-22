---
title: "Como implementar membros de duas interfaces explicitamente (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "herança [C#], implementando explicitamente membros de interface"
  - "interfaces [C#], implementando herança explicitamente com herança"
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como implementar membros de duas interfaces explicitamente (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Explícito  [interface](../../../csharp/language-reference/keywords/interface.md) implementação também permite que o programador implementar duas interfaces que têm os mesmos nomes de membro e fornecer uma implementação separada de cada membro de interface.  Este exemplo exibe as dimensões de uma caixa de métrica e unidades em inglês.  A caixa de  [classe](../../../csharp/language-reference/keywords/class.md) implementa duas interfaces IEnglishDimensions e IMetricDimensions, que representam os sistemas de medida diferente.  Ambas as interfaces têm nomes de membro idênticos, comprimento e largura.  
  
## Exemplo  
 [!code-cs[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## Programação robusta  
 Se você desejar fazer medições padrão em unidades de inglês, implementar os métodos de comprimento e largura normalmente e implementar explicitamente os métodos de comprimento e largura da interface IMetricDimensions:  
  
 [!code-cs[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 Nesse caso, você pode acessar as unidades em inglês da instância da classe e acessar as unidades métricas de instância da interface:  
  
 [!code-cs[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Como implementar membros de interface explicitamente](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)