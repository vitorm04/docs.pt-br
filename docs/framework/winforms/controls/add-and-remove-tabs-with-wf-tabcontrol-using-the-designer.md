---
title: Como adicionar e remover guias com o TabControl dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e603e420be2c5be6174fab3876008fdf73c8459
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="fc77b-102">Como adicionar e remover guias com o TabControl dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="fc77b-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="fc77b-103">Quando você coloca um <xref:System.Windows.Forms.TabControl> controle no formulário, ele contém duas guias por padrão.</span><span class="sxs-lookup"><span data-stu-id="fc77b-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="fc77b-104">Você pode adicionar ou remover guias usando o designer.</span><span class="sxs-lookup"><span data-stu-id="fc77b-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="fc77b-105">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.TabControl> controle.</span><span class="sxs-lookup"><span data-stu-id="fc77b-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="fc77b-106">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fc77b-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc77b-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="fc77b-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fc77b-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="fc77b-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fc77b-109">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="fc77b-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="fc77b-110">Para adicionar ou remover uma guia usando o designer</span><span class="sxs-lookup"><span data-stu-id="fc77b-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="fc77b-111">Na marca inteligente de controle, clique em **Adicionar guia** ou **guia remover**</span><span class="sxs-lookup"><span data-stu-id="fc77b-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="fc77b-112">-ou-</span><span class="sxs-lookup"><span data-stu-id="fc77b-112">-or-</span></span>  
  
     <span data-ttu-id="fc77b-113">No **propriedades** janela, clique no **reticências** botão (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de o <xref:System.Windows.Forms.TabControl.TabPages%2A> propriedade para abrir o **TabPage Collection Editor**.</span><span class="sxs-lookup"><span data-stu-id="fc77b-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="fc77b-114">Clique o **adicionar** ou **remover** botão.</span><span class="sxs-lookup"><span data-stu-id="fc77b-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc77b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc77b-115">See Also</span></span>  
 [<span data-ttu-id="fc77b-116">Controle TabControl</span><span class="sxs-lookup"><span data-stu-id="fc77b-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="fc77b-117">Visão geral do controle TabControl</span><span class="sxs-lookup"><span data-stu-id="fc77b-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="fc77b-118">Como adicionar um controle a uma página da guia</span><span class="sxs-lookup"><span data-stu-id="fc77b-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="fc77b-119">Como desabilitar páginas de guia</span><span class="sxs-lookup"><span data-stu-id="fc77b-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="fc77b-120">Como alterar a aparência do TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc77b-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
