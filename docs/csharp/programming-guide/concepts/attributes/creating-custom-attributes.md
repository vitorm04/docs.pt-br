---
title: Criando atributos personalizados (C#) | Microsoft Docs
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
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
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
ms.openlocfilehash: b71bf8fe1f4d448bf373fcab4bccd89bca4672b8
ms.lasthandoff: 03/13/2017

---
# <a name="creating-custom-attributes-c"></a>Criando atributos personalizados (C#)
Você pode criar seus próprios atributos personalizados definindo uma classe de atributos, uma classe que deriva diretamente ou indiretamente de <xref:System.Attribute>, fazendo com que a identificação das definições de atributo nos metadados seja rápida e fácil. Suponha que você queira marcar tipos com o nome do programador que escreveu o tipo. Você pode definir uma classe de atributos `Author` personalizada:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 O nome de classe será o nome do atributo, `Author`. Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado. Os parâmetros do construtor são parâmetros posicionais do atributo personalizado. Neste exemplo, `name` é um parâmetro posicional. Quaisquer propriedades ou campos públicos de leitura/gravação são chamados de parâmetros. Nesse caso, `version` é o único parâmetro nomeado. Observe o uso do atributo `AttributeUsage` para tornar o atributo `Author` válido apenas na classe e nas declarações `struct`.  
  
 Você pode usar esse novo atributo da seguinte maneira:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado de uso único ou mulituso. No exemplo de código a seguir, um atributo multiuso é criado.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 No exemplo de código a seguir, vários atributos do mesmo tipo são aplicados a uma classe.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  Se sua classe de atributos contém uma propriedade, essa propriedade deve ser de leitura/gravação.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection>   
 [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)   
 [Escrevendo atributos personalizados](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc)   
 [Reflexão (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Atributos (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Acessando atributos usando reflexão (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
