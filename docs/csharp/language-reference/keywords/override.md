---
title: "override (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "override"
  - "override_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave override [C#]"
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# override (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `override` modificador é necessário para estender ou modificar a implementação de um método herdado, propriedade, indexador ou evento abstract ou virtual.  
  
## Exemplo  
 Neste exemplo, o `Square` classe deve fornecer uma implementação substituída do `Area` porque `Area` é herdada da teoria `ShapesClass`:  
  
 [!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 Um `override` método fornece uma nova implementação de um membro que é herdada de uma classe base.  O método que é substituído por um `override` declaração é conhecida como o método base substituído.  O método base substituído deve ter a mesma assinatura que o `override` método.  Para obter informações sobre herança, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Você não pode substituir um método ou virtual não estático.  Método substituído base deve ser `virtual`, `abstract`, ou `override`.  
  
 Um `override` declaração não é possível alterar a acessibilidade da `virtual` método.  Tanto o `override` método e o `virtual` o método deve ter o mesmo  [nível modificador de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Não é possível usar o `new`, `static`, ou `virtual` modificadores para modificar um `override` método.  
  
 Uma declaração de propriedade de substituição deve especificar exatamente o mesmo modificador de acesso, tipo e nome como a propriedade herdada, e a propriedade substituída deve ser `virtual`, `abstract`, ou `override`.  
  
 Para obter mais informações sobre como usar o `override` palavra\-chave, consulte [Controle de versão com as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e  [saber quando usar substituição e novas palavras\-chave](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## Exemplo  
 Este exemplo define uma classe base chamada `Employee`e uma classe derivada chamada `SalesEmployee`.  O `SalesEmployee` classe inclui uma propriedade extra, `salesbonus`e substitui o método `CalculatePay` para levá\-la em consideração.  
  
 [!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)