---
title: Como adicionar um controle a uma página da guia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 1bb2233cf9e288ae89ebb8cab3df4f6451dc8eed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="ad1dd-102">Como adicionar um controle a uma página da guia</span><span class="sxs-lookup"><span data-stu-id="ad1dd-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="ad1dd-103">Você pode usar o Windows Forms <xref:System.Windows.Forms.TabControl> para exibir outros controles de forma organizada.</span><span class="sxs-lookup"><span data-stu-id="ad1dd-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="ad1dd-104">O procedimento a seguir mostra como adicionar um botão à guia primeiro. Para obter informações sobre como adicionar um ícone à parte do rótulo de uma página da guia, veja [Como alterar a aparência do TabControl dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="ad1dd-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="ad1dd-105">Para adicionar um controle programaticamente</span><span class="sxs-lookup"><span data-stu-id="ad1dd-105">To add a control programmatically</span></span>  
  
1.  <span data-ttu-id="ad1dd-106">Use o <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> método da coleção retornada pelo <xref:System.Windows.Forms.Control.Controls%2A> propriedade <xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="ad1dd-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ad1dd-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad1dd-107">See Also</span></span>  
 [<span data-ttu-id="ad1dd-108">Controle TabControl</span><span class="sxs-lookup"><span data-stu-id="ad1dd-108">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="ad1dd-109">Visão geral do controle TabControl</span><span class="sxs-lookup"><span data-stu-id="ad1dd-109">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="ad1dd-110">Como alterar a aparência do TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad1dd-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="ad1dd-111">Como desabilitar páginas de guia</span><span class="sxs-lookup"><span data-stu-id="ad1dd-111">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="ad1dd-112">Como adicionar e remover guias com o TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad1dd-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
