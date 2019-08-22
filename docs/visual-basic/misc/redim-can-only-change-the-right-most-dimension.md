---
title: "' ReDim ' só pode alterar a dimensão mais à direita"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: f38bcb99b682ace497859b67fe3bb829bbc80c4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664416"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>' ReDim ' só pode alterar a dimensão mais à direita
Uma `ReDim` instrução tentou usar a `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não é a última dimensão. Ao usar `Preserve`o, você pode redimensionar apenas a última dimensão de uma matriz. Para todas as outras dimensões, você deve especificar o mesmo tamanho de para a matriz existente.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a `Preserve` palavra-chave.  
  
## <a name="see-also"></a>Consulte também

- [Matrizes no Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Dimensões de matriz no Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [Instrução ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)
