---
title: Palavra-chave set – Referência de C#
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 3020badc8b7873d7feb0b8133d3a181e1c051cbd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243732"
---
# <a name="set-c-reference"></a>set (Referência de C#)

A palavra-chave `set` define um método *acessador* em uma propriedade ou indexador que atribui um valor ao elemento da propriedade ou do elemento. Para obter mais informações e exemplos, consulte [Propriedades](../../programming-guide/classes-and-structs/properties.md), [Propriedades autoimplementadas](../../programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indexadores](../../programming-guide/indexers/index.md).

O exemplo a seguir define um acessador `get` e um acessador `set` para uma propriedade chamada `Seconds`. Ela usa um campo particular chamado `_seconds` para dar suporte ao valor da propriedade.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Geralmente, o acessador `set` consiste em uma única instrução que retorna um valor, como no exemplo anterior. Começando com o C# 7.0, você pode implementar o acessador `set` como um membro apto para expressão. O exemplo a seguir implementa os acessadores `get` e `set` como membros com corpo de expressão.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Para casos simples em que os acessadores `get` e `set` de uma propriedade não realizam nenhuma outra operação, a não ser a configuração ou a recuperação de um valor em um campo de suporte particular, você pode tirar proveito do suporte do compilador do C# para propriedades autoimplementadas. O exemplo a seguir implementa `Hours` como uma propriedade autoimplementada. 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../language-reference/index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Propriedades](../../programming-guide/classes-and-structs/properties.md)