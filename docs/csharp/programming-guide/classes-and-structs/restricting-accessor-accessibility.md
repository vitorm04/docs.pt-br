---
title: Como restringir a acessibilidade ao acessador – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: c15b4939306b79f843b22dc808d88bf3d20ed555
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203698"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="36cf5-102">Restringindo a acessibilidade ao acessador (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="36cf5-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="36cf5-103">As partes [get](../../../csharp/language-reference/keywords/get.md) e [set](../../../csharp/language-reference/keywords/set.md) de uma propriedade ou de um indexador são chamadas *acessadores*.</span><span class="sxs-lookup"><span data-stu-id="36cf5-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="36cf5-104">Por padrão, esses acessadores têm a mesma visibilidade ou nível de acesso da propriedade ou do indexador aos quais pertencem.</span><span class="sxs-lookup"><span data-stu-id="36cf5-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="36cf5-105">Para obter mais informações, consulte [níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="36cf5-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="36cf5-106">No entanto, às vezes é útil restringir o acesso a um desses acessadores.</span><span class="sxs-lookup"><span data-stu-id="36cf5-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="36cf5-107">Normalmente, isso envolve restringir a acessibilidade do acessador `set` e manter o acessador `get` publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="36cf5-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="36cf5-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="36cf5-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="36cf5-109">Neste exemplo, uma propriedade chamada `Name` define um acessador `get` e `set`.</span><span class="sxs-lookup"><span data-stu-id="36cf5-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="36cf5-110">O acessador `get` recebe o nível de acessibilidade da propriedade em si, `public` nesse caso, embora o `set` acessador esteja restrito explicitamente ao aplicar o modificador de acesso [protegido](../../../csharp/language-reference/keywords/protected.md) ao acessador em si.</span><span class="sxs-lookup"><span data-stu-id="36cf5-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="36cf5-111">Restrições em modificadores de acesso nos acessadores</span><span class="sxs-lookup"><span data-stu-id="36cf5-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="36cf5-112">O uso dos modificadores de acesso em propriedades ou indexadores está sujeito a estas condições:</span><span class="sxs-lookup"><span data-stu-id="36cf5-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="36cf5-113">Não é possível usar os modificadores de acessador em uma interface ou em uma implementação de membro de [interface](../../../csharp/language-reference/keywords/interface.md) explícita.</span><span class="sxs-lookup"><span data-stu-id="36cf5-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="36cf5-114">É possível usar os modificadores de acessador somente se a propriedade ou o indexador tiver os acessadores `set` e `get`.</span><span class="sxs-lookup"><span data-stu-id="36cf5-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="36cf5-115">Nesse caso, o modificador é permitido em apenas um dos dois acessadores.</span><span class="sxs-lookup"><span data-stu-id="36cf5-115">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
-   <span data-ttu-id="36cf5-116">Se a propriedade ou o indexador tiver um modificador [substituir](../../../csharp/language-reference/keywords/override.md), o modificador de acessador deverá corresponder o acessador do acessador substituído, se houver.</span><span class="sxs-lookup"><span data-stu-id="36cf5-116">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="36cf5-117">O nível de acessibilidade do acessador deve ser mais restritivo do que o nível de acessibilidade na propriedade ou no indexador em si.</span><span class="sxs-lookup"><span data-stu-id="36cf5-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="36cf5-118">Modificadores de acesso em acessadores de substituição</span><span class="sxs-lookup"><span data-stu-id="36cf5-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="36cf5-119">Quando você substitui uma propriedade ou indexador, os acessadores substituídos devem estar acessíveis ao código de substituição.</span><span class="sxs-lookup"><span data-stu-id="36cf5-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="36cf5-120">Além disso, a acessibilidade da propriedade/indexador, e seus acessadores, devem corresponder à propriedade/indexador substituído e seus acessadores.</span><span class="sxs-lookup"><span data-stu-id="36cf5-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="36cf5-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="36cf5-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="36cf5-122">Implementando interfaces</span><span class="sxs-lookup"><span data-stu-id="36cf5-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="36cf5-123">Quando você usa um acessador para implementar uma interface, o acessador pode não ter um modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="36cf5-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="36cf5-124">No entanto, se você implementar a interface usando um acessador, como `get`, o outro acessador poderá ter um modificador de acesso, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="36cf5-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="36cf5-125">Domínio de acessibilidade do acessador</span><span class="sxs-lookup"><span data-stu-id="36cf5-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="36cf5-126">Se você usar um modificador de acesso no acessador, o [domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md) do acessador será determinado por esse modificador.</span><span class="sxs-lookup"><span data-stu-id="36cf5-126">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="36cf5-127">Se você não usou um modificador de acesso no acessador, o domínio de acessibilidade do acessador é determinado pelo nível de acessibilidade da propriedade ou do indexador.</span><span class="sxs-lookup"><span data-stu-id="36cf5-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36cf5-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36cf5-128">Example</span></span>  
 <span data-ttu-id="36cf5-129">O exemplo a seguir contém três classes, `BaseClass`, `DerivedClass` e `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="36cf5-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="36cf5-130">Há duas propriedades no `BaseClass`, `Name` e `Id` em ambas as classes.</span><span class="sxs-lookup"><span data-stu-id="36cf5-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="36cf5-131">O exemplo demonstra como a propriedade `Id` no `DerivedClass` pode ser oculta pela propriedade `Id` no `BaseClass` quando você usa um modificador de acesso restritivo como [protegido](../../../csharp/language-reference/keywords/protected.md) ou [privado](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="36cf5-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="36cf5-132">Portanto, em vez disso, quando você atribui valores a essa propriedade, a propriedade na classe `BaseClass` é chamada.</span><span class="sxs-lookup"><span data-stu-id="36cf5-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="36cf5-133">Substituindo o modificador de acesso por [público](../../../csharp/language-reference/keywords/public.md) tornará a propriedade acessível.</span><span class="sxs-lookup"><span data-stu-id="36cf5-133">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="36cf5-134">O exemplo também demonstra que um modificador de acesso restritivo, como `private` ou `protected`, no acessador `set` da propriedade `Name` no `DerivedClass` impede o acesso ao acessador e gera um erro quando você atribui a ele.</span><span class="sxs-lookup"><span data-stu-id="36cf5-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="36cf5-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="36cf5-135">Comments</span></span>  
 <span data-ttu-id="36cf5-136">Observe que, se você substituir a declaração `new private string Id` por `new public string Id`, você obterá a saída:</span><span class="sxs-lookup"><span data-stu-id="36cf5-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="36cf5-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36cf5-137">See also</span></span>

- [<span data-ttu-id="36cf5-138">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="36cf5-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="36cf5-139">Propriedades</span><span class="sxs-lookup"><span data-stu-id="36cf5-139">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="36cf5-140">Indexadores</span><span class="sxs-lookup"><span data-stu-id="36cf5-140">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="36cf5-141">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="36cf5-141">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
