---
title: "Como verificar o status da conexão no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 31a8bb72e3b5cdc5ddee626a377c70640facb81d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="8d4a3-102">Como verificar o status da conexão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d4a3-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="8d4a3-103">A propriedade <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> pode ser usada para determinar se o computador tem uma rede ou conexão de Internet em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="8d4a3-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="8d4a3-104">Para verificar se um computador tem uma conexão em funcionamento</span><span class="sxs-lookup"><span data-stu-id="8d4a3-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="8d4a3-105">Determine se a propriedade `IsAvailable` é `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="8d4a3-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="8d4a3-106">O código a seguir verifica e informa o status da propriedade:</span><span class="sxs-lookup"><span data-stu-id="8d4a3-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     <span data-ttu-id="8d4a3-107">Este exemplo de código também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8d4a3-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8d4a3-108">No selecionador de trecho de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="8d4a3-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="8d4a3-109">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8d4a3-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4a3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d4a3-110">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
