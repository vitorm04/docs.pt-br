---
title: sizeof (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="24b16-102">sizeof (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="24b16-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="24b16-103">Usado para obter o tamanho, em bytes, de um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="24b16-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="24b16-104">Tipos não gerenciados incluem os tipos internos listados na tabela a seguir e também o seguinte:</span><span class="sxs-lookup"><span data-stu-id="24b16-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="24b16-105">Tipos enum</span><span class="sxs-lookup"><span data-stu-id="24b16-105">Enum types</span></span>  
  
-   <span data-ttu-id="24b16-106">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="24b16-106">Pointer types</span></span>  
  
-   <span data-ttu-id="24b16-107">Structs definidos pelo usuário que não contêm campos ou propriedades que são tipos de referência</span><span class="sxs-lookup"><span data-stu-id="24b16-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="24b16-108">O exemplo a seguir mostra como recuperar o tamanho de um `int`:</span><span class="sxs-lookup"><span data-stu-id="24b16-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="24b16-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="24b16-109">Remarks</span></span>  
 <span data-ttu-id="24b16-110">A partir da versão 2.0 do C#, aplicar `sizeof` a tipos internos não exige mais que o modo [não seguro](../../../csharp/language-reference/keywords/unsafe.md) seja usado.</span><span class="sxs-lookup"><span data-stu-id="24b16-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="24b16-111">O operador `sizeof` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="24b16-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="24b16-112">Os valores retornados pelo operador `sizeof` são do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="24b16-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="24b16-113">A tabela a seguir mostra os valores constantes que são substituídos por expressões `sizeof` que têm determinados tipos internos como operandos.</span><span class="sxs-lookup"><span data-stu-id="24b16-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="24b16-114">Expressão</span><span class="sxs-lookup"><span data-stu-id="24b16-114">Expression</span></span>|<span data-ttu-id="24b16-115">Valor constante</span><span class="sxs-lookup"><span data-stu-id="24b16-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="24b16-116">1</span><span class="sxs-lookup"><span data-stu-id="24b16-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="24b16-117">1</span><span class="sxs-lookup"><span data-stu-id="24b16-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="24b16-118">2</span><span class="sxs-lookup"><span data-stu-id="24b16-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="24b16-119">2</span><span class="sxs-lookup"><span data-stu-id="24b16-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="24b16-120">4</span><span class="sxs-lookup"><span data-stu-id="24b16-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="24b16-121">4</span><span class="sxs-lookup"><span data-stu-id="24b16-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="24b16-122">8</span><span class="sxs-lookup"><span data-stu-id="24b16-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="24b16-123">8</span><span class="sxs-lookup"><span data-stu-id="24b16-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="24b16-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="24b16-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="24b16-125">4</span><span class="sxs-lookup"><span data-stu-id="24b16-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="24b16-126">8</span><span class="sxs-lookup"><span data-stu-id="24b16-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="24b16-127">16</span><span class="sxs-lookup"><span data-stu-id="24b16-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="24b16-128">1</span><span class="sxs-lookup"><span data-stu-id="24b16-128">1</span></span>|  
  
 <span data-ttu-id="24b16-129">Para todos os outros tipos, incluindo structs, o operador `sizeof` pode ser usado somente em blocos de código não seguro.</span><span class="sxs-lookup"><span data-stu-id="24b16-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="24b16-130">Embora você possa usar o método <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, o valor retornado por esse método não é sempre o mesmo que o valor retornado por `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="24b16-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="24b16-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> retorna o tamanho após o tipo ter passado por marshaling, enquanto `sizeof` retorna o tamanho como ele foi alocado pelo Common Language Runtime, incluindo qualquer preenchimento.</span><span class="sxs-lookup"><span data-stu-id="24b16-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24b16-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24b16-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="24b16-133">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="24b16-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="24b16-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24b16-134">See Also</span></span>  
 [<span data-ttu-id="24b16-135">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="24b16-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="24b16-136">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="24b16-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="24b16-137">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="24b16-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="24b16-138">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="24b16-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="24b16-139">enum</span><span class="sxs-lookup"><span data-stu-id="24b16-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="24b16-140">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="24b16-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="24b16-141">Estruturas</span><span class="sxs-lookup"><span data-stu-id="24b16-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="24b16-142">Constantes</span><span class="sxs-lookup"><span data-stu-id="24b16-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
