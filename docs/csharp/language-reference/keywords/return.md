---
title: Instrução return (referência em C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 0d20da39d3f56220c4499f699e542bd24ded93ca
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480523"
---
# <a name="return-c-reference"></a><span data-ttu-id="df2da-102">return (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="df2da-102">return (C# Reference)</span></span>

<span data-ttu-id="df2da-103">A instrução `return` finaliza a execução do método em que aparece e retorna o controle para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="df2da-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="df2da-104">Ela também pode retornar um valor opcional.</span><span class="sxs-lookup"><span data-stu-id="df2da-104">It can also return an optional value.</span></span> <span data-ttu-id="df2da-105">Se o método for um tipo `void`, a instrução `return` poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="df2da-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="df2da-106">Se a instrução return estiver dentro de um bloco `try`, o bloco `finally`, se houver, será executado antes que o controle retorne para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="df2da-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="df2da-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df2da-107">Example</span></span>

 <span data-ttu-id="df2da-108">No exemplo a seguir, o método `CalculateArea()` retorna a variável `area` local como um valor [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="df2da-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](double.md) value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="df2da-109">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="df2da-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="df2da-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df2da-110">See also</span></span>

- [<span data-ttu-id="df2da-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="df2da-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="df2da-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="df2da-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="df2da-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="df2da-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="df2da-114">Instrução return</span><span class="sxs-lookup"><span data-stu-id="df2da-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
- [<span data-ttu-id="df2da-115">Instruções de atalho</span><span class="sxs-lookup"><span data-stu-id="df2da-115">Jump Statements</span></span>](jump-statements.md)
