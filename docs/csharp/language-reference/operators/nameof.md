---
title: nomede expressão - C# referência
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507133"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="86a8d-102">nomeda expressão (referência C#)</span><span class="sxs-lookup"><span data-stu-id="86a8d-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="86a8d-103">Uma `nameof` expressão produz o nome de uma variável, tipo ou membro como a constante de seqüência de cordas:</span><span class="sxs-lookup"><span data-stu-id="86a8d-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="86a8d-104">Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="86a8d-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="86a8d-105">Uma `nameof` expressão é avaliada no tempo de compilação e não tem efeito no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="86a8d-105">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="86a8d-106">Você pode `nameof` usar uma expressão para tornar o código de verificação de argumentos mais sustentável:</span><span class="sxs-lookup"><span data-stu-id="86a8d-106">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="86a8d-107">Uma `nameof` expressão está disponível em C # 6 e posterior.</span><span class="sxs-lookup"><span data-stu-id="86a8d-107">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="86a8d-108">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="86a8d-108">C# language specification</span></span>

<span data-ttu-id="86a8d-109">Para saber mais, confira a seção [Expressões nameof](~/_csharplang/spec/expressions.md#nameof-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="86a8d-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86a8d-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="86a8d-110">See also</span></span>

- [<span data-ttu-id="86a8d-111">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="86a8d-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="86a8d-112">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="86a8d-112">C# operators</span></span>](index.md)
