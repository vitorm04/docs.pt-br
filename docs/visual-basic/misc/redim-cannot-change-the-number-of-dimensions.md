---
title: '&#39;ReDim&#39; não é possível alterar o número de dimensões'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: bfd4096141833b85a2126340ef549e1e1d1f8e3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640374"
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a>&#39;ReDim&#39; não é possível alterar o número de dimensões
Uma operação tenta usar o `ReDim` instrução para alterar a classificação (número de dimensões) de uma matriz. `ReDim` pode alterar o tamanho de uma ou mais dimensões de uma matriz que já tenha sido formalmente declarado, mas ele não pode alterar a classificação de matriz.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que você pretende alterar a classificação da matriz e não os tamanhos das suas dimensões e, se possível, use `Dim` para declarar uma nova matriz com a classificação desejada.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dimensões de matriz no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [Instrução ReDim](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)
