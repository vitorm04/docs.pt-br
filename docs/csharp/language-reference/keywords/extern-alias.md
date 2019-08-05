---
title: extern alias – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: cfb662203216aa6ca208ceec20d55164c65163dc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626653"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="679b7-102">extern alias (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="679b7-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="679b7-103">Talvez seja necessário referenciar duas versões de assemblies que têm os mesmos nomes de tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="679b7-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="679b7-104">Por exemplo, você pode ter que usar duas ou mais versões de um assembly no mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="679b7-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="679b7-105">Ao usar um alias de assembly externo, os namespaces de cada assembly podem ser encapsulados dentro de namespaces de nível raiz nomeados pelo alias, permitindo que eles sejam utilizados no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="679b7-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="679b7-106">A palavra-chave [extern](../../../csharp/language-reference/keywords/extern.md) também é usada como um modificador de método, declarando um método escrito em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="679b7-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="679b7-107">Para referenciar dois assemblies com os mesmos nomes de tipo totalmente qualificado, um alias deve ser especificado em um prompt de comando, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="679b7-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="679b7-108">Isso cria os alias externos `GridV1` e `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="679b7-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="679b7-109">Para usar esses aliases de dentro de um programa, referencie-os usando a palavra-chave `extern`.</span><span class="sxs-lookup"><span data-stu-id="679b7-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="679b7-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="679b7-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="679b7-111">Cada declaração de alias externo apresenta um namespace de nível raiz adicional que funciona de forma paralela (mas não dentro) com o namespace global.</span><span class="sxs-lookup"><span data-stu-id="679b7-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="679b7-112">Portanto, os tipos de cada assembly podem ser referenciados sem ambiguidade, usando seus nomes totalmente qualificados, enraizados no alias de namespace apropriado.</span><span class="sxs-lookup"><span data-stu-id="679b7-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="679b7-113">No exemplo anterior, `GridV1::Grid` seria o controle de grade da `grid.dll` e `GridV2::Grid` seria o controle de grade da `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="679b7-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="679b7-114">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="679b7-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="679b7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="679b7-115">See also</span></span>

- [<span data-ttu-id="679b7-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="679b7-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="679b7-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="679b7-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="679b7-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="679b7-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="679b7-119">:: ??</span><span class="sxs-lookup"><span data-stu-id="679b7-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="679b7-120">/reference (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="679b7-120">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
