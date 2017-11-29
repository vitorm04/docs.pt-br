---
title: Como agrupar itens em um controle ListView dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97c9dc3a12227d3c9bfd64c97be61e69b50d2bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="2026a-102">Como agrupar itens em um controle ListView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="2026a-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="2026a-103">O recurso de agrupamento do <xref:System.Windows.Forms.ListView> controle permite que você exibir conjuntos de itens relacionados em grupos.</span><span class="sxs-lookup"><span data-stu-id="2026a-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="2026a-104">Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo.</span><span class="sxs-lookup"><span data-stu-id="2026a-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="2026a-105">Você pode usar <xref:System.Windows.Forms.ListView> grupos para facilitar a navegação listas grandes mais fáceis com o agrupamento de itens em ordem alfabética, por data, ou por qualquer outro grupo lógico.</span><span class="sxs-lookup"><span data-stu-id="2026a-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="2026a-106">A imagem a seguir mostra alguns itens agrupados.</span><span class="sxs-lookup"><span data-stu-id="2026a-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="2026a-107">![Grupos de ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="2026a-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
  
 <span data-ttu-id="2026a-108">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="2026a-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="2026a-109">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como Criar um Projeto de Aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2026a-109">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
 <span data-ttu-id="2026a-110">Para habilitar o agrupamento, você primeiro deve criar um ou mais <xref:System.Windows.Forms.ListViewGroup> objetos no designer ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="2026a-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="2026a-111">Depois que um grupo tiver sido definido, você poderá atribuir itens a ele.</span><span class="sxs-lookup"><span data-stu-id="2026a-111">Once a group has been defined, you can assign items to it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2026a-112"><xref:System.Windows.Forms.ListView>os grupos estão disponíveis apenas em [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando o aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="2026a-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2026a-113">Em sistemas operacionais anteriores, nenhum código relacionado a grupos tem efeito e os grupos não serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="2026a-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="2026a-114">Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2026a-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="2026a-115">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="2026a-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2026a-116">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="2026a-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2026a-117">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="2026a-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="2026a-118">Adicionar ou remover grupos no designer</span><span class="sxs-lookup"><span data-stu-id="2026a-118">To add or remove groups in the designer</span></span>  
  
1.  <span data-ttu-id="2026a-119">No **propriedades** janela, clique no **reticências** (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) próximo ao o <xref:System.Windows.Forms.ListView.Groups%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2026a-119">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>  
  
     <span data-ttu-id="2026a-120">O **Editor de coleção de ListViewGroup** é exibido.</span><span class="sxs-lookup"><span data-stu-id="2026a-120">The **ListViewGroup Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="2026a-121">Para adicionar um grupo, clique no botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2026a-121">To add a group, click the **Add** button.</span></span> <span data-ttu-id="2026a-122">Você pode definir propriedades do novo grupo, como o <xref:System.Windows.Forms.ListViewGroup.Header%2A> e <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="2026a-122">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="2026a-123">Para remover um grupo, selecione-o e clique no botão **Remover**.</span><span class="sxs-lookup"><span data-stu-id="2026a-123">To remove a group, select it and click the **Remove** button.</span></span>  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="2026a-124">Atribuir itens aos grupos no designer</span><span class="sxs-lookup"><span data-stu-id="2026a-124">To assign items to groups in the designer</span></span>  
  
1.  <span data-ttu-id="2026a-125">No **propriedades** janela, clique no **reticências** (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) próximo ao o <xref:System.Windows.Forms.ListView.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2026a-125">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="2026a-126">O **Editor de coleção de ListViewItem** é exibido.</span><span class="sxs-lookup"><span data-stu-id="2026a-126">The **ListViewItem Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="2026a-127">Para adicionar um novo item, clique no botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2026a-127">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="2026a-128">Você pode definir propriedades do novo item, como o <xref:System.Windows.Forms.ListViewItem.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="2026a-128">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
3.  <span data-ttu-id="2026a-129">Selecione o <xref:System.Windows.Forms.ListViewItem.Group%2A> propriedade e escolha um grupo na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="2026a-129">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2026a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2026a-130">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="2026a-131">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="2026a-131">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="2026a-132">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="2026a-132">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="2026a-133">Recursos do Windows XP e controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2026a-133">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="2026a-134">Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2026a-134">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
