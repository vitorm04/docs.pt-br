---
title: Como classificar uma matriz no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f24c0625058dbd960411d5981b4e98e0e9422b99
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Como classificar uma matriz no Visual Basic
Este exemplo declara uma matriz de `String` objetos nomeados `zooAnimals`, preenche-o e classifica em ordem alfabética.  
  
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
  
-   Acesso a Mscorlib.dll e o <xref:System> namespace.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   Matriz está vazia (<xref:System.ArgumentNullException> classe)  
  
-   Matriz é multidimensional (<xref:System.RankException> classe)  
  
-   Um ou mais elementos da matriz não implementam a <xref:System.IComparable> interface (<xref:System.InvalidOperationException> classe)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Coleções](../../concepts/collections.md)  
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
