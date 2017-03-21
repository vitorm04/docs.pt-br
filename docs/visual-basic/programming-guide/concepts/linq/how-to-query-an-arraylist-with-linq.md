---
title: 'Como: consultar um ArrayList com LINQ (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
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
ms.openlocfilehash: f48b06c23b1e28fccb953638954a8d9afefe574e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Como: consultar um ArrayList com LINQ (Visual Basic)
Ao usar o LINQ para consultas não-genérica <xref:System.Collections.IEnumerable>coleções como <xref:System.Collections.ArrayList>, você deve declarar explicitamente o tipo da variável de intervalo para refletir o tipo específico de objetos na coleção.</xref:System.Collections.ArrayList> </xref:System.Collections.IEnumerable> Por exemplo, se você tiver um <xref:System.Collections.ArrayList>de `Student` objetos, o [cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md) deve ter esta aparência:</xref:System.Collections.ArrayList>  
  
```  
  
Dim query = From student As Student In arrList   
...  
  
```  
  
 Especificando o tipo da variável de intervalo, são converter cada item de <xref:System.Collections.ArrayList>para um `Student`.</xref:System.Collections.ArrayList>  
  
 O uso de uma variável de intervalo explicitamente digitados em uma expressão de consulta é equivalente a chamar o <xref:System.Linq.Enumerable.Cast%2A>método.</xref:System.Linq.Enumerable.Cast%2A> <xref:System.Linq.Enumerable.Cast%2A>lança uma exceção se a conversão especificada não pode ser executada.</xref:System.Linq.Enumerable.Cast%2A> <xref:System.Linq.Enumerable.Cast%2A>e <xref:System.Linq.Enumerable.OfType%2A>são os dois métodos de operador de consulta padrão que operam em não-genérica <xref:System.Collections.IEnumerable>tipos.</xref:System.Collections.IEnumerable> </xref:System.Linq.Enumerable.OfType%2A></xref:System.Linq.Enumerable.Cast%2A> No Visual Basic, você deve chamar explicitamente o <xref:System.Linq.Enumerable.Cast%2A>método na fonte de dados para garantir que um tipo de variável de intervalo específico.</xref:System.Linq.Enumerable.Cast%2A> Para obter mais informações, consulte[relacionamentos de tipo em operações de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma consulta simples em um <xref:System.Collections.ArrayList>.</xref:System.Collections.ArrayList> Observe que este exemplo usa os inicializadores de objeto quando o código chama o <xref:System.Collections.ArrayList.Add%2A>método, mas isso não é um requisito.</xref:System.Collections.ArrayList.Add%2A>  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
