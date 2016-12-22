---
title: "Implementa&#231;&#227;o de interface expl&#237;cita (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "interfaces explícitas [C#]"
  - "interfaces [c#], explícitas"
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Implementa&#231;&#227;o de interface expl&#237;cita (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Se [classe](../../../csharp/language-reference/keywords/class.md) implementa duas interfaces que contém um membro com a mesma assinatura, então implementar o membro na classe fará com que as duas interfaces usa esse membro como sua implementação.  No exemplo, todas as chamadas a `Paint` chamam o mesmo método.  
  
 [!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 Se os dois membros de [interface](../../../csharp/language-reference/keywords/interface.md) não executam a mesma função, o entanto, isso pode levar a uma implementação incorreta de uma ou ambas a interfaces.  É possível implementar um membro de interface que cria um membro da classe que é chamado somente através da interface, e é específico à interface.  Isso é feito nomeando o membro da classe com o nome da interface e um ponto.  Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 O membro da classe `IControl.Paint` só está disponível através da interface de `IControl` , e `ISurface.Paint` é somente `ISurface`direto disponível.  Ambas as implementações do método são separadas, e nenhuma está disponível diretamente na classe.  Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 A implementação explícita também é usada para resolver os casos onde duas interfaces cada declarar membros diferentes do mesmo nome como uma propriedade e um método:  
  
 [!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 Para implementar ambas as interfaces, uma classe tem que usar a implementação explícita para a propriedade, P ou o método, P ou ambos, para evitar um erro do compilador.  Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)