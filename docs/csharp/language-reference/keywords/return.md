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
ms.openlocfilehash: 058dc1d51099196559bee4ec2b96dc883e813f93
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236551"
---
# <a name="return-c-reference"></a><span data-ttu-id="1c2dd-102">return (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1c2dd-102">return (C# Reference)</span></span>

<span data-ttu-id="1c2dd-103">A instrução `return` finaliza a execução do método em que aparece e retorna o controle para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="1c2dd-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="1c2dd-104">Ela também pode retornar um valor opcional.</span><span class="sxs-lookup"><span data-stu-id="1c2dd-104">It can also return an optional value.</span></span> <span data-ttu-id="1c2dd-105">Se o método for um tipo `void`, a instrução `return` poderá ser omitida.</span><span class="sxs-lookup"><span data-stu-id="1c2dd-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="1c2dd-106">Se a instrução return estiver dentro de um bloco `try`, o bloco `finally`, se houver, será executado antes que o controle retorne para o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="1c2dd-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="1c2dd-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2dd-107">Example</span></span>

 <span data-ttu-id="1c2dd-108">No exemplo a seguir, o método `CalculateArea()` retorna a variável `area` local como um valor [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="1c2dd-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](double.md) value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="1c2dd-109">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1c2dd-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1c2dd-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c2dd-110">See also</span></span>

- [<span data-ttu-id="1c2dd-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1c2dd-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1c2dd-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1c2dd-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1c2dd-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1c2dd-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1c2dd-114">Instrução return</span><span class="sxs-lookup"><span data-stu-id="1c2dd-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
- [<span data-ttu-id="1c2dd-115">Instruções de atalho</span><span class="sxs-lookup"><span data-stu-id="1c2dd-115">Jump Statements</span></span>](jump-statements.md)
