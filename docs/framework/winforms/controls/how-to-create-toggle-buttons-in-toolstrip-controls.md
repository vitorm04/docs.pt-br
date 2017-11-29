---
title: "Como criar botões de alternância em controles ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8529637db7bc4cca011d0992b257d5b8ce9aaff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="c4bb6-102">Como criar botões de alternância em controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c4bb6-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="c4bb6-103">Quando um usuário clica em um botão de alternância, ele aparece em baixo relevo e mantém a aparência de baixo relevo até que o usuário clica no botão novamente.</span><span class="sxs-lookup"><span data-stu-id="c4bb6-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="c4bb6-104">Para criar uma alternância ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="c4bb6-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="c4bb6-105">Use o código como o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4bb6-105">Use code such as the following code example.</span></span> <span data-ttu-id="c4bb6-106">Esse código supõe que o formulário contém um <xref:System.Windows.Forms.ToolStrip> controle e que seu <xref:System.Windows.Forms.ToolStrip.Items%2A> coleção contém um <xref:System.Windows.Forms.ToolStripButton> chamado `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="c4bb6-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="c4bb6-107">Ele também pressupõe que você tenha um manipulador de eventos chamado `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="c4bb6-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c4bb6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4bb6-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripButton>  
 [<span data-ttu-id="c4bb6-109">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c4bb6-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
