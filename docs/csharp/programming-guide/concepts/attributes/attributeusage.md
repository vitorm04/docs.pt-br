---
title: AttributeUsage (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6f6c72c8152cc0f76085efbaa99ec63e50d1b676
ms.lasthandoff: 03/13/2017

---
# <a name="attributeusage-c"></a>AttributeUsage (C#)
Determina como uma classe de atributo personalizado pode ser usada. `AttributeUsage` é um atributo que pode ser aplicado às definições de atributo personalizado para controlar como o novo atributo pode ser aplicado. As configurações padrão têm essa aparência quando aplicadas explicitamente:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 Neste exemplo, a classe `NewAttribute` pode ser aplicada a qualquer entidade de código capaz de receber atributo, mas pode ser aplicadas apenas uma vez para cada entidade. Ela é herdada por classes derivadas quando aplicada a uma classe base.  
  
 Os argumentos `AllowMultiple` e `Inherited` são opcionais, portanto, esse código tem o mesmo efeito:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 O primeiro argumento `AttributeUsage` deve ser um ou mais elementos da enumeração <xref:System.AttributeTargets>. Vários tipos de destino podem ser vinculados junto com o operador OR, dessa maneira:  
  
```csharp  
using System;  
```  
  
```csharp  
[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 Se o argumento `AllowMultiple` for definido como `true`, o atributo resultante poderá ser aplicado mais de uma vez a uma única entidade, dessa maneira:  
  
```csharp  
using System;  
```  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 Nesse caso `MultiUseAttr` pode ser aplicado repetidas vezes porque `AllowMultiple` está definido como `true`. Os dois formatos mostrados para a aplicação de vários atributos são válidos.  
  
 Se `Inherited` for definido como `false`, o atributo não será herdado por classes derivadas de uma classe que é atribuída. Por exemplo:  
  
```csharp  
using System;  
```  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 Nesse caso `Attr1` não é aplicado a `DClass` por meio de herança.  
  
## <a name="remarks"></a>Comentários  
 O atributo `AttributeUsage` é um atributo de uso único. Ele não pode ser aplicado mais de uma vez para a mesma classe. `AttributeUsage` é um alias para <xref:System.AttributeUsageAttribute>.  
  
 Para obter mais informações, consulte [Acessando atributos usando reflexão (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o efeito dos argumentos `Inherited` e `AllowMultiple` no atributo `AttributeUsage` e como os atributos personalizados aplicados a uma classe podem ser enumerados.  
  
```csharp  
using System;  
```  
  
```csharp  
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
 <xref:System.Attribute>   
 <xref:System.Reflection>   
 [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)   
 [Atributos](https://msdn.microsoft.com/library/5x6cd29c)   
 [Reflexão (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Atributos](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Criando atributos personalizados (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Acessando atributos usando reflexão (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
