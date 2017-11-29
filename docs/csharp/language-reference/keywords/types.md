---
title: "Tipos (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c7285e237b04c1290391c4bba3e62886dceb83c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="types-c-reference"></a><span data-ttu-id="5a44a-102">Tipos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="5a44a-102">Types (C# Reference)</span></span>
<span data-ttu-id="5a44a-103">O sistema de digitação do C# contém as seguintes categorias:</span><span class="sxs-lookup"><span data-stu-id="5a44a-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="5a44a-104">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="5a44a-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="5a44a-105">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="5a44a-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="5a44a-106">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a44a-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="5a44a-107">Variáveis que são tipos de valor armazenam dados e as que são tipos de referência armazenam referências aos dados reais.</span><span class="sxs-lookup"><span data-stu-id="5a44a-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="5a44a-108">Os tipos de referência também são chamados de objetos.</span><span class="sxs-lookup"><span data-stu-id="5a44a-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="5a44a-109">Os tipos de ponteiro podem ser usados somente em modo [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="5a44a-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="5a44a-110">É possível converter um tipo de valor em um tipo de referência e, novamente em um tipo de valor, usando [conversões boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="5a44a-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="5a44a-111">Com exceção de um tipo de valor demarcado, não é possível converter um tipo de referência em um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="5a44a-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="5a44a-112">Esta seção também apresenta [nulo](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="5a44a-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="5a44a-113">Os tipos de valor também são anuláveis, o que significa que eles podem armazenar um estado sem valor adicional.</span><span class="sxs-lookup"><span data-stu-id="5a44a-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="5a44a-114">Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a44a-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a44a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a44a-115">See Also</span></span>  
 [<span data-ttu-id="5a44a-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5a44a-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5a44a-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5a44a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5a44a-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="5a44a-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5a44a-119">Tabelas de referência de tipos</span><span class="sxs-lookup"><span data-stu-id="5a44a-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="5a44a-120">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="5a44a-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="5a44a-121">Tipos</span><span class="sxs-lookup"><span data-stu-id="5a44a-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
