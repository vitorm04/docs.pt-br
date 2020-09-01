---
description: Instrução return – Referência de C#
title: Instrução return – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136988"
---
# <a name="return-c-reference"></a><span data-ttu-id="7b3dd-103">return (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7b3dd-103">return (C# Reference)</span></span>

<span data-ttu-id="7b3dd-104">A instrução `return` finaliza a execução do método em que aparece e retorna o controle para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="7b3dd-104">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="7b3dd-105">Ela também pode retornar um valor opcional.</span><span class="sxs-lookup"><span data-stu-id="7b3dd-105">It can also return an optional value.</span></span> <span data-ttu-id="7b3dd-106">Se o método for um tipo `void`, a instrução `return` poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="7b3dd-106">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="7b3dd-107">Se a instrução return estiver dentro de um bloco `try`, o bloco `finally`, se houver, será executado antes que o controle retorne para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="7b3dd-107">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="7b3dd-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b3dd-108">Example</span></span>

 <span data-ttu-id="7b3dd-109">No exemplo a seguir, o método `CalculateArea()` retorna a variável local `area` como um valor `double`.</span><span class="sxs-lookup"><span data-stu-id="7b3dd-109">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="7b3dd-110">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7b3dd-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7b3dd-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b3dd-111">See also</span></span>

- [<span data-ttu-id="7b3dd-112">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="7b3dd-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b3dd-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="7b3dd-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b3dd-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7b3dd-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7b3dd-115">Instrução de retorno</span><span class="sxs-lookup"><span data-stu-id="7b3dd-115">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
