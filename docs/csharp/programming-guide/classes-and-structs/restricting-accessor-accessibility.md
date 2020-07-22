---
title: Como restringir a acessibilidade ao acessador – Guia de Programação em C#
description: Os acessadores get e set de uma propriedade em C# têm a mesma visibilidade ou nível de acesso, por padrão, como Propriedade à qual pertencem. Você pode restringir o acesso.
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: 18fd1d58dc6125b5180118b2e0d3edc885a4b971
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863962"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="c57ba-104">Restringindo a acessibilidade ao acessador (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c57ba-104">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="c57ba-105">As partes [get](../../language-reference/keywords/get.md) e [set](../../language-reference/keywords/set.md) de uma propriedade ou de um indexador são chamadas *acessadores*.</span><span class="sxs-lookup"><span data-stu-id="c57ba-105">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="c57ba-106">Por padrão, esses acessadores têm a mesma visibilidade ou nível de acesso da propriedade ou do indexador aos quais pertencem.</span><span class="sxs-lookup"><span data-stu-id="c57ba-106">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="c57ba-107">Para obter mais informações, consulte [níveis de acessibilidade](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c57ba-107">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="c57ba-108">No entanto, às vezes é útil restringir o acesso a um desses acessadores.</span><span class="sxs-lookup"><span data-stu-id="c57ba-108">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="c57ba-109">Normalmente, isso envolve restringir a acessibilidade do acessador `set` e manter o acessador `get` publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="c57ba-109">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="c57ba-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c57ba-110">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="c57ba-111">Neste exemplo, uma propriedade chamada `Name` define um acessador `get` e `set`.</span><span class="sxs-lookup"><span data-stu-id="c57ba-111">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="c57ba-112">O acessador `get` recebe o nível de acessibilidade da propriedade em si, `public` nesse caso, embora o `set` acessador esteja restrito explicitamente ao aplicar o modificador de acesso [protegido](../../language-reference/keywords/protected.md) ao acessador em si.</span><span class="sxs-lookup"><span data-stu-id="c57ba-112">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="c57ba-113">Restrições em modificadores de acesso nos acessadores</span><span class="sxs-lookup"><span data-stu-id="c57ba-113">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="c57ba-114">O uso dos modificadores de acesso em propriedades ou indexadores está sujeito a estas condições:</span><span class="sxs-lookup"><span data-stu-id="c57ba-114">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="c57ba-115">Não é possível usar os modificadores de acessador em uma interface ou em uma implementação de membro de [interface](../../language-reference/keywords/interface.md) explícita.</span><span class="sxs-lookup"><span data-stu-id="c57ba-115">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="c57ba-116">É possível usar os modificadores de acessador somente se a propriedade ou o indexador tiver os acessadores `set` e `get`.</span><span class="sxs-lookup"><span data-stu-id="c57ba-116">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="c57ba-117">Nesse caso, o modificador é permitido em apenas um dos dois acessadores.</span><span class="sxs-lookup"><span data-stu-id="c57ba-117">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="c57ba-118">Se a propriedade ou o indexador tiver um modificador [substituir](../../language-reference/keywords/override.md), o modificador de acessador deverá corresponder o acessador do acessador substituído, se houver.</span><span class="sxs-lookup"><span data-stu-id="c57ba-118">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="c57ba-119">O nível de acessibilidade do acessador deve ser mais restritivo do que o nível de acessibilidade na propriedade ou no indexador em si.</span><span class="sxs-lookup"><span data-stu-id="c57ba-119">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="c57ba-120">Modificadores de acesso em acessadores de substituição</span><span class="sxs-lookup"><span data-stu-id="c57ba-120">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="c57ba-121">Quando você substitui uma propriedade ou indexador, os acessadores substituídos devem estar acessíveis ao código de substituição.</span><span class="sxs-lookup"><span data-stu-id="c57ba-121">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="c57ba-122">Além disso, a acessibilidade da propriedade/indexador, e seus acessadores, devem corresponder à propriedade/indexador substituído e seus acessadores.</span><span class="sxs-lookup"><span data-stu-id="c57ba-122">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="c57ba-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c57ba-123">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="c57ba-124">Implementando interfaces</span><span class="sxs-lookup"><span data-stu-id="c57ba-124">Implementing Interfaces</span></span>  
 <span data-ttu-id="c57ba-125">Quando você usa um acessador para implementar uma interface, o acessador pode não ter um modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="c57ba-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="c57ba-126">No entanto, se você implementar a interface usando um acessador, como `get`, o outro acessador poderá ter um modificador de acesso, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c57ba-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="c57ba-127">Domínio de acessibilidade do acessador</span><span class="sxs-lookup"><span data-stu-id="c57ba-127">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="c57ba-128">Se você usar um modificador de acesso no acessador, o [domínio de acessibilidade](../../language-reference/keywords/accessibility-domain.md) do acessador será determinado por esse modificador.</span><span class="sxs-lookup"><span data-stu-id="c57ba-128">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="c57ba-129">Se você não usou um modificador de acesso no acessador, o domínio de acessibilidade do acessador é determinado pelo nível de acessibilidade da propriedade ou do indexador.</span><span class="sxs-lookup"><span data-stu-id="c57ba-129">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c57ba-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c57ba-130">Example</span></span>  
 <span data-ttu-id="c57ba-131">O exemplo a seguir contém três classes, `BaseClass`, `DerivedClass` e `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="c57ba-131">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="c57ba-132">Há duas propriedades no `BaseClass`, `Name` e `Id` em ambas as classes.</span><span class="sxs-lookup"><span data-stu-id="c57ba-132">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="c57ba-133">O exemplo demonstra como a propriedade `Id` no `DerivedClass` pode ser oculta pela propriedade `Id` no `BaseClass` quando você usa um modificador de acesso restritivo como [protegido](../../language-reference/keywords/protected.md) ou [privado](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="c57ba-133">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="c57ba-134">Portanto, em vez disso, quando você atribui valores a essa propriedade, a propriedade na classe `BaseClass` é chamada.</span><span class="sxs-lookup"><span data-stu-id="c57ba-134">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="c57ba-135">Substituindo o modificador de acesso por [público](../../language-reference/keywords/public.md) tornará a propriedade acessível.</span><span class="sxs-lookup"><span data-stu-id="c57ba-135">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="c57ba-136">O exemplo também demonstra que um modificador de acesso restritivo, como `private` ou `protected`, no acessador `set` da propriedade `Name` no `DerivedClass` impede o acesso ao acessador e gera um erro quando você atribui a ele.</span><span class="sxs-lookup"><span data-stu-id="c57ba-136">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="c57ba-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="c57ba-137">Comments</span></span>  
 <span data-ttu-id="c57ba-138">Observe que, se você substituir a declaração `new private string Id` por `new public string Id`, você obterá a saída:</span><span class="sxs-lookup"><span data-stu-id="c57ba-138">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="c57ba-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="c57ba-139">See also</span></span>

- [<span data-ttu-id="c57ba-140">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="c57ba-140">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c57ba-141">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c57ba-141">Properties</span></span>](./properties.md)
- [<span data-ttu-id="c57ba-142">Indexadores</span><span class="sxs-lookup"><span data-stu-id="c57ba-142">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="c57ba-143">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="c57ba-143">Access Modifiers</span></span>](./access-modifiers.md)
