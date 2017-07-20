---
title: "set (Referência de C#) | Microsoft Docs"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: 14
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7111483ac2c939830560e8aad61078da5190684a
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="set-c-reference"></a>set (Referência de C#)
A palavra-chave `set` define um método *acessador* em uma propriedade ou indexador que atribui um valor ao elemento da propriedade ou do elemento. Para obter mais informações e exemplos, consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indexadores](../../../csharp/programming-guide/indexers/index.md).  
  
O exemplo a seguir define um acessador `get` e um acessador `set` para uma propriedade chamada `Seconds`. Ela usa um campo particular chamado `_seconds` para dar suporte ao valor da propriedade.  
 
 [!code-cs[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

Frequentemente, o acessador `set` consiste em uma única instrução que retorna um valor, como no exemplo anterior. Começando com o C# 7, você pode implementar o acessador `set` como um membro com corpo de expressão. O exemplo a seguir implementa os acessadores `get` e `set` como membros com corpo de expressão.

 [!code-cs[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
Para casos simples em que os acessadores `get` e `set` de uma propriedade não realizam nenhuma outra operação além da configuração ou da recuperação de um valor em um campo de suporte particular, você pode tirar proveito do suporte do compilador do C# para propriedades autoimplementadas. O exemplo a seguir implementa `Hours` como uma propriedade autoimplementada. 
  
 [!code-cs[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)
