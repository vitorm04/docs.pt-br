---
title: operador nameof – referência do C#
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: a734cae8fbb944774a4bd1bda9194a548b3d82bc
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239216"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="a9202-102">operador nameof (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="a9202-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="a9202-103">O operador `nameof` obtém o nome de uma variável, tipo ou membro como uma cadeia de caracteres constante:</span><span class="sxs-lookup"><span data-stu-id="a9202-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/snippets/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="a9202-104">Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="a9202-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="a9202-105">O operador de `nameof` é avaliado em tempo de compilação e não tem nenhum efeito no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a9202-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="a9202-106">Você pode usar o operador `nameof` para tornar o código de verificação de argumentos mais passível de manutenção:</span><span class="sxs-lookup"><span data-stu-id="a9202-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/snippets/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="a9202-107">O operador `nameof` está disponível no C# 6 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="a9202-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a9202-108">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a9202-108">C# language specification</span></span>

<span data-ttu-id="a9202-109">Para saber mais, confira a seção [Expressões nameof](~/_csharplang/spec/expressions.md#nameof-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a9202-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9202-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="a9202-110">See also</span></span>

- [<span data-ttu-id="a9202-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a9202-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a9202-112">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="a9202-112">C# operators</span></span>](index.md)
