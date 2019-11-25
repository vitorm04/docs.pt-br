---
title: Como criar uma C/C++ Union usando atributos ()C#
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: ff8ce560444581a28b257820573224f89a274cd9
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141578"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="293fd-102">Como criar uma C/C++ Union usando atributos ()C#</span><span class="sxs-lookup"><span data-stu-id="293fd-102">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="293fd-103">Usando atributos, você pode personalizar a forma como as estruturas são colocadas na memória.</span><span class="sxs-lookup"><span data-stu-id="293fd-103">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="293fd-104">Por exemplo, você pode criar o que é conhecido como uma união no C/C++ usando os atributos `StructLayout(LayoutKind.Explicit)` e `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="293fd-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="293fd-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="293fd-105">Example</span></span>

<span data-ttu-id="293fd-106">Neste segmento de código, todos os campos de `TestUnion` são iniciados no mesmo local na memória.</span><span class="sxs-lookup"><span data-stu-id="293fd-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="293fd-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="293fd-107">Example</span></span>

<span data-ttu-id="293fd-108">A seguir, temos outro exemplo em que os campos são iniciados em locais diferentes definidos explicitamente.</span><span class="sxs-lookup"><span data-stu-id="293fd-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="293fd-109">Os dois campos inteiros, `i1` e `i2`, compartilham os mesmos locais de memória que `lg`.</span><span class="sxs-lookup"><span data-stu-id="293fd-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="293fd-110">Esse tipo de controle sobre o layout do struct é útil ao usar a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="293fd-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="293fd-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="293fd-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="293fd-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="293fd-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="293fd-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="293fd-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="293fd-114">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="293fd-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="293fd-115">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="293fd-115">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="293fd-116">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="293fd-116">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="293fd-117">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="293fd-117">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
