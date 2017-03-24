---
title: 'Como: classificar uma matriz no Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Array.Sort
dev_langs:
- VB
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 68b11142b5596bd55f67ff1df7e321950aaa9cce
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Como classificar uma matriz no Visual Basic
Este exemplo declara uma matriz de `String` objetos nomeados `zooAnimals`, preenche-a e classifica em ordem alfabética.  
  
## <a name="example"></a>Exemplo  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Acesso ao mscorlib. dll e o <xref:System>namespace.</xref:System>  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   Matriz está vazia (<xref:System.ArgumentNullException> classe)</xref:System.ArgumentNullException>  
  
-   Matriz é multidimensional (<xref:System.RankException> classe)</xref:System.RankException>  
  
-   Um ou mais elementos da matriz não implementam a <xref:System.IComparable>interface (<xref:System.InvalidOperationException> classe)</xref:System.InvalidOperationException> </xref:System.IComparable>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Array.Sort%2A?displayProperty=fullName></xref:System.Array.Sort%2A?displayProperty=fullName>   
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)   
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
