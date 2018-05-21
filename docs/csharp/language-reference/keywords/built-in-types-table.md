---
title: Tabela de tipos internos (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 120347e5bff7f0d6c7120af0cb250936ca39ea16
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="07174-102">Tabela de tipos internos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="07174-102">Built-In Types Table (C# Reference)</span></span>
<span data-ttu-id="07174-103">A tabela a seguir mostra as palavras-chave para tipos internos do C#, que são aliases de tipos predefinidos no namespace <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="07174-103">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="07174-104">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="07174-104">C# Type</span></span>|<span data-ttu-id="07174-105">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07174-105">.NET Framework Type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="07174-106">bool</span><span class="sxs-lookup"><span data-stu-id="07174-106">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[<span data-ttu-id="07174-107">byte</span><span class="sxs-lookup"><span data-stu-id="07174-107">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[<span data-ttu-id="07174-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="07174-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[<span data-ttu-id="07174-109">char</span><span class="sxs-lookup"><span data-stu-id="07174-109">char</span></span>](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[<span data-ttu-id="07174-110">decimal</span><span class="sxs-lookup"><span data-stu-id="07174-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[<span data-ttu-id="07174-111">double</span><span class="sxs-lookup"><span data-stu-id="07174-111">double</span></span>](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[<span data-ttu-id="07174-112">float</span><span class="sxs-lookup"><span data-stu-id="07174-112">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[<span data-ttu-id="07174-113">int</span><span class="sxs-lookup"><span data-stu-id="07174-113">int</span></span>](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[<span data-ttu-id="07174-114">uint</span><span class="sxs-lookup"><span data-stu-id="07174-114">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[<span data-ttu-id="07174-115">long</span><span class="sxs-lookup"><span data-stu-id="07174-115">long</span></span>](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[<span data-ttu-id="07174-116">ulong</span><span class="sxs-lookup"><span data-stu-id="07174-116">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[<span data-ttu-id="07174-117">object</span><span class="sxs-lookup"><span data-stu-id="07174-117">object</span></span>](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[<span data-ttu-id="07174-118">short</span><span class="sxs-lookup"><span data-stu-id="07174-118">short</span></span>](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[<span data-ttu-id="07174-119">ushort</span><span class="sxs-lookup"><span data-stu-id="07174-119">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[<span data-ttu-id="07174-120">string</span><span class="sxs-lookup"><span data-stu-id="07174-120">string</span></span>](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a><span data-ttu-id="07174-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="07174-121">Remarks</span></span>  
 <span data-ttu-id="07174-122">Todos os tipos na tabela, exceto `object` e `string`, são referidos como tipos simples.</span><span class="sxs-lookup"><span data-stu-id="07174-122">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
 <span data-ttu-id="07174-123">As palavras-chave de tipo C# e seus aliases são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="07174-123">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="07174-124">Por exemplo, é possível declarar uma variável de inteiro usando uma das seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="07174-124">For example, you can declare an integer variable by using either of the following declarations:</span></span>  
  
```csharp  
int x = 123;  
System.Int32 x = 123;  
```  
  
 <span data-ttu-id="07174-125">Para exibir o tipo real para qualquer tipo de C#, use o método do sistema `GetType()`.</span><span class="sxs-lookup"><span data-stu-id="07174-125">To display the actual type for any C# type, use the system method `GetType()`.</span></span> <span data-ttu-id="07174-126">Por exemplo, a instrução a seguir exibe o alias do sistema que representa o tipo de `myVariable`:</span><span class="sxs-lookup"><span data-stu-id="07174-126">For example, the following statement displays the system alias that represents the type of `myVariable`:</span></span>  
  
```csharp  
Console.WriteLine(myVariable.GetType());  
```  
  
 <span data-ttu-id="07174-127">Também é possível usar o operador [typeof](../../../csharp/language-reference/keywords/typeof.md).</span><span class="sxs-lookup"><span data-stu-id="07174-127">You can also use the [typeof](../../../csharp/language-reference/keywords/typeof.md) operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07174-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07174-128">See Also</span></span>  
 [<span data-ttu-id="07174-129">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="07174-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="07174-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="07174-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="07174-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="07174-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="07174-132">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="07174-132">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="07174-133">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="07174-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="07174-134">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="07174-134">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [<span data-ttu-id="07174-135">dynamic</span><span class="sxs-lookup"><span data-stu-id="07174-135">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="07174-136">Tabelas de referência de tipos</span><span class="sxs-lookup"><span data-stu-id="07174-136">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
