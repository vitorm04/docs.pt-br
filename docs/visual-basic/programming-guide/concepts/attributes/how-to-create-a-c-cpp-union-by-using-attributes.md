---
title: 'Como: criar uma C-C++ Union usando atributos (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: 6595d6477d9d0838745e19eb2a44d26f6e534c70
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524264"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="a7486-102">Como: criar uma C/C++ Union usando atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7486-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="a7486-103">Usando atributos, você pode personalizar como structs são dispostos na memória.</span><span class="sxs-lookup"><span data-stu-id="a7486-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="a7486-104">Por exemplo, você pode criar o que é conhecido como uma união no C/C++ usando os atributos `StructLayout(LayoutKind.Explicit)` e `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="a7486-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="a7486-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7486-105">Example</span></span>

<span data-ttu-id="a7486-106">Neste segmento de código, todos os campos de `TestUnion` são iniciados no mesmo local na memória.</span><span class="sxs-lookup"><span data-stu-id="a7486-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a><span data-ttu-id="a7486-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7486-107">Example</span></span>

<span data-ttu-id="a7486-108">A seguir, temos outro exemplo em que os campos são iniciados em locais diferentes definidos explicitamente.</span><span class="sxs-lookup"><span data-stu-id="a7486-108">The following is another example where fields start at different explicitly set locations.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

<span data-ttu-id="a7486-109">Os dois campos inteiros, `i1` e `i2`, compartilham os mesmos locais de memória que `lg`.</span><span class="sxs-lookup"><span data-stu-id="a7486-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="a7486-110">Esse tipo de controle sobre o layout do struct é útil ao usar a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="a7486-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7486-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7486-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="a7486-112">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7486-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="a7486-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a7486-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="a7486-114">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7486-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="a7486-115">Atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7486-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="a7486-116">Criando atributos personalizados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7486-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="a7486-117">Acessando atributos usando reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7486-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
