---
title: 'Como: Verificar o status da conexão no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: c7a43fd154616e516f8c5e7d36d25f34924649ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499954"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="1e49d-102">Como: Verificar o status da conexão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e49d-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="1e49d-103">A propriedade <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> pode ser usada para determinar se o computador tem uma rede ou conexão de Internet em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="1e49d-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="1e49d-104">Para verificar se um computador tem uma conexão em funcionamento</span><span class="sxs-lookup"><span data-stu-id="1e49d-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="1e49d-105">Determine se a propriedade `IsAvailable` é `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="1e49d-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="1e49d-106">O código a seguir verifica e informa o status da propriedade:</span><span class="sxs-lookup"><span data-stu-id="1e49d-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     <span data-ttu-id="1e49d-107">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="1e49d-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="1e49d-108">No selecionador de snippet de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="1e49d-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="1e49d-109">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="1e49d-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e49d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e49d-110">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
