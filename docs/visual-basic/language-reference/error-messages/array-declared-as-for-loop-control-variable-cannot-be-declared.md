---
title: A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: 9f24dd2a20dc3a4935cd288a20a0e12c1d47bee1
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912342"
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
