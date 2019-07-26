---
title: Os limites de matriz não podem ser exibidos em especificadores de tipo
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512756"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Os limites de matriz não podem ser exibidos em especificadores de tipo

Os tamanhos de matriz não podem ser declarados como parte de um especificador de tipo de dados.

**ID do erro:** BC30638

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Especifique o tamanho da matriz imediatamente após o nome da variável, em vez de colocar o tamanho da matriz após o tipo, conforme mostrado no exemplo a seguir.

  ```vb
  Dim Array(8) As Integer
  ```

- Defina uma matriz e inicialize-a com o número de elementos desejado, conforme mostrado no exemplo a seguir.

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a>Consulte também

- [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
