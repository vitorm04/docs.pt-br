---
title: Como criar uma União C/C++ usando atributos (C#)
description: Saiba como usar atributos para personalizar como as estruturas são colocadas na memória em C#. Este exemplo implementa o equivalente de uma União de C/C++.
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 766a070105441630dfd8fecf7b9f68fa6818fe50
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925066"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="05241-104">Como criar uma União C/C++ usando atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="05241-104">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="05241-105">Usando atributos, você pode personalizar a forma como as estruturas são colocadas na memória.</span><span class="sxs-lookup"><span data-stu-id="05241-105">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="05241-106">Por exemplo, você pode criar o que é conhecido como uma união no C/C++ usando os atributos `StructLayout(LayoutKind.Explicit)` e `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="05241-106">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="05241-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05241-107">Example</span></span>

<span data-ttu-id="05241-108">Neste segmento de código, todos os campos de `TestUnion` são iniciados no mesmo local na memória.</span><span class="sxs-lookup"><span data-stu-id="05241-108">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestUnion
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public byte b;
}
```

## <a name="example"></a><span data-ttu-id="05241-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05241-109">Example</span></span>

<span data-ttu-id="05241-110">A seguir, temos outro exemplo em que os campos são iniciados em locais diferentes definidos explicitamente.</span><span class="sxs-lookup"><span data-stu-id="05241-110">The following is another example where fields start at different explicitly set locations.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestExplicit
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public long lg;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i1;

    [System.Runtime.InteropServices.FieldOffset(4)]
    public int i2;

    [System.Runtime.InteropServices.FieldOffset(8)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(12)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(14)]
    public byte b;
}
```

<span data-ttu-id="05241-111">Os dois campos inteiros, `i1` e `i2`, compartilham os mesmos locais de memória que `lg`.</span><span class="sxs-lookup"><span data-stu-id="05241-111">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="05241-112">Esse tipo de controle sobre o layout do struct é útil ao usar a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="05241-112">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="05241-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="05241-113">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="05241-114">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="05241-114">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="05241-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="05241-115">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="05241-116">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="05241-116">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="05241-117">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="05241-117">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="05241-118">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="05241-118">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="05241-119">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="05241-119">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
