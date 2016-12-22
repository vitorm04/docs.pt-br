---
title: "sealed (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "sealed"
  - "sealed_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave sealed [C#]"
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# sealed (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando aplicado a uma classe, o `sealed` modificador impede que outras classes de herdar a partir dele.  No exemplo a seguir, a classe `B` herda da classe `A`, mas nenhuma classe pode herdar da classe `B`.  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 Você também pode usar o `sealed` modificador em um método ou propriedade que substitui um método virtual ou propriedade na classe base.  Isso permite que você permita classes derivar de sua classe e impedir que eles substituam as propriedades ou métodos virtuais específicos.  
  
## Exemplo  
 No exemplo a seguir, `Z` herda de `Y` , mas `Z` não pode substituir a função virtual `F` que é declarado em `X` e lacrada em `Y`.  
  
 [!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 Quando você define novos métodos ou propriedades em uma classe, você pode impedir que classes derivados substituam\-los, não declarando\-os como  [virtual](../../../csharp/language-reference/keywords/virtual.md).  
  
 É um erro para usar o  [abstrata](../../../csharp/language-reference/keywords/abstract.md) modificador com uma classe selada, porque uma classe abstrata que deve ser herdada por uma classe que fornece uma implementação das propriedades ou métodos abstratos.  
  
 Quando aplicado a um método ou propriedade, o `sealed` modificador sempre deve ser usado com  [Substituir](../../../csharp/language-reference/keywords/override.md).  
  
 Porque structs implicitamente são seladas, eles não podem ser herdados.  
  
 Para obter mais informações, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Para obter mais exemplos, consulte [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## Exemplo  
 [!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 No exemplo anterior, você pode experimentar herdar da classe sealed usando a instrução a seguir:  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 O resultado é uma mensagem de erro:  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Comentários  
 Para determinar se deve selar uma classe, método ou propriedade, geralmente, considere os dois pontos a seguintes:  
  
-   Os possíveis benefícios que derivar classes pode obter por meio da capacidade de personalizar a sua classe.  
  
-   O potencial de derivar classes poderia modificar suas classes de tal maneira que podem não mais funcionar corretamente ou como esperado.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)