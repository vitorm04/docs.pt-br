---
title: Instrução return – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713125"
---
# <a name="return-c-reference"></a><span data-ttu-id="e8d9a-102">return (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e8d9a-102">return (C# Reference)</span></span>

<span data-ttu-id="e8d9a-103">A instrução `return` finaliza a execução do método em que aparece e retorna o controle para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="e8d9a-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="e8d9a-104">Ela também pode retornar um valor opcional.</span><span class="sxs-lookup"><span data-stu-id="e8d9a-104">It can also return an optional value.</span></span> <span data-ttu-id="e8d9a-105">Se o método for um tipo `void`, a instrução `return` poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="e8d9a-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="e8d9a-106">Se a instrução return estiver dentro de um bloco `try`, o bloco `finally`, se houver, será executado antes que o controle retorne para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="e8d9a-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="e8d9a-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8d9a-107">Example</span></span>

 <span data-ttu-id="e8d9a-108">No exemplo a seguir, o método `CalculateArea()` retorna a variável local `area` como um valor `double`.</span><span class="sxs-lookup"><span data-stu-id="e8d9a-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="e8d9a-109">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e8d9a-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e8d9a-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8d9a-110">See also</span></span>

- [<span data-ttu-id="e8d9a-111">C# Referência</span><span class="sxs-lookup"><span data-stu-id="e8d9a-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e8d9a-112">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="e8d9a-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e8d9a-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e8d9a-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e8d9a-114">declaração de retorno</span><span class="sxs-lookup"><span data-stu-id="e8d9a-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
