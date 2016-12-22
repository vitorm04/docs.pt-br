---
title: "Como classificar uma matriz no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Array.Sort"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "matrizes [Visual Basic], classificando"
  - "exemplos [Visual Basic], matrizes"
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como classificar uma matriz no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo declara uma matriz de objetos `String` denominados `zooAnimals`, gera\-a e então organiza seu conteúdo alfabeticamente.  
  
## Exemplo  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## Compilando o código  
 Este exemplo requer:  
  
-   Acesso ao MScorlib.dll e ao namespace <xref:System>.  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   Matriz está vazia \(classe <xref:System.ArgumentNullException>\)  
  
-   Matriz é multidimensional \(classe <xref:System.RankException>\)  
  
-   Um ou mais elementos da matriz não implementam a interface <xref:System.IComparable> \(classe <xref:System.InvalidOperationException>\)  
  
## Consulte também  
 <xref:System.Array.Sort%2A?displayProperty=fullName>   
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)