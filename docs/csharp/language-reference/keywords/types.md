---
title: "Tipos (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2816a5dd86e71641198a340b3a72094dffc93bdf
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="types-c-reference"></a><span data-ttu-id="4dfde-102">Tipos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4dfde-102">Types (C# Reference)</span></span>
<span data-ttu-id="4dfde-103">O sistema de digitação do C# contém as seguintes categorias:</span><span class="sxs-lookup"><span data-stu-id="4dfde-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="4dfde-104">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="4dfde-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="4dfde-105">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="4dfde-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="4dfde-106">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="4dfde-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="4dfde-107">Variáveis que são tipos de valor armazenam dados e as que são tipos de referência armazenam referências aos dados reais.</span><span class="sxs-lookup"><span data-stu-id="4dfde-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="4dfde-108">Os tipos de referência também são chamados de objetos.</span><span class="sxs-lookup"><span data-stu-id="4dfde-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="4dfde-109">Os tipos de ponteiro podem ser usados somente em modo [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="4dfde-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="4dfde-110">É possível converter um tipo de valor em um tipo de referência e, novamente em um tipo de valor, usando [conversões boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="4dfde-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="4dfde-111">Com exceção de um tipo de valor demarcado, não é possível converter um tipo de referência em um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="4dfde-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="4dfde-112">Esta seção também apresenta [nulo](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="4dfde-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="4dfde-113">Os tipos de valor também são anuláveis, o que significa que eles podem armazenar um estado sem valor adicional.</span><span class="sxs-lookup"><span data-stu-id="4dfde-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="4dfde-114">Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="4dfde-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfde-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dfde-115">See Also</span></span>  
 <span data-ttu-id="4dfde-116">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4dfde-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4dfde-117">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4dfde-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4dfde-118">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="4dfde-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="4dfde-119">[Tabelas de Referência de Tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span><span class="sxs-lookup"><span data-stu-id="4dfde-119">[Reference Tables for Types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span></span>  
 <span data-ttu-id="4dfde-120">[Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="4dfde-120">[Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
 [<span data-ttu-id="4dfde-121">Tipos</span><span class="sxs-lookup"><span data-stu-id="4dfde-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)

