---
description: operador delegate – referência do C#
title: operador delegate – referência do C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1dfaaf40c0f5a19534adef3be7e3c917bc95c4a8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122245"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="b5daa-103">operador delegate (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="b5daa-103">delegate operator (C# reference)</span></span>

<span data-ttu-id="b5daa-104">O operador `delegate` cria um método anônimo que pode ser convertido em um tipo delegado:</span><span class="sxs-lookup"><span data-stu-id="b5daa-104">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="b5daa-105">Começando com o C# 3, as expressões lambda fornecem uma maneira mais concisa e expressiva de criar uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="b5daa-105">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="b5daa-106">Use o [operador =>](lambda-operator.md) para construir uma expressão lambda:</span><span class="sxs-lookup"><span data-stu-id="b5daa-106">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="b5daa-107">Para saber mais sobre recursos de expressões lambda, por exemplo, que capturam variáveis externas, confira [Expressões lambda](lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b5daa-107">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](lambda-expressions.md).</span></span>

<span data-ttu-id="b5daa-108">Você pode omitir a lista de parâmetros quando usa o operador `delegate`.</span><span class="sxs-lookup"><span data-stu-id="b5daa-108">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="b5daa-109">Se você fizer isso, o método anônimo criado poderá ser convertido em um tipo delegado com qualquer lista de parâmetros, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b5daa-109">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="b5daa-110">Essa é a única funcionalidade de métodos anônimos que não tem suporte por expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="b5daa-110">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="b5daa-111">Em todos os outros casos, uma expressão lambda é a forma preferida de gravar código embutido.</span><span class="sxs-lookup"><span data-stu-id="b5daa-111">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="b5daa-112">Você também usa a palavra-chave `delegate` para declarar um [tipo delegado](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="b5daa-112">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b5daa-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b5daa-113">C# language specification</span></span>

<span data-ttu-id="b5daa-114">Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b5daa-114">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5daa-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5daa-115">See also</span></span>

- [<span data-ttu-id="b5daa-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b5daa-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b5daa-117">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="b5daa-117">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="b5daa-118">= Operador de></span><span class="sxs-lookup"><span data-stu-id="b5daa-118">=> operator</span></span>](lambda-operator.md)
