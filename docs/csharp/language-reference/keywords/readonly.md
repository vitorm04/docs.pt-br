---
title: "readonly (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
dev_langs:
- CSharp
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e915ac4621d2514e1efcaa8bdb4df698e6a66a72
ms.lasthandoff: 03/13/2017

---
# <a name="readonly-c-reference"></a>readonly (Referência de C#)
A palavra-chave `readonly` é um modificador que pode ser usado nos campos. Quando uma declaração de campo incluir um modificador `readonly`, atribuições aos campos introduzidas pela declaração podem ocorrer apenas como parte da declaração ou em um construtor na mesma classe.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, ainda que seja atribuído a ele um valor no construtor da classe:  
  
 [!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:  
  
-   Quando a variável é inicializada na declaração, por exemplo:  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   Para um campo de instância, nos construtores de instância da classe que contém a declaração do campo ou para um campo estático, no construtor estático da classe que contém a declaração do campo. Esses também são os únicos contextos em que é válido passar um campo `readonly` como um parâmetro [out](../../../csharp/language-reference/keywords/out.md) ou [ref](../../../csharp/language-reference/keywords/ref.md).  
  
> [!NOTE]
>  A palavra-chave `readonly` é diferente da palavra-chave [const](../../../csharp/language-reference/keywords/const.md). O campo `const` pode ser inicializado apenas na declaração do campo. Um campo `readonly` pode ser inicializado na declaração ou em um construtor. Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado. Além disso, enquanto um campo `const` é uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como no exemplo a seguir:  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 No exemplo anterior, se você usar uma instrução como esta:  
  
 `p2.y = 66;        // Error`  
  
 você receberá a mensagem de erro do compilador:  
  
 `The left-hand side of an assignment must be an l-value`  
  
 que é o mesmo erro que você recebe quando tenta atribuir um valor a uma constante.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)
