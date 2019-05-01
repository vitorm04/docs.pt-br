---
title: 'Como: Classificar uma matriz no Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3f4dbd6dce0957de3451b1f29c3a67ccd6791045
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053649"
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
  
- Acesso ao mscorlib. dll e o <xref:System> namespace.  
  
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
