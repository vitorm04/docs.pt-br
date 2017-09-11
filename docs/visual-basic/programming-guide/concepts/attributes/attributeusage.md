---
title: AttributeUsage (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c91f2686a03d2590e1aaf166d27c49744bb13c9b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="6fe38-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fe38-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="6fe38-103">Determina como uma classe de atributo personalizado pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="6fe38-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="6fe38-104">`AttributeUsage`é um atributo que pode ser aplicado às definições de atributo personalizado para controlar como o novo atributo pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="6fe38-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="6fe38-105">As configurações padrão assim quando aplicado explicitamente:</span><span class="sxs-lookup"><span data-stu-id="6fe38-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="6fe38-106">Neste exemplo, a `NewAttribute` classe pode ser aplicada a qualquer entidade de código capaz de atributo, mas podem ser aplicadas apenas uma vez para cada entidade.</span><span class="sxs-lookup"><span data-stu-id="6fe38-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="6fe38-107">Ele é herdado por classes derivadas quando aplicado a uma classe base.</span><span class="sxs-lookup"><span data-stu-id="6fe38-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="6fe38-108">O `AllowMultiple` e `Inherited` argumentos são opcionais, portanto, esse código tem o mesmo efeito:</span><span class="sxs-lookup"><span data-stu-id="6fe38-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="6fe38-109">A primeira `AttributeUsage` argumento deve ser um ou mais elementos do <xref:System.AttributeTargets>enumeração.</xref:System.AttributeTargets></span><span class="sxs-lookup"><span data-stu-id="6fe38-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="6fe38-110">Vários tipos de destino podem ser vinculados junto com o operador OR, como este:</span><span class="sxs-lookup"><span data-stu-id="6fe38-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="6fe38-111">Se o `AllowMultiple` argumento é definido como `true`, em seguida, o atributo resultante pode ser aplicado mais de uma vez a uma única entidade, como este:</span><span class="sxs-lookup"><span data-stu-id="6fe38-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 <span data-ttu-id="6fe38-112">Nesse caso `MultiUseAttr` pode ser aplicado várias vezes porque `AllowMultiple` é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="6fe38-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="6fe38-113">Os dois formatos mostrados para aplicar vários atributos são válidos.</span><span class="sxs-lookup"><span data-stu-id="6fe38-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="6fe38-114">Se `Inherited` é definido como `false`, em seguida, o atributo não é herdado por classes que derivam de uma classe que é atribuída.</span><span class="sxs-lookup"><span data-stu-id="6fe38-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="6fe38-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6fe38-115">For example:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 <span data-ttu-id="6fe38-116">Nesse caso `Attr1` não é aplicado a `DClass` por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="6fe38-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fe38-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fe38-117">Remarks</span></span>  
 <span data-ttu-id="6fe38-118">O `AttributeUsage` é um atributo de uso único – não pode ser aplicado mais de uma vez para a mesma classe.</span><span class="sxs-lookup"><span data-stu-id="6fe38-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="6fe38-119">`AttributeUsage`é um alias para <xref:System.AttributeUsageAttribute>.</xref:System.AttributeUsageAttribute></span><span class="sxs-lookup"><span data-stu-id="6fe38-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="6fe38-120">Para obter mais informações, consulte [acessar atributos por usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="6fe38-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fe38-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fe38-121">Example</span></span>  
 <span data-ttu-id="6fe38-122">O exemplo a seguir demonstra o efeito do `Inherited` e `AllowMultiple` argumentos para o `AttributeUsage` atributo e como os atributos personalizados aplicados a uma classe podem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="6fe38-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a><span data-ttu-id="6fe38-123">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fe38-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fe38-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fe38-124">See Also</span></span>  
 <span data-ttu-id="6fe38-125"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="6fe38-125"><xref:System.Attribute></span></span>   
 <span data-ttu-id="6fe38-126"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="6fe38-126"><xref:System.Reflection></span></span>   
<span data-ttu-id="6fe38-127"> [Guia de programação em Visual Basic](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6fe38-127"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="6fe38-128"> [Atributos](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="6fe38-128"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="6fe38-129"> [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="6fe38-129"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="6fe38-130"> [Atributos (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="6fe38-130"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="6fe38-131"> [Criando atributos personalizados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="6fe38-131"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
<span data-ttu-id="6fe38-132"> [Acessando atributos usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="6fe38-132"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
