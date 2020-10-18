---
title: O número de índices excede o número de dimensões da matriz indexada
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 9a191ff7ec3ad6a607e6509cc143c359f64f21ea
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159905"
---
# <a name="bc30106-number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>BC30106: o número de índices excede o número de dimensões da matriz indexada

O número de índices usados para acessar um elemento de matriz deve ser exatamente o mesmo que a classificação da matriz, ou seja, o número de dimensões declaradas para ele.

 **ID do erro:** BC30106

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Remova os subscritos da referência de matriz até que o número total de subscritos seja igual à classificação da matriz. Por exemplo:

    ```vb
    Dim gameBoard(3, 3) As String

    ' Incorrect code. The array has two dimensions.
    gameBoard(1, 1, 1) = "X"
    gameBoard(2, 1, 1) = "O"

    ' Correct code.
    gameBoard(0, 0) = "X"
    gameBoard(1, 0) = "O"
    ```

## <a name="see-also"></a>Confira também

- [matrizes](../../programming-guide/language-features/arrays/index.md)
