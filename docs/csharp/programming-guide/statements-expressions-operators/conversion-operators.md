---
title: "Operadores de conversão (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c12fd13d6526d79363f973ce2a944c4823bf4104
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="5b621-102">Operadores de conversão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5b621-102">Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="5b621-103">O C# habilita os programadores a declarar conversões em classes ou structs, para que tais classes ou structs possam ser convertidas para e/ou de outras classes ou structs ou tipos básicos.</span><span class="sxs-lookup"><span data-stu-id="5b621-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="5b621-104">As conversões são definidas como operadores e nomeadas para o tipo para o qual são convertidas.</span><span class="sxs-lookup"><span data-stu-id="5b621-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="5b621-105">O tipo do argumento a ser convertido ou o tipo do resultado da conversão, mas não ambos, deve ser o tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="5b621-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 <span data-ttu-id="5b621-106">[!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5b621-106">[!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]</span></span>  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="5b621-107">Visão Geral dos Operadores de Conversão</span><span class="sxs-lookup"><span data-stu-id="5b621-107">Conversion Operators Overview</span></span>  
 <span data-ttu-id="5b621-108">Os operadores de conversão têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="5b621-108">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="5b621-109">Conversões declaradas como `implicit` ocorrem automaticamente quando for necessário.</span><span class="sxs-lookup"><span data-stu-id="5b621-109">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="5b621-110">Conversões declaradas como `explicit` exigem que uma conversão seja chamada.</span><span class="sxs-lookup"><span data-stu-id="5b621-110">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="5b621-111">Todas as conversões devem ser declaradas como `static`.</span><span class="sxs-lookup"><span data-stu-id="5b621-111">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5b621-112">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="5b621-112">Related Sections</span></span>  
 <span data-ttu-id="5b621-113">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="5b621-113">For more information:</span></span>  
  
-   [<span data-ttu-id="5b621-114">Usando operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="5b621-114">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="5b621-115">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="5b621-115">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="5b621-116">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="5b621-116">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="5b621-117">explicit</span><span class="sxs-lookup"><span data-stu-id="5b621-117">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="5b621-118">implicit</span><span class="sxs-lookup"><span data-stu-id="5b621-118">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="5b621-119">static</span><span class="sxs-lookup"><span data-stu-id="5b621-119">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b621-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b621-120">See Also</span></span>  
 <span data-ttu-id="5b621-121"><xref:System.Convert></span><span class="sxs-lookup"><span data-stu-id="5b621-121"><xref:System.Convert></span></span>   
 <span data-ttu-id="5b621-122">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5b621-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="5b621-123">Conversões explícitas encadeadas definidas pelo usuário em C#</span><span class="sxs-lookup"><span data-stu-id="5b621-123">Chained user-defined explicit conversions in C#</span></span>](http://go.microsoft.com/fwlink/?LinkId=112384)

