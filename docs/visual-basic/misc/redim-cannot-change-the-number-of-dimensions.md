---
title: "'ReDim' não é possível alterar o número de dimensões"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 1e9695bbc7f104aa741de232f1f6d3c76df2cebf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591739"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>'ReDim' não é possível alterar o número de dimensões
Uma operação tenta usar o `ReDim` instrução para alterar a classificação (número de dimensões) de uma matriz. `ReDim` pode alterar o tamanho de uma ou mais dimensões de uma matriz que já foi formalmente declarado, mas ele não é possível alterar a classificação de matriz.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Certifique-se de que você pretende alterar a classificação da matriz e não os tamanhos das suas dimensões e, se possível, use `Dim` para declarar uma nova matriz com a classificação desejada.  
  
## <a name="see-also"></a>Consulte também

- [Matrizes no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Dimensões de matriz no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [Instrução ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)
