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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bf56f40033f9d1547d63fccd25e3c0561bb62cb1
ms.lasthandoff: 03/13/2017

---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
Determina como uma classe de atributo personalizado pode ser usada. `AttributeUsage`é um atributo que pode ser aplicado às definições de atributo personalizado para controlar como o novo atributo pode ser aplicado. As configurações padrão assim quando aplicado explicitamente:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 Neste exemplo, a `NewAttribute` classe pode ser aplicada a qualquer entidade de código capaz de atributo, mas podem ser aplicadas apenas uma vez para cada entidade. Ele é herdado por classes derivadas quando aplicado a uma classe base.  
  
 O `AllowMultiple` e `Inherited` argumentos são opcionais, portanto, esse código tem o mesmo efeito:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 A primeira `AttributeUsage` argumento deve ser um ou mais elementos do <xref:System.AttributeTargets>enumeração.</xref:System.AttributeTargets> Vários tipos de destino podem ser vinculados junto com o operador OR, como este:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 Se o `AllowMultiple` argumento é definido como `true`, em seguida, o atributo resultante pode ser aplicado mais de uma vez a uma única entidade, como este:  
  
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
  
 Nesse caso `MultiUseAttr` pode ser aplicado várias vezes porque `AllowMultiple` é definido como `true`. Os dois formatos mostrados para aplicar vários atributos são válidos.  
  
 Se `Inherited` é definido como `false`, em seguida, o atributo não é herdado por classes que derivam de uma classe que é atribuída. Por exemplo:  
  
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
  
 Nesse caso `Attr1` não é aplicado a `DClass` por meio de herança.  
  
## <a name="remarks"></a>Comentários  
 O `AttributeUsage` é um atributo de uso único – não pode ser aplicado mais de uma vez para a mesma classe. `AttributeUsage`é um alias para <xref:System.AttributeUsageAttribute>.</xref:System.AttributeUsageAttribute>  
  
 Para obter mais informações, consulte [acessar atributos por usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o efeito do `Inherited` e `AllowMultiple` argumentos para o `AttributeUsage` atributo e como os atributos personalizados aplicados a uma classe podem ser enumerados.  
  
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
  
## <a name="sample-output"></a>Saída de Exemplo  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Attribute></xref:System.Attribute>   
 <xref:System.Reflection></xref:System.Reflection>   
 [Guia de programação em Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Atributos](https://msdn.microsoft.com/library/5x6cd29c)   
 [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Atributos (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [Criando atributos personalizados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Acessando atributos usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
