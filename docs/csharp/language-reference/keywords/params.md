---
description: palavra-chave params para matrizes de parâmetros-referência C#
title: palavra-chave params para matrizes de parâmetros-referência C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134460"
---
# <a name="params-c-reference"></a><span data-ttu-id="4e108-103">params (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4e108-103">params (C# Reference)</span></span>

<span data-ttu-id="4e108-104">Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](method-parameters.md) que aceita um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="4e108-104">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="4e108-105">O tipo de parâmetro deve ser uma matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="4e108-105">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="4e108-106">Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.</span><span class="sxs-lookup"><span data-stu-id="4e108-106">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="4e108-107">Se o tipo declarado do `params` parâmetro não for uma matriz unidimensional, ocorrerá um erro [CS0225](../../misc/cs0225.md) do compilador.</span><span class="sxs-lookup"><span data-stu-id="4e108-107">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="4e108-108">Ao chamar um método com um `params` parâmetro, você pode passar:</span><span class="sxs-lookup"><span data-stu-id="4e108-108">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="4e108-109">Uma lista separada por vírgulas de argumentos do tipo dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="4e108-109">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="4e108-110">Uma matriz de argumentos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="4e108-110">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="4e108-111">Sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="4e108-111">No arguments.</span></span> <span data-ttu-id="4e108-112">Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.</span><span class="sxs-lookup"><span data-stu-id="4e108-112">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="4e108-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e108-113">Example</span></span>

<span data-ttu-id="4e108-114">O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.</span><span class="sxs-lookup"><span data-stu-id="4e108-114">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="4e108-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4e108-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4e108-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="4e108-116">See also</span></span>

- [<span data-ttu-id="4e108-117">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="4e108-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e108-118">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="4e108-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e108-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="4e108-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4e108-120">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="4e108-120">Method Parameters</span></span>](method-parameters.md)
