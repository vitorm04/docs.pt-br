---
title: '&#39;ReDim&#39; só pode alterar a dimensão mais à direita'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: efb98df13a7e3e378347b30b6fc00b90030ec194
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641177"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>&#39;ReDim&#39; só pode alterar a dimensão mais à direita
Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não é da última dimensão. Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz. Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remover o `Preserve` palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dimensões de matriz no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [Instrução ReDim](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Preservar - excluir](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
