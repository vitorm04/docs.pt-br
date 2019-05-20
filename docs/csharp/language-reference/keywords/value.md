---
title: Palavra-chave contextual value – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: cfd370df771998057fd421a0917b3e2fcd96d9f8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633032"
---
# <a name="value-c-reference"></a><span data-ttu-id="47c35-102">value (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="47c35-102">value (C# Reference)</span></span>

<span data-ttu-id="47c35-103">A palavra-chave contextual `value` é usada no acessador definido em declarações de propriedade comuns.</span><span class="sxs-lookup"><span data-stu-id="47c35-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="47c35-104">Ela é semelhante a um parâmetro de entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="47c35-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="47c35-105">A palavra `value` referencia o valor que o código cliente está tentando atribuir à propriedade.</span><span class="sxs-lookup"><span data-stu-id="47c35-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="47c35-106">No exemplo a seguir, `MyDerivedClass` tem uma propriedade chamada `Name` que usa o parâmetro `value` para atribuir uma nova cadeia de caracteres ao campo de suporte `name`.</span><span class="sxs-lookup"><span data-stu-id="47c35-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="47c35-107">Do ponto de vista do código cliente, a operação é gravada como uma atribuição simples.</span><span class="sxs-lookup"><span data-stu-id="47c35-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="47c35-108">Para obter mais informações sobre o uso de `value`, consulte [Propriedades](../../programming-guide/classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="47c35-108">For more information about the use of `value`, see [Properties](../../programming-guide/classes-and-structs/properties.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="47c35-109">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="47c35-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="47c35-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47c35-110">See also</span></span>

- [<span data-ttu-id="47c35-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="47c35-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47c35-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="47c35-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47c35-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="47c35-113">C# Keywords</span></span>](index.md)
