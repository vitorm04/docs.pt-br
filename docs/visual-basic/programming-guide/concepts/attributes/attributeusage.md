---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 1841171f2f3fc26ba9244c72c69960b765d39807
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827504"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="9866a-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9866a-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="9866a-103">Determina como uma classe de atributo personalizado pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="9866a-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="9866a-104">`AttributeUsage` é um atributo que pode ser aplicado às definições de atributo personalizado para controlar como o novo atributo pode ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="9866a-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="9866a-105">As configurações padrão têm essa aparência quando aplicadas explicitamente:</span><span class="sxs-lookup"><span data-stu-id="9866a-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="9866a-106">Neste exemplo, a classe `NewAttribute` pode ser aplicada a qualquer entidade de código capaz de receber atributo, mas pode ser aplicadas apenas uma vez para cada entidade.</span><span class="sxs-lookup"><span data-stu-id="9866a-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="9866a-107">Ela é herdada por classes derivadas quando aplicada a uma classe base.</span><span class="sxs-lookup"><span data-stu-id="9866a-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="9866a-108">Os argumentos `AllowMultiple` e `Inherited` são opcionais, portanto, esse código tem o mesmo efeito:</span><span class="sxs-lookup"><span data-stu-id="9866a-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="9866a-109">O primeiro argumento `AttributeUsage` deve ser um ou mais elementos da enumeração <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="9866a-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="9866a-110">Vários tipos de destino podem ser vinculados junto com o operador OR, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="9866a-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="9866a-111">Se o argumento `AllowMultiple` for definido como `true`, o atributo resultante poderá ser aplicado mais de uma vez a uma única entidade, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="9866a-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="9866a-112">Nesse caso `MultiUseAttr` pode ser aplicado repetidas vezes porque `AllowMultiple` está definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="9866a-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="9866a-113">Os dois formatos mostrados para a aplicação de vários atributos são válidos.</span><span class="sxs-lookup"><span data-stu-id="9866a-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="9866a-114">Se `Inherited` for definido como `false`, o atributo não será herdado por classes derivadas de uma classe que é atribuída.</span><span class="sxs-lookup"><span data-stu-id="9866a-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="9866a-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9866a-115">For example:</span></span>  
  
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
  
 <span data-ttu-id="9866a-116">Nesse caso `Attr1` não é aplicado a `DClass` por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="9866a-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9866a-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="9866a-117">Remarks</span></span>  
 <span data-ttu-id="9866a-118">O atributo `AttributeUsage` é um atributo de uso único. Ele não pode ser aplicado mais de uma vez para a mesma classe.</span><span class="sxs-lookup"><span data-stu-id="9866a-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="9866a-119">`AttributeUsage` é um alias para <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9866a-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="9866a-120">Para obter mais informações, consulte [Acessando atributos usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="9866a-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9866a-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9866a-121">Example</span></span>  
 <span data-ttu-id="9866a-122">O exemplo a seguir demonstra o efeito dos argumentos `Inherited` e `AllowMultiple` no atributo `AttributeUsage` e como os atributos personalizados aplicados a uma classe podem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9866a-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="9866a-123">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="9866a-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="9866a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9866a-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="9866a-125">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9866a-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="9866a-126">Atributos</span><span class="sxs-lookup"><span data-stu-id="9866a-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="9866a-127">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9866a-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="9866a-128">Atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9866a-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="9866a-129">Criando atributos personalizados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9866a-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="9866a-130">Acessando atributos usando reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9866a-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
