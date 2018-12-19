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
ms.openlocfilehash: 1c5526366651d7e6623724c939b08ac46aa7db56
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242627"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="b21f8-102">sizeof (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b21f8-102">sizeof (C# Reference)</span></span>

<span data-ttu-id="b21f8-103">Usado para obter o tamanho, em bytes, de um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b21f8-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="b21f8-104">Os tipos não gerenciados incluem:</span><span class="sxs-lookup"><span data-stu-id="b21f8-104">Unmanaged types include:</span></span>

- <span data-ttu-id="b21f8-105">Os tipos simples que são listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="b21f8-105">The simple types that are listed in the following table:</span></span>

   |<span data-ttu-id="b21f8-106">Expressão</span><span class="sxs-lookup"><span data-stu-id="b21f8-106">Expression</span></span>|<span data-ttu-id="b21f8-107">Valor constante</span><span class="sxs-lookup"><span data-stu-id="b21f8-107">Constant value</span></span>|
   |----------------|--------------------|
   |`sizeof(sbyte)`|<span data-ttu-id="b21f8-108">1</span><span class="sxs-lookup"><span data-stu-id="b21f8-108">1</span></span>|
   |`sizeof(byte)`|<span data-ttu-id="b21f8-109">1</span><span class="sxs-lookup"><span data-stu-id="b21f8-109">1</span></span>|
   |`sizeof(short)`|<span data-ttu-id="b21f8-110">2</span><span class="sxs-lookup"><span data-stu-id="b21f8-110">2</span></span>|
   |`sizeof(ushort)`|<span data-ttu-id="b21f8-111">2</span><span class="sxs-lookup"><span data-stu-id="b21f8-111">2</span></span>|
   |`sizeof(int)`|<span data-ttu-id="b21f8-112">4</span><span class="sxs-lookup"><span data-stu-id="b21f8-112">4</span></span>|
   |`sizeof(uint)`|<span data-ttu-id="b21f8-113">4</span><span class="sxs-lookup"><span data-stu-id="b21f8-113">4</span></span>|
   |`sizeof(long)`|<span data-ttu-id="b21f8-114">8</span><span class="sxs-lookup"><span data-stu-id="b21f8-114">8</span></span>|
   |`sizeof(ulong)`|<span data-ttu-id="b21f8-115">8</span><span class="sxs-lookup"><span data-stu-id="b21f8-115">8</span></span>|
   |`sizeof(char)`|<span data-ttu-id="b21f8-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="b21f8-116">2 (Unicode)</span></span>|
   |`sizeof(float)`|<span data-ttu-id="b21f8-117">4</span><span class="sxs-lookup"><span data-stu-id="b21f8-117">4</span></span>|
   |`sizeof(double)`|<span data-ttu-id="b21f8-118">8</span><span class="sxs-lookup"><span data-stu-id="b21f8-118">8</span></span>|
   |`sizeof(decimal)`|<span data-ttu-id="b21f8-119">16</span><span class="sxs-lookup"><span data-stu-id="b21f8-119">16</span></span>|
   |`sizeof(bool)`|<span data-ttu-id="b21f8-120">1</span><span class="sxs-lookup"><span data-stu-id="b21f8-120">1</span></span>|

- <span data-ttu-id="b21f8-121">Tipos enumerados.</span><span class="sxs-lookup"><span data-stu-id="b21f8-121">Enum types.</span></span>

- <span data-ttu-id="b21f8-122">Tipos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="b21f8-122">Pointer types.</span></span>

- <span data-ttu-id="b21f8-123">Os structs definidos pelo usuário que não contêm campos de instância ou propriedades de instância autoimplementadas que são tipos de referência ou tipos construídos.</span><span class="sxs-lookup"><span data-stu-id="b21f8-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>

<span data-ttu-id="b21f8-124">O exemplo a seguir mostra como recuperar o tamanho de um `int`:</span><span class="sxs-lookup"><span data-stu-id="b21f8-124">The following example shows how to retrieve the size of an `int`:</span></span>

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a><span data-ttu-id="b21f8-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b21f8-125">Remarks</span></span>

<span data-ttu-id="b21f8-126">A partir da versão 2.0 do C#, aplicar `sizeof` a tipos simples ou enumerados não exige mais que o código seja compilado em um contexto [não seguro](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="b21f8-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>

<span data-ttu-id="b21f8-127">O operador `sizeof` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="b21f8-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="b21f8-128">Os valores retornados pelo operador `sizeof` são do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="b21f8-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="b21f8-129">A tabela anterior mostra os valores constantes que são substituídos por expressões `sizeof` que têm determinados tipos simples como operandos.</span><span class="sxs-lookup"><span data-stu-id="b21f8-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>

<span data-ttu-id="b21f8-130">Para todos os outros tipos, incluindo structs, o operador `sizeof` pode ser usado somente em blocos de código não seguro.</span><span class="sxs-lookup"><span data-stu-id="b21f8-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="b21f8-131">Embora você possa usar o método <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, o valor retornado por esse método não é sempre o mesmo que o valor retornado por `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="b21f8-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="b21f8-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> retorna o tamanho após o tipo ter passado por marshaling, enquanto `sizeof` retorna o tamanho como ele foi alocado pelo Common Language Runtime, incluindo qualquer preenchimento.</span><span class="sxs-lookup"><span data-stu-id="b21f8-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>

## <a name="example"></a><span data-ttu-id="b21f8-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b21f8-133">Example</span></span>

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a><span data-ttu-id="b21f8-134">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b21f8-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b21f8-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b21f8-135">See also</span></span>

- [<span data-ttu-id="b21f8-136">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b21f8-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b21f8-137">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b21f8-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b21f8-138">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b21f8-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b21f8-139">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="b21f8-139">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="b21f8-140">enum</span><span class="sxs-lookup"><span data-stu-id="b21f8-140">enum</span></span>](enum.md)
- [<span data-ttu-id="b21f8-141">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="b21f8-141">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="b21f8-142">Estruturas</span><span class="sxs-lookup"><span data-stu-id="b21f8-142">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="b21f8-143">Constantes</span><span class="sxs-lookup"><span data-stu-id="b21f8-143">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)