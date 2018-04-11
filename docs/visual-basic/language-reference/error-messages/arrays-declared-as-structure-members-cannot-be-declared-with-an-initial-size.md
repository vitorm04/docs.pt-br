---
title: Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial
Uma matriz em uma estrutura é declarada com um tamanho inicial. Não é possível inicializar qualquer elemento de estrutura e declarar um tamanho da matriz é uma forma de inicialização.  
  
 **ID do erro:** BC31043  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Defina a matriz na sua estrutura como dinâmica (sem tamanho inicial).  
  
2.  Se você precisar de um determinado tamanho de matriz, você pode redimensionar uma matriz dinâmica com uma [instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) quando seu código está sendo executado. O exemplo a seguir ilustra essa situação.  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Como declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
