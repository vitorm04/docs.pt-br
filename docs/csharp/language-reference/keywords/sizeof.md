---
title: sizeof (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 83038255160ec778c71120566cf8f99092761add
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270572"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="17505-102">sizeof (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="17505-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="17505-103">Usado para obter o tamanho, em bytes, de um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="17505-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="17505-104">Tipos não gerenciados incluem os tipos internos listados na tabela a seguir e também o seguinte:</span><span class="sxs-lookup"><span data-stu-id="17505-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="17505-105">Tipos enum</span><span class="sxs-lookup"><span data-stu-id="17505-105">Enum types</span></span>  
  
-   <span data-ttu-id="17505-106">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="17505-106">Pointer types</span></span>  
  
-   <span data-ttu-id="17505-107">Structs definidos pelo usuário que não contêm campos ou propriedades que são tipos de referência</span><span class="sxs-lookup"><span data-stu-id="17505-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="17505-108">O exemplo a seguir mostra como recuperar o tamanho de um `int`:</span><span class="sxs-lookup"><span data-stu-id="17505-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="17505-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="17505-109">Remarks</span></span>  
 <span data-ttu-id="17505-110">A partir da versão 2.0 do C#, aplicar `sizeof` a tipos internos não exige mais que o modo [não seguro](../../../csharp/language-reference/keywords/unsafe.md) seja usado.</span><span class="sxs-lookup"><span data-stu-id="17505-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="17505-111">O operador `sizeof` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="17505-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="17505-112">Os valores retornados pelo operador `sizeof` são do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="17505-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="17505-113">A tabela a seguir mostra os valores constantes que são substituídos por expressões `sizeof` que têm determinados tipos internos como operandos.</span><span class="sxs-lookup"><span data-stu-id="17505-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="17505-114">Expressão</span><span class="sxs-lookup"><span data-stu-id="17505-114">Expression</span></span>|<span data-ttu-id="17505-115">Valor constante</span><span class="sxs-lookup"><span data-stu-id="17505-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="17505-116">1</span><span class="sxs-lookup"><span data-stu-id="17505-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="17505-117">1</span><span class="sxs-lookup"><span data-stu-id="17505-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="17505-118">2</span><span class="sxs-lookup"><span data-stu-id="17505-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="17505-119">2</span><span class="sxs-lookup"><span data-stu-id="17505-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="17505-120">4</span><span class="sxs-lookup"><span data-stu-id="17505-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="17505-121">4</span><span class="sxs-lookup"><span data-stu-id="17505-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="17505-122">8</span><span class="sxs-lookup"><span data-stu-id="17505-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="17505-123">8</span><span class="sxs-lookup"><span data-stu-id="17505-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="17505-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="17505-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="17505-125">4</span><span class="sxs-lookup"><span data-stu-id="17505-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="17505-126">8</span><span class="sxs-lookup"><span data-stu-id="17505-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="17505-127">16</span><span class="sxs-lookup"><span data-stu-id="17505-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="17505-128">1</span><span class="sxs-lookup"><span data-stu-id="17505-128">1</span></span>|  
  
 <span data-ttu-id="17505-129">Para todos os outros tipos, incluindo structs, o operador `sizeof` pode ser usado somente em blocos de código não seguro.</span><span class="sxs-lookup"><span data-stu-id="17505-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="17505-130">Embora você possa usar o método <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, o valor retornado por esse método não é sempre o mesmo que o valor retornado por `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="17505-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="17505-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> retorna o tamanho após o tipo ter passado por marshaling, enquanto `sizeof` retorna o tamanho como ele foi alocado pelo Common Language Runtime, incluindo qualquer preenchimento.</span><span class="sxs-lookup"><span data-stu-id="17505-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17505-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17505-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="17505-133">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="17505-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="17505-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17505-134">See Also</span></span>  
 [<span data-ttu-id="17505-135">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="17505-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="17505-136">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="17505-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="17505-137">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="17505-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="17505-138">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="17505-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="17505-139">enum</span><span class="sxs-lookup"><span data-stu-id="17505-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="17505-140">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="17505-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="17505-141">Estruturas</span><span class="sxs-lookup"><span data-stu-id="17505-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="17505-142">Constantes</span><span class="sxs-lookup"><span data-stu-id="17505-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
