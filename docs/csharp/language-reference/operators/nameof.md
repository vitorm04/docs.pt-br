---
title: expressão nameof-referência C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: d71acf0cf7d5cdcfa5310455af2120fa1f82d567
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135913"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="e5362-102">expressão nameof (referência C#)</span><span class="sxs-lookup"><span data-stu-id="e5362-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="e5362-103">Uma `nameof` expressão produz o nome de uma variável, tipo ou membro como a constante de cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="e5362-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="e5362-104">Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="e5362-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="e5362-105">No caso de [identificadores textuais](../tokens/verbatim.md), o `@` caractere não é a parte de um nome, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e5362-105">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="e5362-106">Uma `nameof` expressão é avaliada em tempo de compilação e não tem nenhum efeito no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e5362-106">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="e5362-107">Você pode usar uma `nameof` expressão para tornar o código de verificação de argumento mais passível de manutenção:</span><span class="sxs-lookup"><span data-stu-id="e5362-107">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="e5362-108">Uma `nameof` expressão está disponível no C# 6 e posterior.</span><span class="sxs-lookup"><span data-stu-id="e5362-108">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e5362-109">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e5362-109">C# language specification</span></span>

<span data-ttu-id="e5362-110">Para saber mais, confira a seção [Expressões nameof](~/_csharplang/spec/expressions.md#nameof-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e5362-110">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5362-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="e5362-111">See also</span></span>

- [<span data-ttu-id="e5362-112">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="e5362-112">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e5362-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e5362-113">C# operators</span></span>](index.md)
