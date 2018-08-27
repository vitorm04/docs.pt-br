---
title: Como verificar o status da conexão no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 4a6cb67474d03ada5e0a73d94f65da7a381c44a8
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911935"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="3b0f6-102">Como verificar o status da conexão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b0f6-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="3b0f6-103">A propriedade <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> pode ser usada para determinar se o computador tem uma rede ou conexão de Internet em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="3b0f6-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="3b0f6-104">Para verificar se um computador tem uma conexão em funcionamento</span><span class="sxs-lookup"><span data-stu-id="3b0f6-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="3b0f6-105">Determine se a propriedade `IsAvailable` é `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="3b0f6-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="3b0f6-106">O código a seguir verifica e informa o status da propriedade:</span><span class="sxs-lookup"><span data-stu-id="3b0f6-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     <span data-ttu-id="3b0f6-107">Este exemplo de código também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3b0f6-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3b0f6-108">No selecionador de trecho de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="3b0f6-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="3b0f6-109">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="3b0f6-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0f6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b0f6-110">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
