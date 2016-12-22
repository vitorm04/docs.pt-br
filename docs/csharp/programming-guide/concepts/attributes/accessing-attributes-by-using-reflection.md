---
title: "Acessando atributos usando reflex&#227;o (c#) | Microsoft Docs"
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
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Acessando atributos usando reflex&#227;o (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O fato de que você pode definir atributos personalizados e colocá\-los em seu código\-fonte seria de pouco valor sem alguma maneira de recuperar essas informações e agir sobre ele. Por meio de reflexão, você pode recuperar as informações que foi definidas com atributos personalizados. O método principal é `GetCustomAttributes`, que retorna uma matriz de objetos que são os equivalentes de tempo de execução dos atributos de código de origem. Esse método possui várias versões sobrecarregadas. Para obter mais informações, consulte <xref:System.Attribute>.  
  
 Uma especificação de atributo, como:  
  
```c#  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 é conceitualmente equivalente a esta:  
  
```c#  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 No entanto, o código não será executado até `SampleClass` é consultada para atributos. Chamando `GetCustomAttributes` em `SampleClass` faz com que uma `Author` objeto a ser criado e inicializado como acima. Se a classe tiver outros atributos, outros objetos de atributo são construídos da mesma forma.`GetCustomAttributes` em seguida, retorna o `Author` objeto e quaisquer outros objetos de atributo em uma matriz. Você pode iterar sobre essa matriz, determinar quais atributos foram aplicados com base no tipo de cada elemento da matriz e extrair informações dos objetos de atributo.  
  
## Exemplo  
 Aqui está um exemplo completo. Um atributo personalizado é definido, aplicado a várias entidades e recuperado por meio de reflexão.  
  
```c#  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## Consulte também  
 <xref:System.Reflection>   
 <xref:System.Attribute>   
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)   
 [Recuperando informações armazenadas em atributos](../Topic/Retrieving%20Information%20Stored%20in%20Attributes.md)   
 [Reflexão \(c\#\)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Atributos \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Criando atributos personalizados \(c\#\)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)