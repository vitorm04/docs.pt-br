---
title: Como adicionar e remover guias com o TabControl dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
ms.openlocfilehash: 89440b083aa6b2dc3f95e0878075a20aeac65b32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525255"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="b3726-102">Como adicionar e remover guias com o TabControl dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="b3726-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="b3726-103">Quando você coloca um <xref:System.Windows.Forms.TabControl> controle no formulário, ele contém duas guias por padrão.</span><span class="sxs-lookup"><span data-stu-id="b3726-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="b3726-104">Você pode adicionar ou remover guias usando o designer.</span><span class="sxs-lookup"><span data-stu-id="b3726-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="b3726-105">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.TabControl> controle.</span><span class="sxs-lookup"><span data-stu-id="b3726-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="b3726-106">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b3726-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3726-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="b3726-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b3726-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="b3726-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b3726-109">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="b3726-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="b3726-110">Para adicionar ou remover uma guia usando o designer</span><span class="sxs-lookup"><span data-stu-id="b3726-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="b3726-111">Na marca inteligente de controle, clique em **Adicionar guia** ou **guia remover**</span><span class="sxs-lookup"><span data-stu-id="b3726-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="b3726-112">-ou-</span><span class="sxs-lookup"><span data-stu-id="b3726-112">-or-</span></span>  
  
     <span data-ttu-id="b3726-113">No **propriedades** janela, clique no **reticências** botão (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de o <xref:System.Windows.Forms.TabControl.TabPages%2A> propriedade para abrir o **TabPage Collection Editor**.</span><span class="sxs-lookup"><span data-stu-id="b3726-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="b3726-114">Clique o **adicionar** ou **remover** botão.</span><span class="sxs-lookup"><span data-stu-id="b3726-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3726-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3726-115">See Also</span></span>  
 [<span data-ttu-id="b3726-116">Controle TabControl</span><span class="sxs-lookup"><span data-stu-id="b3726-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="b3726-117">Visão geral do controle TabControl</span><span class="sxs-lookup"><span data-stu-id="b3726-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="b3726-118">Como adicionar um controle a uma página da guia</span><span class="sxs-lookup"><span data-stu-id="b3726-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="b3726-119">Como desabilitar páginas de guia</span><span class="sxs-lookup"><span data-stu-id="b3726-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="b3726-120">Como alterar a aparência do TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3726-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
