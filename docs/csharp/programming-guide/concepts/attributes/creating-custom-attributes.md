---
title: Criando atributos personalizados (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 38bdedb352cc79f7a4cc3d08eb6138e7d994514b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-c"></a>Criando atributos personalizados (C#)
Você pode criar seus próprios atributos personalizados definindo uma classe de atributos, uma classe que deriva direta ou indiretamente de <xref:System.Attribute>, o que faz com que a identificação das definições de atributo nos metadados seja rápida e fácil. Suponha que você queira marcar tipos com o nome do programador que escreveu o tipo. Você pode definir uma classe de atributos `Author` personalizada:  
  
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
 [Escrevendo atributos personalizados](../../../../standard/attributes/writing-custom-attributes.md)  
 [Reflexão (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atributos (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Acessando atributos usando reflexão (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
