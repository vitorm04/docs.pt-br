---
title: Como criar botões de alternância em controles ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: a04d531433273328c2d8eb0c5ef614f08c33952a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530374"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="86bc1-102">Como criar botões de alternância em controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="86bc1-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="86bc1-103">Quando um usuário clica em um botão de alternância, ele aparece em baixo relevo e mantém a aparência de baixo relevo até que o usuário clica no botão novamente.</span><span class="sxs-lookup"><span data-stu-id="86bc1-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="86bc1-104">Para criar uma alternância ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="86bc1-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="86bc1-105">Use o código como o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="86bc1-105">Use code such as the following code example.</span></span> <span data-ttu-id="86bc1-106">Esse código supõe que o formulário contém um <xref:System.Windows.Forms.ToolStrip> controle e que seu <xref:System.Windows.Forms.ToolStrip.Items%2A> coleção contém um <xref:System.Windows.Forms.ToolStripButton> chamado `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="86bc1-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="86bc1-107">Ele também pressupõe que você tenha um manipulador de eventos chamado `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="86bc1-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="86bc1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86bc1-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripButton>  
 [<span data-ttu-id="86bc1-109">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="86bc1-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
