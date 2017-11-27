---
title: "Como definir um ícone para um botão ToolBar usando o designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d8bdad3aa17c964871c0d35f6e33b8098f2c649
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="4e6ce-102">Como definir um ícone para um botão ToolBar usando o designer</span><span class="sxs-lookup"><span data-stu-id="4e6ce-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="4e6ce-103">O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="4e6ce-104"><xref:System.Windows.Forms.ToolBar>botões são capazes de exibir ícones dentro delas para facilitar a identificação pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="4e6ce-105">Isso é conseguido por meio da adição de imagens para o <xref:System.Windows.Forms.ImageList> componente e associá-lo com o <xref:System.Windows.Forms.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="4e6ce-106">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ToolBar> controle e um <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="4e6ce-107">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como Criar um Projeto de Aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4e6ce-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e6ce-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4e6ce-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4e6ce-110">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="4e6ce-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="4e6ce-111">Para definir um ícone para um botão de barra de ferramentas em tempo de design</span><span class="sxs-lookup"><span data-stu-id="4e6ce-111">To set an icon for a toolbar button at design time</span></span>  
  
1.  <span data-ttu-id="4e6ce-112">Adicionar imagens para o <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="4e6ce-113">Para obter mais informações, consulte [Como adicionar ou remover imagens ImageList com o designer](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="4e6ce-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2.  <span data-ttu-id="4e6ce-114">Selecione o <xref:System.Windows.Forms.ToolBar> controle do formulário.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3.  <span data-ttu-id="4e6ce-115">No **propriedades** janela, defina o <xref:System.Windows.Forms.ToolBar> do controle <xref:System.Windows.Forms.ToolBar.ImageList%2A> propriedade para o <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="4e6ce-116">Clique o <xref:System.Windows.Forms.ToolBar> do controle <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriedade para selecioná-lo e, em seguida, clique nas reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para abrir o **Editor de coleção de ToolBarButton**.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="4e6ce-117">Use o **adicionar** botão para adicionar os botões para o <xref:System.Windows.Forms.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6.  <span data-ttu-id="4e6ce-118">No **propriedades** que aparece no painel no lado direito da janela de **ToolBarButton Collection Editor**, defina o <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriedade de cada botão da barra de ferramentas para um dos valores na lista, que é desenhada de imagens adicionadas para o <xref:System.Windows.Forms.ImageList> componente.</span><span class="sxs-lookup"><span data-stu-id="4e6ce-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e6ce-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e6ce-119">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="4e6ce-120">Como disparar eventos de menu para botões da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="4e6ce-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="4e6ce-121">Controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="4e6ce-121">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [<span data-ttu-id="4e6ce-122">Componente ImageList</span><span class="sxs-lookup"><span data-stu-id="4e6ce-122">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
