---
description: Palavra-chave contextual value – Referência de C#
title: Palavra-chave contextual value – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f72e9f097880d9de725a85a0973001baaefd9a9c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141732"
---
# <a name="value-c-reference"></a><span data-ttu-id="3a8b5-103">value (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3a8b5-103">value (C# Reference)</span></span>

<span data-ttu-id="3a8b5-104">A palavra-chave contextual `value` é usada no `set` acessador em declarações de [Propriedade](../../programming-guide/classes-and-structs/properties.md) e [indexador](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="3a8b5-104">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="3a8b5-105">É semelhante a um parâmetro de entrada de um método.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-105">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="3a8b5-106">A palavra `value` faz referência ao valor que o código do cliente está tentando atribuir à propriedade ou ao indexador.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-106">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="3a8b5-107">No exemplo a seguir, `MyDerivedClass` tem uma propriedade chamada `Name` que usa o parâmetro `value` para atribuir uma nova cadeia de caracteres ao campo de suporte `name`.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-107">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="3a8b5-108">Do ponto de vista do código cliente, a operação é gravada como uma atribuição simples.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-108">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="3a8b5-109">Para obter mais informações, consulte as [Propriedades](../../programming-guide/classes-and-structs/properties.md) e os artigos do [Indexeres](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="3a8b5-109">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3a8b5-110">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3a8b5-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3a8b5-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a8b5-111">See also</span></span>

- [<span data-ttu-id="3a8b5-112">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="3a8b5-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3a8b5-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="3a8b5-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3a8b5-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="3a8b5-114">C# Keywords</span></span>](index.md)
