---
title: Parâmetros opcionais devem especificar um valor padrão
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e9ec6d044ba0a1bb904030ddbb4c4fa406c3ba63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="9c2c0-102">Parâmetros opcionais devem especificar um valor padrão</span><span class="sxs-lookup"><span data-stu-id="9c2c0-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="9c2c0-103">Parâmetros opcionais devem fornecer valores padrão que podem ser usados se nenhum parâmetro for fornecido por um procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="9c2c0-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="9c2c0-104">**ID do erro:** BC30812</span><span class="sxs-lookup"><span data-stu-id="9c2c0-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c2c0-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9c2c0-105">To correct this error</span></span>  
  
-   <span data-ttu-id="9c2c0-106">Especificar valores padrão para parâmetros opcionais; Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9c2c0-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9c2c0-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c2c0-107">See Also</span></span>  
 [<span data-ttu-id="9c2c0-108">Opcional</span><span class="sxs-lookup"><span data-stu-id="9c2c0-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
