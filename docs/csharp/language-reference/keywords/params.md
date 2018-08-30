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
ms.openlocfilehash: 692c2f61ae99f1c1c8e04a5a1bcad08814d286fe
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752067"
---
# <a name="params-c-reference"></a><span data-ttu-id="0d755-102">params (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0d755-102">params (C# Reference)</span></span>
<span data-ttu-id="0d755-103">Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](../../../csharp/language-reference/keywords/method-parameters.md) que aceita um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="0d755-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="0d755-104">Você pode enviar uma lista separada por vírgulas dos argumentos do tipo especificado na declaração de parâmetros ou uma matriz de argumentos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="0d755-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="0d755-105">Você também pode não enviar nenhum argumento.</span><span class="sxs-lookup"><span data-stu-id="0d755-105">You also can send no arguments.</span></span> <span data-ttu-id="0d755-106">Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.</span><span class="sxs-lookup"><span data-stu-id="0d755-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="0d755-107">Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.</span><span class="sxs-lookup"><span data-stu-id="0d755-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
 
 <span data-ttu-id="0d755-108">O tipo declarado do parâmetro `params` precisa ser uma matriz unidimensional, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0d755-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="0d755-109">Caso contrário, ocorrerá o erro do compilador [CS0225](../../../csharp/misc/cs0225.md).</span><span class="sxs-lookup"><span data-stu-id="0d755-109">Otherwise, a compiler error [CS0225](../../../csharp/misc/cs0225.md) occurs.</span></span>
  
## <a name="example"></a><span data-ttu-id="0d755-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d755-110">Example</span></span>  
 <span data-ttu-id="0d755-111">O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.</span><span class="sxs-lookup"><span data-stu-id="0d755-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0d755-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0d755-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d755-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d755-113">See Also</span></span>  
 [<span data-ttu-id="0d755-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0d755-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0d755-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0d755-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0d755-116">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="0d755-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0d755-117">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="0d755-117">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
