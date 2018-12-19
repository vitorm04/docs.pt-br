---
title: Instrução goto – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: bfc997631cc147bf5718ec91a57e2995cead052f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236759"
---
# <a name="goto-c-reference"></a><span data-ttu-id="61c3c-102">goto (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="61c3c-102">goto (C# Reference)</span></span>

<span data-ttu-id="61c3c-103">A declaração `goto` transfere o controle do programa diretamente para uma instrução rotulada.</span><span class="sxs-lookup"><span data-stu-id="61c3c-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="61c3c-104">Um uso comum de `goto` é a transferência do controle para um rótulo de caso de opção específico ou para o rótulo padrão em uma instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="61c3c-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="61c3c-105">A instrução `goto` também é útil para sair de loops profundamente aninhados.</span><span class="sxs-lookup"><span data-stu-id="61c3c-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="61c3c-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61c3c-106">Example</span></span>

<span data-ttu-id="61c3c-107">O exemplo a seguir demonstra o uso de `goto` em uma instrução [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="61c3c-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="61c3c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61c3c-108">Example</span></span>

<span data-ttu-id="61c3c-109">O exemplo a seguir demonstra o uso de `goto` para sair de loops aninhados.</span><span class="sxs-lookup"><span data-stu-id="61c3c-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="61c3c-110">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="61c3c-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="61c3c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61c3c-111">See also</span></span>

- [<span data-ttu-id="61c3c-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="61c3c-112">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="61c3c-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="61c3c-113">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="61c3c-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="61c3c-114">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="61c3c-115">Instrução goto (C++)</span><span class="sxs-lookup"><span data-stu-id="61c3c-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)  
- [<span data-ttu-id="61c3c-116">Instruções de atalho</span><span class="sxs-lookup"><span data-stu-id="61c3c-116">Jump Statements</span></span>](jump-statements.md)  
