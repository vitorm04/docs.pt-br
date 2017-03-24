---
title: "Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
dev_langs:
- VB
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 679af6f8f709134b791ef763b86070d9d66fa12c
ms.lasthandoff: 03/13/2017

---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial
Uma matriz em uma estrutura é declarada com um tamanho inicial. Você não pode inicializar qualquer elemento de estrutura, e declarar o tamanho de uma matriz é uma forma de inicialização.  
  
 **ID do erro:** BC31043  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Defina a matriz na sua estrutura como dinâmica (sem tamanho inicial).  
  
2.  Se você precisar de um certo tamanho de matriz, você pode redimensionar uma matriz dinâmica com uma [instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) quando seu código está em execução. O exemplo a seguir ilustra essa situação.  
  
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
