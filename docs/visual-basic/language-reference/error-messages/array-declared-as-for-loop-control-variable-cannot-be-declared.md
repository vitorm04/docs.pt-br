---
title: A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: bee3bcd3701945f5cf77f6761defc8be77acf49f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935376"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial
Um `For Each` loop usa uma matriz como seu *elemento* variável de iteração, mas inicializa essa matriz.  
  
 As instruções a seguir mostram como esse erro pode ser gerado.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 A primeira `For Each` instrução é a maneira correta de acessar elementos de `arrayList`. O segundo `For Each` instrução gera esse erro.  
  
 **ID do erro:** BC32039  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a inicialização da declaração do *elemento* variável de iteração.  
  
## <a name="see-also"></a>Consulte também

- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Coleções](../../../standard/collections/index.md)
