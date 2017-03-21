---
title: "Acessando atributos usando reflexão (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
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
ms.openlocfilehash: 4763eccc5d1a6bdf3e89c1c4d825d5ff5c6caa3e
ms.lasthandoff: 03/13/2017

---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Acessando atributos usando reflexão (Visual Basic)
O fato de que você pode definir atributos personalizados e colocá-los em seu código-fonte seria de pouco valor sem alguma maneira de recuperar essas informações e agir sobre ele. Por meio de reflexão, você pode recuperar as informações que foi definidas com atributos personalizados. O método principal é `GetCustomAttributes`, que retorna uma matriz de objetos que são os equivalentes de tempo de execução dos atributos de código de origem. Esse método possui várias versões sobrecarregadas. Para obter mais informações, consulte <xref:System.Attribute>.</xref:System.Attribute>  
  
 Uma especificação de atributo, como:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 é conceitualmente equivalente a esta:  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 No entanto, o código não será executado até `SampleClass` é consultada para atributos. Chamando `GetCustomAttributes` na `SampleClass` faz com que uma `Author` objeto a ser criado e inicializado como acima. Se a classe tiver outros atributos, outros objetos de atributo são construídos da mesma forma. `GetCustomAttributes`em seguida, retorna o `Author` objeto e quaisquer outros objetos de atributo em uma matriz. Você pode iterar sobre essa matriz, determinar quais atributos foram aplicados com base no tipo de cada elemento da matriz e extrair informações dos objetos de atributo.  
  
## <a name="example"></a>Exemplo  
 Aqui está um exemplo completo. Um atributo personalizado é definido, aplicado a várias entidades e recuperado por meio de reflexão.  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Guia de programação em Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Recuperando informações armazenadas em atributos](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)   
 [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Atributos (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [Criando atributos personalizados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
