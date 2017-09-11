---
title: "params (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5999911b96d17c710096e74c8f3da65223e778fc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="params-c-reference"></a><span data-ttu-id="59cd3-102">params (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="59cd3-102">params (C# Reference)</span></span>
<span data-ttu-id="59cd3-103">Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](../../../csharp/language-reference/keywords/method-parameters.md) que aceita um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="59cd3-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="59cd3-104">Você pode enviar uma lista separada por vírgulas dos argumentos do tipo especificado na declaração de parâmetros ou uma matriz de argumentos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="59cd3-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="59cd3-105">Você também pode não enviar nenhum argumento.</span><span class="sxs-lookup"><span data-stu-id="59cd3-105">You also can send no arguments.</span></span> <span data-ttu-id="59cd3-106">Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.</span><span class="sxs-lookup"><span data-stu-id="59cd3-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="59cd3-107">Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.</span><span class="sxs-lookup"><span data-stu-id="59cd3-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59cd3-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59cd3-108">Example</span></span>  
 <span data-ttu-id="59cd3-109">O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.</span><span class="sxs-lookup"><span data-stu-id="59cd3-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 <span data-ttu-id="59cd3-110">[!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="59cd3-110">[!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="59cd3-111">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="59cd3-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="59cd3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59cd3-112">See Also</span></span>  
 <span data-ttu-id="59cd3-113">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="59cd3-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="59cd3-114">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="59cd3-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="59cd3-115">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="59cd3-115">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="59cd3-116">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="59cd3-116">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)

