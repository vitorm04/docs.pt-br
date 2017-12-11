---
title: AttributeUsage (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e9351ee10b523145ace1249bf17388da0cdba277
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="attributeusage-c"></a><span data-ttu-id="91cad-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="91cad-102">AttributeUsage (C#)</span></span>
<span data-ttu-id="91cad-103">Determina como uma classe de atributo personalizado pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="91cad-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="91cad-104">`AttributeUsage` é um atributo que pode ser aplicado às definições de atributo personalizado para controlar como o novo atributo pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="91cad-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="91cad-105">As configurações padrão têm essa aparência quando aplicadas explicitamente:</span><span class="sxs-lookup"><span data-stu-id="91cad-105">The default settings look like this when applied explicitly:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="91cad-106">Neste exemplo, a classe `NewAttribute` pode ser aplicada a qualquer entidade de código capaz de receber atributo, mas pode ser aplicadas apenas uma vez para cada entidade.</span><span class="sxs-lookup"><span data-stu-id="91cad-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="91cad-107">Ela é herdada por classes derivadas quando aplicada a uma classe base.</span><span class="sxs-lookup"><span data-stu-id="91cad-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="91cad-108">Os argumentos `AllowMultiple` e `Inherited` são opcionais, portanto, esse código tem o mesmo efeito:</span><span class="sxs-lookup"><span data-stu-id="91cad-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="91cad-109">O primeiro argumento `AttributeUsage` deve ser um ou mais elementos da enumeração <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="91cad-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="91cad-110">Vários tipos de destino podem ser vinculados junto com o operador OR, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="91cad-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 <span data-ttu-id="91cad-111">Se o argumento `AllowMultiple` for definido como `true`, o atributo resultante poderá ser aplicado mais de uma vez a uma única entidade, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="91cad-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 <span data-ttu-id="91cad-112">Nesse caso `MultiUseAttr` pode ser aplicado repetidas vezes porque `AllowMultiple` está definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="91cad-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="91cad-113">Os dois formatos mostrados para a aplicação de vários atributos são válidos.</span><span class="sxs-lookup"><span data-stu-id="91cad-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="91cad-114">Se `Inherited` for definido como `false`, o atributo não será herdado por classes derivadas de uma classe que é atribuída.</span><span class="sxs-lookup"><span data-stu-id="91cad-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="91cad-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91cad-115">For example:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 <span data-ttu-id="91cad-116">Nesse caso `Attr1` não é aplicado a `DClass` por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="91cad-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91cad-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="91cad-117">Remarks</span></span>  
 <span data-ttu-id="91cad-118">O atributo `AttributeUsage` é um atributo de uso único. Ele não pode ser aplicado mais de uma vez para a mesma classe.</span><span class="sxs-lookup"><span data-stu-id="91cad-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="91cad-119">`AttributeUsage` é um alias para <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="91cad-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="91cad-120">Para obter mais informações, consulte [Acessando atributos usando reflexão (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="91cad-120">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="91cad-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91cad-121">Example</span></span>  
 <span data-ttu-id="91cad-122">O exemplo a seguir demonstra o efeito dos argumentos `Inherited` e `AllowMultiple` no atributo `AttributeUsage` e como os atributos personalizados aplicados a uma classe podem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="91cad-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
```  
  
## <a name="sample-output"></a><span data-ttu-id="91cad-123">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="91cad-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="91cad-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91cad-124">See Also</span></span>  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="91cad-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="91cad-125">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="91cad-126">Atributos</span><span class="sxs-lookup"><span data-stu-id="91cad-126">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="91cad-127">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="91cad-127">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="91cad-128">Atributos</span><span class="sxs-lookup"><span data-stu-id="91cad-128">Attributes</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="91cad-129">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="91cad-129">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="91cad-130">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="91cad-130">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
