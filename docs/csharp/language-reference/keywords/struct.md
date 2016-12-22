---
title: "struct (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "struct_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave struct [C#]"
  - "estruturas [C#], palavra-chave struct"
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# struct (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um tipo `struct` é um tipo de valor que é geralmente usado para encapsular pequenos grupos de variáveis relacionadas, tais como coordenadas de um retângulo ou as características de um item em um inventário.  O seguinte exemplo mostra uma declaração simples de struct:  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## Comentários  
 Os structs podem conter também [construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constantes](../../../csharp/programming-guide/classes-and-structs/constants.md), [campos](../../../csharp/programming-guide/classes-and-structs/fields.md), [métodos](../../../fsharp/language-reference/members/methods.md), [propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexadores](../../../csharp/programming-guide/indexers/index.md), [operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [eventos](../../../csharp/programming-guide/events/index.md) e [tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md), embora se vários membros desse tipo forem necessários, você deverá considerar tornar o seu tipo uma classe.  
  
 Para obter exemplos, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Os structs podem implantar uma interface, mas não podem herdá\-la de outra struct.  Por esse motivo, os membros de struct não podem ser declarados como `protected`.  
  
 Para obter mais informações, consulte [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## Exemplos  
 Para obter exemplos e mais informações, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## Especificação da Linguagem C\#  
 Para obter exemplos, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)