---
title: "readonly (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "readonly_CSharpKeyword"
  - "readonly"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave readonly [C#]"
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# readonly (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `readonly` palavra\-chave é um modificador que pode ser usado em campos.  Quando uma declaração de campo inclui uma `readonly` modificador, atribuições para os campos introduzidos pela declaração só podem ocorrer como parte da declaração ou em um construtor na mesma classe.  
  
## Exemplo  
 Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, mesmo que ele é atribuído um valor no construtor da classe:  
  
 [!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 Você pode atribuir um valor para um `readonly` campo somente nos seguintes contextos:  
  
-   Quando a variável é inicializada na declaração, por exemplo:  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   Para um campo de instância, nos construtores de instância da classe que contém a declaração de campo ou para um campo estático, no construtor estático da classe que contém a declaração de campo.  Estes também são os contextos somente é válido para passar um `readonly` campo como um  [check\-out](../../../csharp/language-reference/keywords/out.md) ou  [ref](../../../csharp/language-reference/keywords/ref.md) parâmetro.  
  
> [!NOTE]
>  O `readonly` palavra\-chave é diferente do  [const](../../../csharp/language-reference/keywords/const.md) palavra\-chave.  A `const` campo somente pode ser inicializado na declaração do campo.  A `readonly` campo pode ser inicializado na declaração ou em um construtor.  Portanto, `readonly` campos podem ter valores diferentes dependendo do construtor usado.  Além disso, enquanto um `const` campo é uma constante de tempo de compilação, o `readonly` campo pode ser usado para constantes de tempo de execução como no exemplo a seguir:  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## Exemplo  
 [!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 No exemplo anterior, se você usar uma instrução como esta:  
  
 `p2.y = 66;        // Error`  
  
 Você receberá a mensagem de erro do compilador:  
  
 `The left-hand side of an assignment must be an l-value`  
  
 qual é o mesmo erro que você obtém ao tentar atribuir um valor a uma constante.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)