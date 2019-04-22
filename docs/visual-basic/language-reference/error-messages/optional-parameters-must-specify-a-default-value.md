---
title: Parâmetros opcionais devem especificar um valor padrão
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 01c0abb366e8605a9b153333e645fc3276b6bd16
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821719"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>Parâmetros opcionais devem especificar um valor padrão
Parâmetros opcionais devem fornecer valores padrão que podem ser usados se nenhum parâmetro for fornecido por um procedimento de chamada.  
  
 **ID do erro:** BC30812  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Especificar valores padrão para parâmetros opcionais; Por exemplo:  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Opcional](../../../visual-basic/language-reference/modifiers/optional.md)
