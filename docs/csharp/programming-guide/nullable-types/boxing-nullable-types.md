---
title: Executando a conversão boxing de tipos anuláveis (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334750"
---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="7ee85-102">Executando a conversão boxing de tipos anuláveis (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="7ee85-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="7ee85-103">Objetos baseados em tipos que permitem valor nulo serão convertidos somente se o objeto não for nulo.</span><span class="sxs-lookup"><span data-stu-id="7ee85-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="7ee85-104">Se <xref:System.Nullable%601.HasValue%2A> for `false`, a referência do objeto será atribuída a `null`, em vez da conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="7ee85-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="7ee85-105">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7ee85-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="7ee85-106">Se o objeto for não nulo – se <xref:System.Nullable%601.HasValue%2A> for `true` –, então, a conversão boxing ocorrerá, mas somente o tipo subjacente no qual o objeto anulável é baseado será convertido.</span><span class="sxs-lookup"><span data-stu-id="7ee85-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="7ee85-107">A conversão boxing de um tipo de valor anulável não nulo demarca o próprio tipo de valor e não o <xref:System.Nullable%601?displayProperty=nameWithType> que encapsula o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="7ee85-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=nameWithType> that wraps the value type.</span></span> <span data-ttu-id="7ee85-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7ee85-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="7ee85-109">Os dois objetos convertidos são idênticos àqueles criados por meio da conversão boxing de tipos tipo que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="7ee85-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="7ee85-110">Assim como os tipos que não permitem valor nulo convertidos, eles podem ser desconvertidos para tipos que permitem valor nulo, conforme o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7ee85-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="7ee85-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ee85-111">Remarks</span></span>  
 <span data-ttu-id="7ee85-112">O comportamento de tipos que permitem valor nulo convertidos oferece duas vantagens:</span><span class="sxs-lookup"><span data-stu-id="7ee85-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="7ee85-113">Objetos anuláveis e seus correspondentes convertidos podem ser testados como nulos:</span><span class="sxs-lookup"><span data-stu-id="7ee85-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  <span data-ttu-id="7ee85-114">Tipos convertidos que permitem valor nulo oferecem suporte total à funcionalidade do tipo subjacente:</span><span class="sxs-lookup"><span data-stu-id="7ee85-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7ee85-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ee85-115">See Also</span></span>  
 [<span data-ttu-id="7ee85-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7ee85-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7ee85-117">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="7ee85-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="7ee85-118">Como identificar um tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="7ee85-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
