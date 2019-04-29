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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772587"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="2f4ce-102">Parâmetros opcionais devem especificar um valor padrão</span><span class="sxs-lookup"><span data-stu-id="2f4ce-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="2f4ce-103">Parâmetros opcionais devem fornecer valores padrão que podem ser usados se nenhum parâmetro for fornecido por um procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="2f4ce-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="2f4ce-104">**ID do erro:** BC30812</span><span class="sxs-lookup"><span data-stu-id="2f4ce-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2f4ce-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2f4ce-105">To correct this error</span></span>  
  
- <span data-ttu-id="2f4ce-106">Especificar valores padrão para parâmetros opcionais; Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2f4ce-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2f4ce-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f4ce-107">See also</span></span>

- [<span data-ttu-id="2f4ce-108">Opcional</span><span class="sxs-lookup"><span data-stu-id="2f4ce-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
