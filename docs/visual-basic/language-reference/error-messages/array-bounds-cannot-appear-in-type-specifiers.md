---
title: "Limites de matriz não podem aparecer em especificadores de tipo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
dev_langs:
- VB
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
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
ms.openlocfilehash: c608ef3d48eff4036f72c8504f882ac251a989d8
ms.lasthandoff: 03/13/2017

---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Os limites de matriz não podem ser exibidos em especificadores de tipo
Tamanhos de matriz não podem ser declarados como parte de um especificador de tipo de dados.  
  
 **ID do erro:** BC30638  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Especifique o tamanho da matriz imediatamente após o nome da variável em vez de colocar o tamanho da matriz após o tipo, conforme mostrado no exemplo a seguir.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Definir uma matriz e inicialize-o com o número desejado de elementos, conforme mostrado no exemplo a seguir.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
