---
title: Operador sizeof – referência em C#
ms.custom: seodec18
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 32103043d4c3a8b38f4c8aad80282f6c0555719f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038932"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="2beba-102">Operador sizeof (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="2beba-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="2beba-103">O operador `sizeof` retorna o número de bytes ocupados por uma variável de um determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="2beba-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="2beba-104">O argumento do operador `sizeof` deve ser o nome de um [tipo não gerenciado](../builtin-types/unmanaged-types.md) ou um parâmetro de tipo que seja [restrito](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) a um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2beba-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="2beba-105">O operador `sizeof` exige um contexto [não seguro](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="2beba-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="2beba-106">No entanto, as expressões apresentadas na tabela a seguir são avaliadas em tempo de compilação para os valores constantes correspondentes e não exigem um contexto não seguro:</span><span class="sxs-lookup"><span data-stu-id="2beba-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="2beba-107">Expressão</span><span class="sxs-lookup"><span data-stu-id="2beba-107">Expression</span></span>|<span data-ttu-id="2beba-108">Valor constante</span><span class="sxs-lookup"><span data-stu-id="2beba-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="2beba-109">1</span><span class="sxs-lookup"><span data-stu-id="2beba-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="2beba-110">1</span><span class="sxs-lookup"><span data-stu-id="2beba-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="2beba-111">2</span><span class="sxs-lookup"><span data-stu-id="2beba-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="2beba-112">2</span><span class="sxs-lookup"><span data-stu-id="2beba-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="2beba-113">4</span><span class="sxs-lookup"><span data-stu-id="2beba-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="2beba-114">4</span><span class="sxs-lookup"><span data-stu-id="2beba-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="2beba-115">8</span><span class="sxs-lookup"><span data-stu-id="2beba-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="2beba-116">8</span><span class="sxs-lookup"><span data-stu-id="2beba-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="2beba-117">2</span><span class="sxs-lookup"><span data-stu-id="2beba-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="2beba-118">4</span><span class="sxs-lookup"><span data-stu-id="2beba-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="2beba-119">8</span><span class="sxs-lookup"><span data-stu-id="2beba-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="2beba-120">16</span><span class="sxs-lookup"><span data-stu-id="2beba-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="2beba-121">1</span><span class="sxs-lookup"><span data-stu-id="2beba-121">1</span></span>|

<span data-ttu-id="2beba-122">Você também não precisará usar um contexto não seguro quando o operando do operador `sizeof` for o nome de um tipo [enumerado](../keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="2beba-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="2beba-123">O exemplo a seguir demonstra o uso do operador `sizeof`:</span><span class="sxs-lookup"><span data-stu-id="2beba-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="2beba-124">O operador `sizeof` retorna o número de bytes que seriam alocados pelo Common Language Runtime na memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="2beba-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="2beba-125">Para tipos [struct](../keywords/struct.md), esse valor inclui todo o preenchimento, como demonstra o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="2beba-125">For [struct](../keywords/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="2beba-126">O resultado do operador `sizeof` pode ser diferente do resultado do método <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, que retorna o tamanho de um tipo na memória *não gerenciada*.</span><span class="sxs-lookup"><span data-stu-id="2beba-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2beba-127">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2beba-127">C# language specification</span></span>

<span data-ttu-id="2beba-128">Para obter mais informações, confira a seção [O operador sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator), nas [especificações da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2beba-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2beba-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2beba-129">See also</span></span>

- [<span data-ttu-id="2beba-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="2beba-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2beba-131">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="2beba-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="2beba-132">Operadores relacionados a ponteiro</span><span class="sxs-lookup"><span data-stu-id="2beba-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="2beba-133">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="2beba-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="2beba-134">Tipos relativos a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="2beba-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="2beba-135">Genéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="2beba-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
