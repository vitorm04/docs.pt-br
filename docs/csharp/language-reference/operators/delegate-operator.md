---
title: operador delegate – referência do C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1fe281776bd75d8fa869065cd24e85f04fec849d
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331825"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="3f743-102">operador delegate (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="3f743-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="3f743-103">O operador `delegate` cria um método anônimo que pode ser convertido em um tipo delegado:</span><span class="sxs-lookup"><span data-stu-id="3f743-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

<span data-ttu-id="3f743-104">Começando com o C# 3, as [expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) fornecem uma maneira mais concisa e expressiva de criar uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="3f743-104">Beginning with C# 3, [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="3f743-105">Use o [operador =>](lambda-operator.md) para construir uma expressão lambda:</span><span class="sxs-lookup"><span data-stu-id="3f743-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>

[!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]

<span data-ttu-id="3f743-106">Você pode omitir a lista de parâmetros quando usa o operador `delegate`.</span><span class="sxs-lookup"><span data-stu-id="3f743-106">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="3f743-107">Se você fizer isso, o método anônimo criado poderá ser convertido em um tipo delegado com qualquer lista de parâmetros, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3f743-107">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="3f743-108">Essa é a única funcionalidade de métodos anônimos que não tem suporte por expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="3f743-108">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="3f743-109">Em todos os outros casos, uma expressão lambda é a forma preferida de gravar código embutido.</span><span class="sxs-lookup"><span data-stu-id="3f743-109">In all other cases, a lambda expression is a preferred way to write inline code.</span></span> <span data-ttu-id="3f743-110">Para saber mais sobre recursos de expressões lambda, por exemplo, que capturam variáveis externas, confira [Expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3f743-110">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="3f743-111">Você também usa a palavra-chave `delegate` para declarar um [tipo delegado](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="3f743-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3f743-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3f743-112">C# language specification</span></span>

<span data-ttu-id="3f743-113">Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3f743-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f743-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f743-114">See also</span></span>

- [<span data-ttu-id="3f743-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3f743-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3f743-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3f743-116">C# operators</span></span>](index.md)
