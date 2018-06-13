---
title: goto (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 2dd70a30b885dcdae9637b02e8c34ac39f4879fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216798"
---
# <a name="goto-c-reference"></a><span data-ttu-id="524f8-102">goto (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="524f8-102">goto (C# Reference)</span></span>
<span data-ttu-id="524f8-103">A declaração `goto` transfere o controle do programa diretamente para uma instrução rotulada.</span><span class="sxs-lookup"><span data-stu-id="524f8-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="524f8-104">Um uso comum de `goto` é a transferência do controle para um rótulo de caso de opção específico ou para o rótulo padrão em uma instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="524f8-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="524f8-105">A instrução `goto` também é útil para sair de loops profundamente aninhados.</span><span class="sxs-lookup"><span data-stu-id="524f8-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="524f8-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="524f8-106">Example</span></span>  
 <span data-ttu-id="524f8-107">O exemplo a seguir demonstra o uso de `goto` em uma instrução [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="524f8-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="524f8-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="524f8-108">Example</span></span>  
 <span data-ttu-id="524f8-109">O exemplo a seguir demonstra o uso de `goto` para sair de loops aninhados.</span><span class="sxs-lookup"><span data-stu-id="524f8-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="524f8-110">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="524f8-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="524f8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="524f8-111">See Also</span></span>  
 [<span data-ttu-id="524f8-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="524f8-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="524f8-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="524f8-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="524f8-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="524f8-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="524f8-115">Instrução goto</span><span class="sxs-lookup"><span data-stu-id="524f8-115">goto Statement</span></span>](/cpp/cpp/goto-statement-cpp)  
 [<span data-ttu-id="524f8-116">Instruções de atalho</span><span class="sxs-lookup"><span data-stu-id="524f8-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
