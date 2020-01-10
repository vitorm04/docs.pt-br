---
title: Palavra-chave contextual value – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712891"
---
# <a name="value-c-reference"></a>value (Referência de C#)

A palavra-chave contextual `value` é usada no acessador `set` em declarações de [Propriedade](../../programming-guide/classes-and-structs/properties.md) e [indexador](../../programming-guide/indexers/index.md) . É semelhante a um parâmetro de entrada de um método. A palavra `value` faz referência ao valor que o código do cliente está tentando atribuir à propriedade ou ao indexador. No exemplo a seguir, `MyDerivedClass` tem uma propriedade chamada `Name` que usa o parâmetro `value` para atribuir uma nova cadeia de caracteres ao campo de suporte `name`. Do ponto de vista do código cliente, a operação é gravada como uma atribuição simples.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Para obter mais informações, consulte as [Propriedades](../../programming-guide/classes-and-structs/properties.md) e os artigos do [Indexeres](../../programming-guide/indexers/index.md) .

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Veja também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
