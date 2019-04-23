---
title: 'Como: Adicionar um controle a uma página da guia'
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
ms.openlocfilehash: 9806583fda60f1cb8a5ef2d97f42eba158593f61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322713"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="d49b7-102">Como: Adicionar um controle a uma página da guia</span><span class="sxs-lookup"><span data-stu-id="d49b7-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="d49b7-103">Você pode usar os formulários do Windows <xref:System.Windows.Forms.TabControl> para exibir outros controles de forma organizada.</span><span class="sxs-lookup"><span data-stu-id="d49b7-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="d49b7-104">O procedimento a seguir mostra como adicionar um botão para a primeira guia. Para obter informações sobre como adicionar um ícone à parte do rótulo de uma página da guia, consulte [como: Alterar a aparência do TabControl dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="d49b7-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="d49b7-105">Para adicionar um controle de forma programática</span><span class="sxs-lookup"><span data-stu-id="d49b7-105">To add a control programmatically</span></span>  
  
1. <span data-ttu-id="d49b7-106">Use o <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> método de coleção retornada pela <xref:System.Windows.Forms.Control.Controls%2A> propriedade de <xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="d49b7-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d49b7-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d49b7-107">See also</span></span>

- [<span data-ttu-id="d49b7-108">Controle TabControl</span><span class="sxs-lookup"><span data-stu-id="d49b7-108">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="d49b7-109">Visão geral do controle TabControl</span><span class="sxs-lookup"><span data-stu-id="d49b7-109">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="d49b7-110">Como: Alterar a aparência do TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d49b7-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="d49b7-111">Como: Desabilitar páginas de guia</span><span class="sxs-lookup"><span data-stu-id="d49b7-111">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="d49b7-112">Como: Adicionar e remover guias com o TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d49b7-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
