---
title: Palavra-chave params (Referência em C#)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 089e31f3aad12c2303619e2a1998d0d6a5a0ad86
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48844089"
---
# <a name="params-c-reference"></a><span data-ttu-id="f8153-102">params (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f8153-102">params (C# Reference)</span></span>

<span data-ttu-id="f8153-103">Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](method-parameters.md) que aceita um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="f8153-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="f8153-104">Você pode enviar uma lista separada por vírgulas dos argumentos do tipo especificado na declaração de parâmetros ou uma matriz de argumentos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="f8153-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="f8153-105">Você também pode não enviar nenhum argumento.</span><span class="sxs-lookup"><span data-stu-id="f8153-105">You also can send no arguments.</span></span> <span data-ttu-id="f8153-106">Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.</span><span class="sxs-lookup"><span data-stu-id="f8153-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="f8153-107">Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.</span><span class="sxs-lookup"><span data-stu-id="f8153-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="f8153-108">O tipo declarado do parâmetro `params` precisa ser uma matriz unidimensional, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f8153-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="f8153-109">Caso contrário, ocorrerá o erro do compilador [CS0225](../../misc/cs0225.md).</span><span class="sxs-lookup"><span data-stu-id="f8153-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="f8153-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8153-110">Example</span></span>

<span data-ttu-id="f8153-111">O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.</span><span class="sxs-lookup"><span data-stu-id="f8153-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a><span data-ttu-id="f8153-112">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f8153-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f8153-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8153-113">See also</span></span>

- [<span data-ttu-id="f8153-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f8153-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f8153-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f8153-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f8153-116">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f8153-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f8153-117">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="f8153-117">Method Parameters</span></span>](method-parameters.md)