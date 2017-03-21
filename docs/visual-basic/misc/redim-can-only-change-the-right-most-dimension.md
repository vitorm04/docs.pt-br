---
title: "&quot;ReDim&quot; só pode alterar a dimensão mais à direita | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b78d409cda4e4493eac988edfa4b821ba141b7f4
ms.lasthandoff: 03/13/2017

---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>'ReDim' só pode alterar a dimensão mais à direita
A `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não seja a última dimensão. Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz. Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remover o `Preserve` palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/en-us/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD matrizes multidimensionais no Visual Basic](http://msdn.microsoft.com/en-us/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [Instrução reDim](../../visual-basic/language-reference/statements/redim-statement.md)   
 [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)   
 [Preservar - excluir](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
