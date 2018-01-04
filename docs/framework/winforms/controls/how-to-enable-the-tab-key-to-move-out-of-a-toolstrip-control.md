---
title: Como habilitar a tecla TAB para deixar um controle ToolStrip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38a2e331d9530c42be6b9047b11ea235ae81d58d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a><span data-ttu-id="1e0ce-102">Como habilitar a tecla TAB para deixar um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1e0ce-102">How to: Enable the TAB Key to Move Out of a ToolStrip Control</span></span>
<span data-ttu-id="1e0ce-103">Use o procedimento a seguir para permitir que o usuário pressionar a tecla TAB para mover de um <xref:System.Windows.Forms.ToolStrip> para o próximo controle na ordem de tabulação.</span><span class="sxs-lookup"><span data-stu-id="1e0ce-103">Use the following procedure to enable the user to press the TAB key to move out of a <xref:System.Windows.Forms.ToolStrip> to the next control in the tab order.</span></span>  
  
 <span data-ttu-id="1e0ce-104">O <xref:System.Windows.Forms.ToolStrip> aceita a primeira pressione a tecla TAB e os chaves de seta para selecionar itens dentro de <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="1e0ce-104">The <xref:System.Windows.Forms.ToolStrip> accepts the first press of the TAB key, and the arrow keys select items within the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="1e0ce-105">Quando o usuário pressiona a tecla TAB uma segunda vez, ele leva o usuário para o próximo controle na ordem de tabulação.</span><span class="sxs-lookup"><span data-stu-id="1e0ce-105">When the user presses the TAB key a second time, it takes the user to the next control in the tab order.</span></span>  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a><span data-ttu-id="1e0ce-106">Para permitir que o usuário pressionar a tecla TAB para mover para fora de um ToolStrip para o próximo controle</span><span class="sxs-lookup"><span data-stu-id="1e0ce-106">To enable the user to press the TAB key to move out of a ToolStrip to the next control</span></span>  
  
-   <span data-ttu-id="1e0ce-107">Definir o <xref:System.Windows.Forms.ToolStrip.TabStop%2A> propriedade o <xref:System.Windows.Forms.ToolStrip> para `true`.</span><span class="sxs-lookup"><span data-stu-id="1e0ce-107">Set the <xref:System.Windows.Forms.ToolStrip.TabStop%2A> property of the <xref:System.Windows.Forms.ToolStrip> to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e0ce-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e0ce-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>  
 [<span data-ttu-id="1e0ce-109">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1e0ce-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
