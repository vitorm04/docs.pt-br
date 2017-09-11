---
title: "Restringindo a acessibilidade ao acessador (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: 26
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
ms.openlocfilehash: 347fffa4f612c5cb674a6529e46c0b1785670c95
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="9706c-102">Restringindo a acessibilidade ao acessador (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9706c-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="9706c-103">As partes [get](../../../csharp/language-reference/keywords/get.md) e [set](../../../csharp/language-reference/keywords/set.md) de uma propriedade ou de um indexador são chamadas *acessadores*.</span><span class="sxs-lookup"><span data-stu-id="9706c-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="9706c-104">Por padrão, esses acessadores têm a mesma visibilidade ou nível de acesso: a da propriedade ou do indexador aos quais eles pertencem.</span><span class="sxs-lookup"><span data-stu-id="9706c-104">By default these accessors have the same visibility, or access level: that of the property or indexer to which they belong.</span></span> <span data-ttu-id="9706c-105">Para obter mais informações, consulte [níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9706c-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="9706c-106">No entanto, às vezes é útil restringir o acesso a um desses acessadores.</span><span class="sxs-lookup"><span data-stu-id="9706c-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="9706c-107">Normalmente, isso envolve restringir a acessibilidade do acessador `set` e manter o acessador `get` publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="9706c-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="9706c-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9706c-108">For example:</span></span>  
  
 <span data-ttu-id="9706c-109">[!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9706c-109">[!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]</span></span>  
  
 <span data-ttu-id="9706c-110">Neste exemplo, uma propriedade chamada `Name` define um acessador `get` e `set`.</span><span class="sxs-lookup"><span data-stu-id="9706c-110">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="9706c-111">O acessador `get` recebe o nível de acessibilidade da propriedade em si, `public` nesse caso, embora o `set` acessador esteja restrito explicitamente ao aplicar o modificador de acesso [protegido](../../../csharp/language-reference/keywords/protected.md) ao acessador em si.</span><span class="sxs-lookup"><span data-stu-id="9706c-111">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="9706c-112">Restrições em modificadores de acesso nos acessadores</span><span class="sxs-lookup"><span data-stu-id="9706c-112">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="9706c-113">O uso dos modificadores de acesso em propriedades ou indexadores está sujeito a estas condições:</span><span class="sxs-lookup"><span data-stu-id="9706c-113">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="9706c-114">Não é possível usar os modificadores de acessador em uma interface ou em uma implementação de membro de [interface](../../../csharp/language-reference/keywords/interface.md) explícita.</span><span class="sxs-lookup"><span data-stu-id="9706c-114">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="9706c-115">É possível usar os modificadores de acessador somente se a propriedade ou o indexador tiver os acessadores `set` e `get`.</span><span class="sxs-lookup"><span data-stu-id="9706c-115">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="9706c-116">Nesse caso, o modificador é permitido em apenas um dos dois acessadores.</span><span class="sxs-lookup"><span data-stu-id="9706c-116">In this case, the modifier is permitted on one only of the two accessors.</span></span>  
  
-   <span data-ttu-id="9706c-117">Se a propriedade ou o indexador tiver um modificador [substituir](../../../csharp/language-reference/keywords/override.md), o modificador de acessador deverá corresponder o acessador do acessador substituído, se houver.</span><span class="sxs-lookup"><span data-stu-id="9706c-117">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="9706c-118">O nível de acessibilidade do acessador deve ser mais restritivo do que o nível de acessibilidade na propriedade ou no indexador em si.</span><span class="sxs-lookup"><span data-stu-id="9706c-118">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="9706c-119">Modificadores de acesso em acessadores de substituição</span><span class="sxs-lookup"><span data-stu-id="9706c-119">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="9706c-120">Quando você substitui uma propriedade ou indexador, os acessadores substituídos devem estar acessíveis ao código de substituição.</span><span class="sxs-lookup"><span data-stu-id="9706c-120">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="9706c-121">Além disso, o nível de acessibilidade da propriedade/indexador e o dos acessadores devem corresponder à propriedade/indexador substituído e aos acessadores.</span><span class="sxs-lookup"><span data-stu-id="9706c-121">Also, the accessibility level of both the property/indexer, and that of the accessors must match the corresponding overridden property/indexer and the accessors.</span></span> <span data-ttu-id="9706c-122">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9706c-122">For example:</span></span>  
  
 <span data-ttu-id="9706c-123">[!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9706c-123">[!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]</span></span>  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="9706c-124">Implementando interfaces</span><span class="sxs-lookup"><span data-stu-id="9706c-124">Implementing Interfaces</span></span>  
 <span data-ttu-id="9706c-125">Quando você usa um acessador para implementar uma interface, o acessador pode não ter um modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="9706c-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="9706c-126">No entanto, se você implementar a interface usando um acessador, como `get`, o outro acessador poderá ter um modificador de acesso, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9706c-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 <span data-ttu-id="9706c-127">[!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9706c-127">[!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]</span></span>  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="9706c-128">Domínio de acessibilidade do acessador</span><span class="sxs-lookup"><span data-stu-id="9706c-128">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="9706c-129">Se você usar um modificador de acesso no acessador, o [domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md) do acessador será determinado por esse modificador.</span><span class="sxs-lookup"><span data-stu-id="9706c-129">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="9706c-130">Se você não usou um modificador de acesso no acessador, o domínio de acessibilidade do acessador é determinado pelo nível de acessibilidade da propriedade ou do indexador.</span><span class="sxs-lookup"><span data-stu-id="9706c-130">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9706c-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9706c-131">Example</span></span>  
 <span data-ttu-id="9706c-132">O exemplo a seguir contém três classes, `BaseClass`, `DerivedClass` e `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="9706c-132">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="9706c-133">Há duas propriedades no `BaseClass`, `Name` e `Id` em ambas as classes.</span><span class="sxs-lookup"><span data-stu-id="9706c-133">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="9706c-134">O exemplo demonstra como a propriedade `Id` no `DerivedClass` pode ser oculta pela propriedade `Id` no `BaseClass` quando você usa um modificador de acesso restritivo como [protegido](../../../csharp/language-reference/keywords/protected.md) ou [privado](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="9706c-134">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="9706c-135">Portanto, em vez disso, quando você atribui valores a essa propriedade, a propriedade na classe `BaseClass` é chamada.</span><span class="sxs-lookup"><span data-stu-id="9706c-135">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="9706c-136">Substituindo o modificador de acesso por [público](../../../csharp/language-reference/keywords/public.md) tornará a propriedade acessível.</span><span class="sxs-lookup"><span data-stu-id="9706c-136">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="9706c-137">O exemplo também demonstra que um modificador de acesso restritivo, como `private` ou `protected`, no acessador `set` da propriedade `Name` no `DerivedClass` impede o acesso ao acessador e gera um erro quando você atribui a ele.</span><span class="sxs-lookup"><span data-stu-id="9706c-137">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 <span data-ttu-id="9706c-138">[!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9706c-138">[!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]</span></span>  
  
## <a name="comments"></a><span data-ttu-id="9706c-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="9706c-139">Comments</span></span>  
 <span data-ttu-id="9706c-140">Observe que, se você substituir a declaração `new private string Id` por `new public string Id`, você obterá a saída:</span><span class="sxs-lookup"><span data-stu-id="9706c-140">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="9706c-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9706c-141">See Also</span></span>  
 <span data-ttu-id="9706c-142">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9706c-142">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9706c-143">[Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="9706c-143">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 <span data-ttu-id="9706c-144">[Indexadores](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="9706c-144">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 [<span data-ttu-id="9706c-145">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="9706c-145">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)

