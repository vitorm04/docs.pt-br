---
title: "Criando atributos personalizados (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Criando atributos personalizados (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode criar seus próprios atributos personalizados, definindo uma classe de atributo, uma classe que deriva diretamente ou indiretamente de <xref:System.Attribute>, que faz com que identifica as definições de atributo nos metadados rápida e fácil. Suponha que você queira para tipos de marca com o nome do programador que escreveu o tipo. Você pode definir um personalizado `Author` classe de atributo:  
  
```c#  
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
  
 O nome da classe é o nome do atributo, `Author`. Ela é derivada de `System.Attribute`, portanto, é uma classe de atributo personalizado. Parâmetros do construtor são parâmetros posicionais do atributo personalizado. Neste exemplo, `name` é um parâmetro posicional. Quaisquer propriedades ou campos públicos de leitura \/ gravação são parâmetros nomeadas. Nesse caso, `version` é o único parâmetro nomeado. Observe o uso do `AttributeUsage` atributo para tornar o `Author` válido apenas na classe de atributo e `struct` declarações.  
  
 Você pode usar esse novo atributo da seguinte maneira:  
  
```c#  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` tem um parâmetro nomeado, `AllowMultiple`, com o qual você pode fazer um atributo personalizado multiuse ou de uso único. No exemplo de código a seguir, um atributo multiuse é criado.  
  
```c#  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 No exemplo de código a seguir, vários atributos do mesmo tipo são aplicados a uma classe.  
  
```c#  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  Se sua classe de atributo contém uma propriedade, essa propriedade deve ser leitura \/ gravação.  
  
## Consulte também  
 <xref:System.Reflection>   
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)   
 [Escrevendo atributos personalizados](../Topic/Writing%20Custom%20Attributes.md)   
 [Reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Atributos \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Acessando atributos usando reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage \(c\#\)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)