---
title: "Parâmetros opcionais devem especificar um valor padrão | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30812
- bc30812
dev_langs:
- VB
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d94b001e108e8792f3a94cee6d5477be1a245347
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="09bb2-102">Parâmetros opcionais devem especificar um valor padrão</span><span class="sxs-lookup"><span data-stu-id="09bb2-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="09bb2-103">Parâmetros opcionais devem fornecer valores padrão que podem ser usados se nenhum parâmetro for fornecido por um procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="09bb2-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="09bb2-104">**ID do erro:** BC30812</span><span class="sxs-lookup"><span data-stu-id="09bb2-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09bb2-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="09bb2-105">To correct this error</span></span>  
  
-   <span data-ttu-id="09bb2-106">Especificar valores padrão para parâmetros opcionais; Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09bb2-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="09bb2-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09bb2-107">See Also</span></span>  
 [<span data-ttu-id="09bb2-108">Opcional</span><span class="sxs-lookup"><span data-stu-id="09bb2-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
