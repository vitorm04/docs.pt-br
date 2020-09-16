---
title: Tipos blittable e não blittable
description: Saiba mais sobre tipos blittable e não blittable. Os tipos de dados blittable são normalmente representados em memória gerenciada e não gerenciada e não precisam de manipulação especial.
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: 8bbf9c72143033cec22b38cc26cbe8ceb44f790b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556265"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="c4f55-104">Tipos blittable e não blittable</span><span class="sxs-lookup"><span data-stu-id="c4f55-104">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="c4f55-105">A maioria dos tipos de dados tem uma representação comum na memória gerenciada e não gerenciada e não exige manipulação especial pelo marshaler de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="c4f55-105">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="c4f55-106">Esses tipos são chamados *tipos blittable* porque não exigem conversão quando são passados entre o código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c4f55-106">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="c4f55-107">Estruturas retornadas de chamadas de invocação de plataforma devem ser tipos blittable.</span><span class="sxs-lookup"><span data-stu-id="c4f55-107">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="c4f55-108">A invocação de plataforma não dá suporte a estruturas não blittable como tipos de retorno.</span><span class="sxs-lookup"><span data-stu-id="c4f55-108">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="c4f55-109">Os seguintes tipos do namespace <xref:System> são tipos blittable:</span><span class="sxs-lookup"><span data-stu-id="c4f55-109">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="c4f55-110">Os seguintes tipos complexos também são tipos blittable:</span><span class="sxs-lookup"><span data-stu-id="c4f55-110">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="c4f55-111">Matrizes unidimensionais de tipos blittable, como uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="c4f55-111">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="c4f55-112">No entanto, um tipo que contém uma matriz variável de tipos blittable não é blittable em si.</span><span class="sxs-lookup"><span data-stu-id="c4f55-112">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
- <span data-ttu-id="c4f55-113">Tipos de valor formatados que contêm somente tipos blittable (e classes, se elas tiverem o marshaling realizado como tipos formatados).</span><span class="sxs-lookup"><span data-stu-id="c4f55-113">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="c4f55-114">Para obter mais informações sobre os tipos de valor formatados, consulte [Marshaling padrão para tipos de valor](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="c4f55-114">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="c4f55-115">Referências de objeto não são blittable.</span><span class="sxs-lookup"><span data-stu-id="c4f55-115">Object references are not blittable.</span></span> <span data-ttu-id="c4f55-116">Isso inclui uma matriz de referências a objetos que são blittable por si mesmos.</span><span class="sxs-lookup"><span data-stu-id="c4f55-116">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="c4f55-117">Por exemplo, é possível definir uma estrutura blittable, mas não é possível definir um tipo blittable que contém uma matriz de referências a essas estruturas.</span><span class="sxs-lookup"><span data-stu-id="c4f55-117">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="c4f55-118">Como uma otimização, as matrizes de tipos blittable e as classes que contêm somente membros blittable são [fixadas](copying-and-pinning.md), em vez de copiadas durante o marshaling.</span><span class="sxs-lookup"><span data-stu-id="c4f55-118">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="c4f55-119">Esses tipos podem parecer como se tivessem o marshaling realizado como parâmetros de Entrada/Saída quando o chamador e o receptor estão no mesmo apartment.</span><span class="sxs-lookup"><span data-stu-id="c4f55-119">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="c4f55-120">No entanto, esses tipos, na verdade, têm o marshaling realizado como parâmetros de Entrada e é necessário aplicar os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> de você desejar realizar marshaling do argumento como um parâmetro de Entrada/Saída.</span><span class="sxs-lookup"><span data-stu-id="c4f55-120">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="c4f55-121">Alguns tipos de dados gerenciados exigem uma representação diferente em um ambiente não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c4f55-121">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="c4f55-122">Esses tipos de dados não blittable devem ser convertidos em um formato que pode ter o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="c4f55-122">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="c4f55-123">Por exemplo, cadeias de caracteres gerenciadas não são tipos blittable porque devem ser convertidas em objetos de cadeia de caracteres antes que possam ter o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="c4f55-123">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="c4f55-124">A tabela a seguir lista tipos não blittable do namespace <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="c4f55-124">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="c4f55-125">[Representantes](default-marshaling-behavior.md#default-marshaling-for-delegates), que são estruturas de dados que se referem a um método estático ou a uma instância de classe, também não são blittable.</span><span class="sxs-lookup"><span data-stu-id="c4f55-125">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="c4f55-126">Tipo não bittable</span><span class="sxs-lookup"><span data-stu-id="c4f55-126">Non-blittable type</span></span>|<span data-ttu-id="c4f55-127">Description</span><span class="sxs-lookup"><span data-stu-id="c4f55-127">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="c4f55-128">System.Array</span><span class="sxs-lookup"><span data-stu-id="c4f55-128">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="c4f55-129">Converte em uma matriz C-style ou em um `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="c4f55-129">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="c4f55-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c4f55-130">[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="c4f55-131">Converte em um valor de 1, 2 ou 4 bytes com `true` como 1 ou -1.</span><span class="sxs-lookup"><span data-stu-id="c4f55-131">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="c4f55-132">[System. Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c4f55-132">[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="c4f55-133">Converte em um caractere Unicode ou ANSI.</span><span class="sxs-lookup"><span data-stu-id="c4f55-133">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="c4f55-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c4f55-134">[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="c4f55-135">Converte em uma interface de classe.</span><span class="sxs-lookup"><span data-stu-id="c4f55-135">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="c4f55-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="c4f55-136">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="c4f55-137">Converte em uma variante ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="c4f55-137">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="c4f55-138">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="c4f55-138">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="c4f55-139">Converte em uma matriz C-style ou em um `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="c4f55-139">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="c4f55-140">System.String</span><span class="sxs-lookup"><span data-stu-id="c4f55-140">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="c4f55-141">Converte em uma cadeia de caracteres que termina em uma referência nula ou em um BSTR.</span><span class="sxs-lookup"><span data-stu-id="c4f55-141">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="c4f55-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c4f55-142">[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="c4f55-143">Converte em uma estrutura com um layout de memória fixo.</span><span class="sxs-lookup"><span data-stu-id="c4f55-143">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="c4f55-144">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="c4f55-144">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="c4f55-145">Converte em uma matriz C-style ou em um `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="c4f55-145">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="c4f55-146">Há suporte para tipos de objeto e de classe apenas na interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="c4f55-146">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="c4f55-147">Para tipos correspondentes no Visual Basic, C# e C++, consulte a [Visão geral da biblioteca de classes](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c4f55-147">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f55-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4f55-148">See also</span></span>

- [<span data-ttu-id="c4f55-149">Comportamento de marshaling padrão</span><span class="sxs-lookup"><span data-stu-id="c4f55-149">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
