---
title: 'Como: Classificar uma matriz no Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 680f488a98d6e7e31b3d077843514fd12f75481c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586434"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Como: Classificar uma matriz no Visual Basic
Este exemplo declara uma matriz de `String` objetos nomeados `zooAnimals`, preenche-o e, em seguida, classifica-os em ordem alfabética.  
  
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
  
- Acesso a <xref:System> namespace.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
- Matriz está vazia (<xref:System.ArgumentNullException> classe)  
  
- A matriz é multidimensional (<xref:System.RankException> classe)  
  
- Um ou mais elementos da matriz não implementam o <xref:System.IComparable> interface (<xref:System.InvalidOperationException> classe)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Coleções](../../concepts/collections.md)
- [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
