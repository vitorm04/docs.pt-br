---
title: 'Como: Classificar uma matriz no Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700969"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Como classificar uma matriz no Visual Basic

Este artigo mostra um exemplo de como classificar uma matriz de cadeias de caracteres no Visual Basic.

## <a name="example"></a>Exemplo

Este exemplo declara uma matriz de objetos `String` chamados `zooAnimals`, popula-o e, em seguida, classifica-o em ordem alfabética:
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a>Programação robusta

As seguintes condições podem causar uma exceção:

- A matriz está vazia (classe <xref:System.ArgumentNullException>).
- A matriz é multidimensional (classe <xref:System.RankException>).
- Um ou mais elementos da matriz não implementam a interface <xref:System.IComparable> (classe <xref:System.InvalidOperationException>).

## <a name="see-also"></a>Consulte também

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Matrizes](index.md)
- [Solução de problemas de matrizes](troubleshooting-arrays.md)
- [Coleções](../../concepts/collections.md)
- [Instrução For Each...Next](../../../language-reference/statements/for-each-next-statement.md)
