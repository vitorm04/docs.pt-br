---
title: params (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: d7e0094d0f60aa201ae7229983f3e4b9764d2cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265464"
---
# <a name="params-c-reference"></a><span data-ttu-id="9cce7-102">params (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9cce7-102">params (C# Reference)</span></span>
<span data-ttu-id="9cce7-103">Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](../../../csharp/language-reference/keywords/method-parameters.md) que aceita um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="9cce7-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="9cce7-104">Você pode enviar uma lista separada por vírgulas dos argumentos do tipo especificado na declaração de parâmetros ou uma matriz de argumentos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="9cce7-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="9cce7-105">Você também pode não enviar nenhum argumento.</span><span class="sxs-lookup"><span data-stu-id="9cce7-105">You also can send no arguments.</span></span> <span data-ttu-id="9cce7-106">Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.</span><span class="sxs-lookup"><span data-stu-id="9cce7-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="9cce7-107">Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.</span><span class="sxs-lookup"><span data-stu-id="9cce7-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cce7-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9cce7-108">Example</span></span>  
 <span data-ttu-id="9cce7-109">O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.</span><span class="sxs-lookup"><span data-stu-id="9cce7-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9cce7-110">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9cce7-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9cce7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cce7-111">See Also</span></span>  
 [<span data-ttu-id="9cce7-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9cce7-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9cce7-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9cce7-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9cce7-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="9cce7-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9cce7-115">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="9cce7-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
