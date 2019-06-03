---
title: sizeof – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: a00c4f96e62f7fd7d7c352aece097acd5b600ae2
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422404"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="826b7-102">sizeof (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="826b7-102">sizeof (C# Reference)</span></span>

<span data-ttu-id="826b7-103">Usado para obter o tamanho, em bytes, de um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="826b7-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="826b7-104">Os tipos não gerenciados incluem:</span><span class="sxs-lookup"><span data-stu-id="826b7-104">Unmanaged types include:</span></span>

- <span data-ttu-id="826b7-105">Os tipos simples que são listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="826b7-105">The simple types that are listed in the following table:</span></span>

   |<span data-ttu-id="826b7-106">Expressão</span><span class="sxs-lookup"><span data-stu-id="826b7-106">Expression</span></span>|<span data-ttu-id="826b7-107">Valor constante</span><span class="sxs-lookup"><span data-stu-id="826b7-107">Constant value</span></span>|
   |----------------|--------------------|
   |`sizeof(sbyte)`|<span data-ttu-id="826b7-108">1</span><span class="sxs-lookup"><span data-stu-id="826b7-108">1</span></span>|
   |`sizeof(byte)`|<span data-ttu-id="826b7-109">1</span><span class="sxs-lookup"><span data-stu-id="826b7-109">1</span></span>|
   |`sizeof(short)`|<span data-ttu-id="826b7-110">2</span><span class="sxs-lookup"><span data-stu-id="826b7-110">2</span></span>|
   |`sizeof(ushort)`|<span data-ttu-id="826b7-111">2</span><span class="sxs-lookup"><span data-stu-id="826b7-111">2</span></span>|
   |`sizeof(int)`|<span data-ttu-id="826b7-112">4</span><span class="sxs-lookup"><span data-stu-id="826b7-112">4</span></span>|
   |`sizeof(uint)`|<span data-ttu-id="826b7-113">4</span><span class="sxs-lookup"><span data-stu-id="826b7-113">4</span></span>|
   |`sizeof(long)`|<span data-ttu-id="826b7-114">8</span><span class="sxs-lookup"><span data-stu-id="826b7-114">8</span></span>|
   |`sizeof(ulong)`|<span data-ttu-id="826b7-115">8</span><span class="sxs-lookup"><span data-stu-id="826b7-115">8</span></span>|
   |`sizeof(char)`|<span data-ttu-id="826b7-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="826b7-116">2 (Unicode)</span></span>|
   |`sizeof(float)`|<span data-ttu-id="826b7-117">4</span><span class="sxs-lookup"><span data-stu-id="826b7-117">4</span></span>|
   |`sizeof(double)`|<span data-ttu-id="826b7-118">8</span><span class="sxs-lookup"><span data-stu-id="826b7-118">8</span></span>|
   |`sizeof(decimal)`|<span data-ttu-id="826b7-119">16</span><span class="sxs-lookup"><span data-stu-id="826b7-119">16</span></span>|
   |`sizeof(bool)`|<span data-ttu-id="826b7-120">1</span><span class="sxs-lookup"><span data-stu-id="826b7-120">1</span></span>|

- <span data-ttu-id="826b7-121">Tipos enumerados.</span><span class="sxs-lookup"><span data-stu-id="826b7-121">Enum types.</span></span>

- <span data-ttu-id="826b7-122">Tipos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="826b7-122">Pointer types.</span></span>

- <span data-ttu-id="826b7-123">Os structs definidos pelo usuário que não contêm campos de instância ou propriedades de instância autoimplementadas que são tipos de referência ou tipos construídos.</span><span class="sxs-lookup"><span data-stu-id="826b7-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>

<span data-ttu-id="826b7-124">O exemplo a seguir mostra como recuperar o tamanho de um `int`:</span><span class="sxs-lookup"><span data-stu-id="826b7-124">The following example shows how to retrieve the size of an `int`:</span></span>

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a><span data-ttu-id="826b7-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="826b7-125">Remarks</span></span>

<span data-ttu-id="826b7-126">A partir da versão 2.0 do C#, aplicar `sizeof` a tipos simples ou enumerados não exige mais que o código seja compilado em um contexto [não seguro](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="826b7-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>

<span data-ttu-id="826b7-127">O operador `sizeof` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="826b7-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="826b7-128">Os valores retornados pelo operador `sizeof` são do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="826b7-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="826b7-129">A tabela anterior mostra os valores constantes que são substituídos por expressões `sizeof` que têm determinados tipos simples como operandos.</span><span class="sxs-lookup"><span data-stu-id="826b7-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>

<span data-ttu-id="826b7-130">Para todos os outros tipos, incluindo structs, o operador `sizeof` pode ser usado somente em blocos de código não seguro.</span><span class="sxs-lookup"><span data-stu-id="826b7-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="826b7-131">Embora você possa usar o método <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, o valor retornado por esse método não é sempre o mesmo que o valor retornado por `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="826b7-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="826b7-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> retorna o tamanho após o tipo ter passado por marshaling, enquanto `sizeof` retorna o tamanho como ele foi alocado pelo Common Language Runtime, incluindo qualquer preenchimento.</span><span class="sxs-lookup"><span data-stu-id="826b7-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>

## <a name="example"></a><span data-ttu-id="826b7-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="826b7-133">Example</span></span>

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a><span data-ttu-id="826b7-134">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="826b7-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="826b7-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="826b7-135">See also</span></span>

- [<span data-ttu-id="826b7-136">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="826b7-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="826b7-137">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="826b7-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="826b7-138">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="826b7-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="826b7-139">enum</span><span class="sxs-lookup"><span data-stu-id="826b7-139">enum</span></span>](enum.md)
- [<span data-ttu-id="826b7-140">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="826b7-140">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="826b7-141">Estruturas</span><span class="sxs-lookup"><span data-stu-id="826b7-141">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="826b7-142">Constantes</span><span class="sxs-lookup"><span data-stu-id="826b7-142">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)
