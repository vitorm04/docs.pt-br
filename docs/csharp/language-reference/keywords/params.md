---
title: palavra-chave params para matrizes de parâmetros - referência C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738840"
---
# <a name="params-c-reference"></a><span data-ttu-id="5c825-102">params (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="5c825-102">params (C# Reference)</span></span>

<span data-ttu-id="5c825-103">Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](method-parameters.md) que aceita um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5c825-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="5c825-104">O tipo de parâmetro deve ser uma matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="5c825-104">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="5c825-105">Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.</span><span class="sxs-lookup"><span data-stu-id="5c825-105">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="5c825-106">Se o tipo declarado `params` do parâmetro não for uma matriz unidimensional, ocorrerá o erro de compilador [CS0225.](../../misc/cs0225.md)</span><span class="sxs-lookup"><span data-stu-id="5c825-106">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="5c825-107">Quando você chama um `params` método com um parâmetro, você pode passar em:</span><span class="sxs-lookup"><span data-stu-id="5c825-107">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="5c825-108">Uma lista separada por vírgulas de argumentos do tipo dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="5c825-108">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="5c825-109">Uma matriz de argumentos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="5c825-109">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="5c825-110">Sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="5c825-110">No arguments.</span></span> <span data-ttu-id="5c825-111">Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.</span><span class="sxs-lookup"><span data-stu-id="5c825-111">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="5c825-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c825-112">Example</span></span>

<span data-ttu-id="5c825-113">O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.</span><span class="sxs-lookup"><span data-stu-id="5c825-113">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="5c825-114">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="5c825-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5c825-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c825-115">See also</span></span>

- [<span data-ttu-id="5c825-116">C# Referência</span><span class="sxs-lookup"><span data-stu-id="5c825-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5c825-117">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="5c825-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5c825-118">C# Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5c825-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5c825-119">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="5c825-119">Method Parameters</span></span>](method-parameters.md)
