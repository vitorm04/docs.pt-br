---
title: "'ReDim' não é possível alterar o número de dimensões"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b6bb78c3f1d7224e6e4b432fd3aef4589f2f1cd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964886"
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
