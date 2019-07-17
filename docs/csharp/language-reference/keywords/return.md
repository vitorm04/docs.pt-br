---
title: Instrução return – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: a845ce257bf7f0cf0e64d6815b2278f6cec946e7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661611"
---
# <a name="return-c-reference"></a><span data-ttu-id="b5151-102">return (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b5151-102">return (C# Reference)</span></span>

<span data-ttu-id="b5151-103">A instrução `return` finaliza a execução do método em que aparece e retorna o controle para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="b5151-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="b5151-104">Ela também pode retornar um valor opcional.</span><span class="sxs-lookup"><span data-stu-id="b5151-104">It can also return an optional value.</span></span> <span data-ttu-id="b5151-105">Se o método for um tipo `void`, a instrução `return` poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="b5151-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="b5151-106">Se a instrução return estiver dentro de um bloco `try`, o bloco `finally`, se houver, será executado antes que o controle retorne para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="b5151-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="b5151-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5151-107">Example</span></span>

 <span data-ttu-id="b5151-108">No exemplo a seguir, o método `CalculateArea()` retorna a variável local `area` como um valor `double`.</span><span class="sxs-lookup"><span data-stu-id="b5151-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="b5151-109">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b5151-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b5151-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5151-110">See also</span></span>

- [<span data-ttu-id="b5151-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b5151-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b5151-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b5151-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b5151-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b5151-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b5151-114">Instrução return</span><span class="sxs-lookup"><span data-stu-id="b5151-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
