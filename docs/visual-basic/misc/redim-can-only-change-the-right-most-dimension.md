---
title: "'ReDim' só pode alterar a dimensão mais à direita"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 5b4f054c5d1dfad52ce19e1a9f9d246945866703
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53767382"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>'ReDim' só pode alterar a dimensão mais à direita
Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não seja a última dimensão. Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz. Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remover o `Preserve` palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dimensões de matriz no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [Instrução ReDim](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Preservar - excluir](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
