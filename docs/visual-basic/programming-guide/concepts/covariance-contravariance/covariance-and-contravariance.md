---
title: "Covariância e contravariância (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b785e298c5ba38a8e3d8cc549b2dcf2df1ef6bd8
ms.lasthandoff: 03/13/2017

---
# <a name="covariance-and-contravariance-visual-basic"></a>Covariância e contravariância (Visual Basic)
No Visual Basic, covariância e contravariância Habilitar conversão de referência implícita de tipos de matriz, tipos de delegados e argumentos de tipo genérico. Covariância preserva a compatibilidade de atribuição e contravariância inverte a ele.  
  
 O código a seguir demonstra a diferença entre a compatibilidade da atribuição, covariância e contravariância.  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 Covariância de matrizes permite a conversão implícita de uma matriz de um tipo mais derivado para uma matriz de um tipo derivado. Mas essa operação não é fortemente tipado, conforme mostrado no exemplo de código a seguir.  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 Covariância e contravariância suporte para grupos de método permite assinaturas de método correspondentes com tipos delegados. Isso permite atribuir a delegados não apenas os métodos que têm correspondência assinaturas, mas também métodos que retornam que mais derivado tipos (covariância) ou que aceita parâmetros que têm menos tipos derivados (contravariância) que o especificado pelo tipo de delegado. Para obter mais informações, consulte [variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [usando variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 O exemplo de código a seguir mostra a covariância e contravariância suportam para grupos de método.  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 No .NET Framework 4 ou posterior do Visual Basic suportam covariância e contravariância em interfaces e delegados genéricos e permitir a conversão implícita de parâmetros de tipo genérico. Para obter mais informações, consulte [variação em Interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) e [variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 O exemplo de código a seguir mostra a conversão de referência implícita para interfaces genéricas.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Uma interface genérica ou representante é chamado *variante* se seus parâmetros genéricos são declarados covariantes ou contravariant. Visual Basic permite que você crie suas próprias interfaces variantes e delegados. Para obter mais informações, consulte [criando Interfaces genéricas variantes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) e [variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Variação em Interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Discute a covariância e contravariância em interfaces genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.|  
|[Criando Interfaces genéricas variantes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Mostra como criar interfaces variantes personalizados.|  
|[Usando variação em Interfaces para coleções genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Mostra como suportam a covariância e contravariância no <xref:System.Collections.Generic.IEnumerable%601>e <xref:System.IComparable%601>interfaces podem ajudá-lo a reutilizar o código.</xref:System.IComparable%601> </xref:System.Collections.Generic.IEnumerable%601>|  
|[Variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Discute a covariância e contravariância genérica e não genérica delegados e fornece uma lista de variantes delegados genéricos no .NET Framework.|  
|[Usando variação em delegações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Mostra como usar o suporte a covariância e contravariância delegados não genérico para corresponder assinaturas de método com tipos delegados.|  
|[Usando variação para delegações Func e Action genérica (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Mostra como suportam a covariância e contravariância no `Func` e `Action` delegados podem ajudá-lo a reutilizar o código.|
