---
title: "Executando a conversão boxing de tipos anuláveis (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ce063a70ced98fd8b99b4b46d704e08ddc96e10
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="315e5-102">Executando a conversão boxing de tipos anuláveis (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="315e5-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="315e5-103">Objetos baseados em tipos que permitem valor nulo serão convertidos somente se o objeto não for nulo.</span><span class="sxs-lookup"><span data-stu-id="315e5-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="315e5-104">Se <xref:System.Nullable%601.HasValue%2A> for `false`, a referência do objeto será atribuída a `null`, em vez da conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="315e5-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="315e5-105">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="315e5-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="315e5-106">Se o objeto for não nulo – se <xref:System.Nullable%601.HasValue%2A> for `true` –, então, a conversão boxing ocorrerá, mas somente o tipo subjacente no qual o objeto anulável é baseado será convertido.</span><span class="sxs-lookup"><span data-stu-id="315e5-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="315e5-107">A conversão boxing de um tipo de valor anulável não nulo demarca o próprio tipo de valor e não o <xref:System.Nullable%601?displayProperty=fullName> que encapsula o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="315e5-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=fullName> that wraps the value type.</span></span> <span data-ttu-id="315e5-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="315e5-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="315e5-109">Os dois objetos convertidos são idênticos àqueles criados por meio da conversão boxing de tipos tipo que não permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="315e5-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="315e5-110">Assim como os tipos que não permitem valor nulo convertidos, eles podem ser desconvertidos para tipos que permitem valor nulo, conforme o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="315e5-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="315e5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="315e5-111">Remarks</span></span>  
 <span data-ttu-id="315e5-112">O comportamento de tipos que permitem valor nulo convertidos oferece duas vantagens:</span><span class="sxs-lookup"><span data-stu-id="315e5-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="315e5-113">Objetos anuláveis e seus correspondentes convertidos podem ser testados como nulos:</span><span class="sxs-lookup"><span data-stu-id="315e5-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
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
  
2.  <span data-ttu-id="315e5-114">Tipos convertidos que permitem valor nulo oferecem suporte total à funcionalidade do tipo subjacente:</span><span class="sxs-lookup"><span data-stu-id="315e5-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="315e5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="315e5-115">See Also</span></span>  
 <span data-ttu-id="315e5-116">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="315e5-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="315e5-117">[Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="315e5-117">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="315e5-118">Como identificar um tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="315e5-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)

