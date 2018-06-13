---
title: return (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266104"
---
# <a name="return-c-reference"></a><span data-ttu-id="4896c-102">return (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4896c-102">return (C# Reference)</span></span>
<span data-ttu-id="4896c-103">A instrução `return` finaliza a execução do método em que aparece e retorna o controle para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="4896c-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="4896c-104">Ela também pode retornar um valor opcional.</span><span class="sxs-lookup"><span data-stu-id="4896c-104">It can also return an optional value.</span></span> <span data-ttu-id="4896c-105">Se o método for um tipo `void`, a instrução `return` poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="4896c-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="4896c-106">Se a instrução return estiver dentro de um bloco `try`, o bloco `finally`, se houver, será executado antes que o controle retorne para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="4896c-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4896c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4896c-107">Example</span></span>  
 <span data-ttu-id="4896c-108">No exemplo a seguir, o método `CalculateArea()` retorna a variável `area` local como um valor [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="4896c-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4896c-109">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4896c-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4896c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4896c-110">See Also</span></span>  
 [<span data-ttu-id="4896c-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4896c-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4896c-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4896c-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4896c-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="4896c-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4896c-114">Instrução return</span><span class="sxs-lookup"><span data-stu-id="4896c-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
 [<span data-ttu-id="4896c-115">Instruções de atalho</span><span class="sxs-lookup"><span data-stu-id="4896c-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
