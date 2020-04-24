---
title: 'Como: Verificar o status da conexão'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 89ef431759dac25bd213fd954db0712ad95434b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345890"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="0c846-102">Como verificar o status da conexão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c846-102">How to: Check Connection Status in Visual Basic</span></span>

<span data-ttu-id="0c846-103">A propriedade <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> pode ser usada para determinar se o computador tem uma rede ou conexão de Internet em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="0c846-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="0c846-104">Para verificar se um computador tem uma conexão em funcionamento</span><span class="sxs-lookup"><span data-stu-id="0c846-104">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="0c846-105">Determine se a propriedade `IsAvailable` é `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="0c846-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="0c846-106">O código a seguir verifica e informa o status da propriedade:</span><span class="sxs-lookup"><span data-stu-id="0c846-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="0c846-107">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="0c846-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="0c846-108">No selecionador de snippet de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="0c846-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="0c846-109">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="0c846-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c846-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c846-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
