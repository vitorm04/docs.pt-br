---
title: expressão nameof-referência C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 1bd8800a553eb9b3363da8a3b5f230caecddf223
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556404"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="27447-102">expressão nameof (referência C#)</span><span class="sxs-lookup"><span data-stu-id="27447-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="27447-103">Uma `nameof` expressão produz o nome de uma variável, tipo ou membro como a constante de cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="27447-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="27447-104">Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="27447-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="27447-105">No caso de [identificadores textuais](../tokens/verbatim.md), o `@` caractere não é a parte de um nome, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="27447-105">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="27447-106">Uma `nameof` expressão é avaliada em tempo de compilação e não tem nenhum efeito no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="27447-106">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="27447-107">Você pode usar uma `nameof` expressão para tornar o código de verificação de argumento mais passível de manutenção:</span><span class="sxs-lookup"><span data-stu-id="27447-107">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="27447-108">Uma `nameof` expressão está disponível no C# 6 e posterior.</span><span class="sxs-lookup"><span data-stu-id="27447-108">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="27447-109">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="27447-109">C# language specification</span></span>

<span data-ttu-id="27447-110">Para saber mais, confira a seção [Expressões nameof](~/_csharplang/spec/expressions.md#nameof-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="27447-110">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="27447-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="27447-111">See also</span></span>

- [<span data-ttu-id="27447-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="27447-112">C# reference</span></span>](../index.md)
- [<span data-ttu-id="27447-113">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="27447-113">C# operators and expressions</span></span>](index.md)
