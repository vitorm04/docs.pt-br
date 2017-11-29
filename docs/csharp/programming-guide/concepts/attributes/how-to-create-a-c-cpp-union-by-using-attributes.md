---
title: "Como criar uma união do C/C++ usando atributos (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 450fb922079ca6737b8db7754f25435b9c3b884b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="2a41f-102">Como criar uma união do C-C++ usando atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="2a41f-102">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>
<span data-ttu-id="2a41f-103">Usando atributos, você pode personalizar como structs são dispostos na memória.</span><span class="sxs-lookup"><span data-stu-id="2a41f-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="2a41f-104">Por exemplo, você pode criar o que é conhecido como uma união no C/C++ usando os atributos `StructLayout(LayoutKind.Explicit)` e `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="2a41f-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a41f-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a41f-105">Example</span></span>  
 <span data-ttu-id="2a41f-106">Neste segmento de código, todos os campos de `TestUnion` são iniciados no mesmo local na memória.</span><span class="sxs-lookup"><span data-stu-id="2a41f-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2a41f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a41f-107">Example</span></span>  
 <span data-ttu-id="2a41f-108">A seguir, temos outro exemplo em que os campos são iniciados em locais diferentes definidos explicitamente.</span><span class="sxs-lookup"><span data-stu-id="2a41f-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="2a41f-109">Os dois campos inteiros, `i1` e `i2`, compartilham os mesmos locais de memória que `lg`.</span><span class="sxs-lookup"><span data-stu-id="2a41f-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="2a41f-110">Esse tipo de controle sobre o layout do struct é útil ao usar a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="2a41f-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a41f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a41f-111">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="2a41f-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2a41f-112">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2a41f-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a41f-113">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="2a41f-114">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="2a41f-114">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="2a41f-115">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="2a41f-115">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="2a41f-116">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="2a41f-116">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="2a41f-117">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="2a41f-117">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
