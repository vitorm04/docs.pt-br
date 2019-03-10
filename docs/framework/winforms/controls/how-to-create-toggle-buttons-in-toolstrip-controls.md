---
title: 'Como: Criar botões de alternância em controles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: a059726ea410e88121a0b755295c3c492c11962a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705513"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="01da9-102">Como: Criar botões de alternância em controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="01da9-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="01da9-103">Quando um usuário clica em um botão de alternância, ele é exibido em baixo-relevo e retém a aparência em baixo-relevo até que o usuário clica no botão novamente.</span><span class="sxs-lookup"><span data-stu-id="01da9-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="01da9-104">Para criar um alternância ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="01da9-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="01da9-105">Use um código como o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="01da9-105">Use code such as the following code example.</span></span> <span data-ttu-id="01da9-106">Esse código supõe que o formulário contém um <xref:System.Windows.Forms.ToolStrip> controle e que seus <xref:System.Windows.Forms.ToolStrip.Items%2A> coleção contém um <xref:System.Windows.Forms.ToolStripButton> chamado `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="01da9-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="01da9-107">Ele também pressupõe que você tenha um manipulador de eventos chamado `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="01da9-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01da9-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01da9-108">See also</span></span>
- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="01da9-109">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="01da9-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
