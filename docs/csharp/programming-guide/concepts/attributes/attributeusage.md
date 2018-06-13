---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33955922"
---
# <a name="attributeusage-c"></a><span data-ttu-id="3818b-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="3818b-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="3818b-103">Determina como uma classe de atributo personalizado pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="3818b-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="3818b-104"><xref:System.AttributeUsageAttribute> é um atributo aplicado a definições de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="3818b-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="3818b-105">O atributo `AttributeUsage` permite que você controle:</span><span class="sxs-lookup"><span data-stu-id="3818b-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="3818b-106">A quais elementos do programa o atributo pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="3818b-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="3818b-107">A menos que você restrinja seu uso, um atributo pode ser aplicado a um dos seguintes elementos do programa:</span><span class="sxs-lookup"><span data-stu-id="3818b-107">Unless you restrict is usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="3818b-108">assembly</span><span class="sxs-lookup"><span data-stu-id="3818b-108">assembly</span></span>
  - <span data-ttu-id="3818b-109">module</span><span class="sxs-lookup"><span data-stu-id="3818b-109">module</span></span>
  - <span data-ttu-id="3818b-110">campo</span><span class="sxs-lookup"><span data-stu-id="3818b-110">field</span></span>
  - <span data-ttu-id="3818b-111">evento</span><span class="sxs-lookup"><span data-stu-id="3818b-111">event</span></span>
  - <span data-ttu-id="3818b-112">method</span><span class="sxs-lookup"><span data-stu-id="3818b-112">method</span></span>
  - <span data-ttu-id="3818b-113">param</span><span class="sxs-lookup"><span data-stu-id="3818b-113">param</span></span>
  - <span data-ttu-id="3818b-114">propriedade</span><span class="sxs-lookup"><span data-stu-id="3818b-114">property</span></span>
  - <span data-ttu-id="3818b-115">return</span><span class="sxs-lookup"><span data-stu-id="3818b-115">return</span></span>
  - <span data-ttu-id="3818b-116">tipo</span><span class="sxs-lookup"><span data-stu-id="3818b-116">type</span></span>
- <span data-ttu-id="3818b-117">Indica se um atributo pode ser aplicado a um único elemento do programa várias vezes.</span><span class="sxs-lookup"><span data-stu-id="3818b-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="3818b-118">Indica se os atributos são herdados por classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="3818b-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="3818b-119">As configurações padrão se parecem com o seguinte exemplo quando aplicadas explicitamente:</span><span class="sxs-lookup"><span data-stu-id="3818b-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="3818b-120">Neste exemplo, a classe `NewAttribute` pode ser aplicada a qualquer elemento de programa compatível.</span><span class="sxs-lookup"><span data-stu-id="3818b-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="3818b-121">Porém, ele pode ser aplicado apenas uma vez para cada entidade.</span><span class="sxs-lookup"><span data-stu-id="3818b-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="3818b-122">O atributo é herdado por classes derivadas quando aplicado a uma classe base.</span><span class="sxs-lookup"><span data-stu-id="3818b-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="3818b-123">Os argumentos <xref:System.AttributeUsageAttribute.AllowMultiple> e <xref:System.AttributeUsageAttribute.Inherited> são opcionais e, portanto, o seguinte código tem o mesmo efeito:</span><span class="sxs-lookup"><span data-stu-id="3818b-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="3818b-124">O primeiro argumento <xref:System.AttributeUsageAttribute> deve ser um ou mais elementos da enumeração <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="3818b-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="3818b-125">Vários tipos de destino podem ser vinculados junto com o operador OR, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="3818b-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="3818b-126">Do C# 7.3 em diante, os atributos podem ser aplicados à propriedade ou ao campo de suporte de uma propriedade autoimplementada.</span><span class="sxs-lookup"><span data-stu-id="3818b-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="3818b-127">O atributo se aplica à propriedade, a menos que você especifique o especificador `field` no atributo.</span><span class="sxs-lookup"><span data-stu-id="3818b-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="3818b-128">Ambos são mostrados no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="3818b-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="3818b-129">Se o argumento <xref:System.AttributeUsageAttribute.AllowMultiple> for `true`, o atributo resultante poderá ser aplicado mais de uma vez a uma única entidade, conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="3818b-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="3818b-130">Nesse caso, `MultiUseAttribute` pode ser aplicado repetidas vezes porque `AllowMultiple` está definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="3818b-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="3818b-131">Os dois formatos mostrados para a aplicação de vários atributos são válidos.</span><span class="sxs-lookup"><span data-stu-id="3818b-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="3818b-132">Se <xref:System.AttributeUsageAttribute.Inherited> for `false`, o atributo não será herdado por classes derivadas de uma classe atribuída.</span><span class="sxs-lookup"><span data-stu-id="3818b-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="3818b-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3818b-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="3818b-134">Nesse caso, `NonInheritedAttribute` não é aplicado a `DClass` por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="3818b-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="3818b-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="3818b-135">Remarks</span></span>

<span data-ttu-id="3818b-136">O atributo `AttributeUsage` é um atributo de uso único. Ele não pode ser aplicado mais de uma vez à mesma classe.</span><span class="sxs-lookup"><span data-stu-id="3818b-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="3818b-137">`AttributeUsage` é um alias para <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3818b-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="3818b-138">Para obter mais informações, consulte [Acessando atributos usando reflexão (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="3818b-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="3818b-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3818b-139">Example</span></span>

<span data-ttu-id="3818b-140">O exemplo a seguir demonstra o efeito dos argumentos <xref:System.AttributeUsageAttribute.Inherited> e <xref:System.AttributeUsageAttribute.AllowMultiple> no atributo <xref:System.AttributeUsageAttribute> e como os atributos personalizados aplicados a uma classe podem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="3818b-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="3818b-141">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="3818b-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="3818b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3818b-142">See Also</span></span>
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="3818b-143">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3818b-143">C# Programming Guide</span></span>](../..//index.md)  
 [<span data-ttu-id="3818b-144">Atributos</span><span class="sxs-lookup"><span data-stu-id="3818b-144">Attributes</span></span>](../../../..//standard/attributes/index.md)  
 [<span data-ttu-id="3818b-145">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="3818b-145">Reflection (C#)</span></span>](../reflection.md)  
 [<span data-ttu-id="3818b-146">Atributos</span><span class="sxs-lookup"><span data-stu-id="3818b-146">Attributes</span></span>](index.md)  
 [<span data-ttu-id="3818b-147">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="3818b-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
 [<span data-ttu-id="3818b-148">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="3818b-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
