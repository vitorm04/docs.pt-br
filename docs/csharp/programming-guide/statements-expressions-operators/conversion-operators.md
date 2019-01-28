---
title: Operadores de conversão – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 071eb75d9bab2b91b9cdb8ecc33df249b01e7ac6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619742"
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="e33e5-102">Operadores de conversão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e33e5-102">Conversion operators (C# Programming Guide)</span></span>

<span data-ttu-id="e33e5-103">O C# habilita os programadores a declarar conversões em classes ou structs, para que tais classes ou structs possam ser convertidas para e/ou de outras classes ou structs ou tipos básicos.</span><span class="sxs-lookup"><span data-stu-id="e33e5-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="e33e5-104">As conversões são definidas como operadores e nomeadas para o tipo para o qual são convertidas.</span><span class="sxs-lookup"><span data-stu-id="e33e5-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="e33e5-105">O tipo do argumento a ser convertido ou o tipo do resultado da conversão, mas não ambos, deve ser o tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="e33e5-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="e33e5-106">Visão geral dos operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="e33e5-106">Conversion operators overview</span></span>

 <span data-ttu-id="e33e5-107">Os operadores de conversão têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e33e5-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="e33e5-108">Conversões declaradas como `implicit` ocorrem automaticamente quando for necessário.</span><span class="sxs-lookup"><span data-stu-id="e33e5-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="e33e5-109">Conversões declaradas como `explicit` exigem que uma conversão seja chamada.</span><span class="sxs-lookup"><span data-stu-id="e33e5-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="e33e5-110">Todas as conversões devem ser declaradas como `static`.</span><span class="sxs-lookup"><span data-stu-id="e33e5-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e33e5-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e33e5-111">Related sections</span></span>

 <span data-ttu-id="e33e5-112">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="e33e5-112">For more information:</span></span>  
  
-   [<span data-ttu-id="e33e5-113">Usando operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="e33e5-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="e33e5-114">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="e33e5-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="e33e5-115">Como: implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="e33e5-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="e33e5-116">explicit</span><span class="sxs-lookup"><span data-stu-id="e33e5-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="e33e5-117">implicit</span><span class="sxs-lookup"><span data-stu-id="e33e5-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="e33e5-118">static</span><span class="sxs-lookup"><span data-stu-id="e33e5-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="e33e5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e33e5-119">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="e33e5-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e33e5-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e33e5-121">Conversões explícitas encadeadas definidas pelo usuário em C#</span><span class="sxs-lookup"><span data-stu-id="e33e5-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
