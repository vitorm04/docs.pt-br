---
title: "'ReDim' só pode alterar a dimensão mais à direita"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 584370f356180fe8b1710a9e145018be7f2d8a0f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592304"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>'ReDim' só pode alterar a dimensão mais à direita
Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não seja a última dimensão. Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz. Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remover o `Preserve` palavra-chave.  
  
## <a name="see-also"></a>Consulte também

- [Matrizes no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Dimensões de matriz no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [Instrução ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)
