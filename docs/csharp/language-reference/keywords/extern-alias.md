---
description: extern alias – Referência de C#
title: extern alias – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 301ae06ec02fa6f09257dc87383bc2ec7f589b6d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139002"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="a1e93-103">extern alias (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a1e93-103">extern alias (C# Reference)</span></span>
<span data-ttu-id="a1e93-104">Talvez seja necessário referenciar duas versões de assemblies que têm os mesmos nomes de tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="a1e93-104">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="a1e93-105">Por exemplo, você pode ter que usar duas ou mais versões de um assembly no mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1e93-105">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="a1e93-106">Ao usar um alias de assembly externo, os namespaces de cada assembly podem ser encapsulados dentro de namespaces de nível raiz nomeados pelo alias, permitindo que eles sejam utilizados no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="a1e93-106">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1e93-107">A palavra-chave [extern](./extern.md) também é usada como um modificador de método, declarando um método escrito em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a1e93-107">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="a1e93-108">Para referenciar dois assemblies com os mesmos nomes de tipo totalmente qualificado, um alias deve ser especificado em um prompt de comando, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a1e93-108">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="a1e93-109">Isso cria os alias externos `GridV1` e `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="a1e93-109">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="a1e93-110">Para usar esses aliases de dentro de um programa, referencie-os usando a palavra-chave `extern`.</span><span class="sxs-lookup"><span data-stu-id="a1e93-110">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="a1e93-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a1e93-111">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="a1e93-112">Cada declaração de alias externo apresenta um namespace de nível raiz adicional que funciona de forma paralela (mas não dentro) com o namespace global.</span><span class="sxs-lookup"><span data-stu-id="a1e93-112">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="a1e93-113">Portanto, os tipos de cada assembly podem ser referenciados sem ambiguidade, usando seus nomes totalmente qualificados, enraizados no alias de namespace apropriado.</span><span class="sxs-lookup"><span data-stu-id="a1e93-113">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="a1e93-114">No exemplo anterior, `GridV1::Grid` seria o controle de grade da `grid.dll` e `GridV2::Grid` seria o controle de grade da `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="a1e93-114">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="using-visual-studio"></a><span data-ttu-id="a1e93-115">Como usar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1e93-115">Using Visual Studio</span></span>

<span data-ttu-id="a1e93-116">Se você estiver usando o Visual Studio, os aliases podem ser fornecidos de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="a1e93-116">If you are using Visual Studio, aliases can be provided in similar way.</span></span>

<span data-ttu-id="a1e93-117">Adicione referência de *grid.dll* e *grid20.dll* ao seu projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1e93-117">Add reference of *grid.dll* and *grid20.dll* to your project in Visual Studio.</span></span> <span data-ttu-id="a1e93-118">Abra uma guia de propriedade e altere os aliases de global para GridV1 e GridV2, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a1e93-118">Open a property tab and change the Aliases from global to GridV1 and GridV2 respectively.</span></span>

<span data-ttu-id="a1e93-119">Use esses aliases da mesma maneira acima</span><span class="sxs-lookup"><span data-stu-id="a1e93-119">Use these aliases the same way above</span></span>

```csharp
 extern alias GridV1;  
  
 extern alias GridV2;  
```

<span data-ttu-id="a1e93-120">Agora você pode criar um alias para um namespace ou um tipo *usando a diretiva alias*.</span><span class="sxs-lookup"><span data-stu-id="a1e93-120">Now you can create alias for a namespace or a type by *using alias directive*.</span></span> <span data-ttu-id="a1e93-121">Para obter mais informações, consulte [usando a diretiva](using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="a1e93-121">For more information, see [using directive](using-directive.md).</span></span>

```csharp
using Class1V1 = GridV1::Namespace.Class1;

using Class1V2 = GridV2::Namespace.Class1;
```

## <a name="c-language-specification"></a><span data-ttu-id="a1e93-122">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a1e93-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1e93-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="a1e93-123">See also</span></span>

- [<span data-ttu-id="a1e93-124">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="a1e93-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a1e93-125">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="a1e93-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a1e93-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a1e93-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="a1e93-127">Operador::</span><span class="sxs-lookup"><span data-stu-id="a1e93-127">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="a1e93-128">-Reference (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="a1e93-128">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
