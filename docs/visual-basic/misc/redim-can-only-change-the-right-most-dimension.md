---
title: "&#39; ReDim &#39; só é possível alterar a dimensão mais à direita"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752e0e54c48b3b348a477787e5e911f1b1777667
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>&#39; ReDim &#39; só é possível alterar a dimensão mais à direita
Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não é da última dimensão. Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz. Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remover o `Preserve` palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dimensões de matriz no Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [Instrução ReDim](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Preservar - excluir](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
