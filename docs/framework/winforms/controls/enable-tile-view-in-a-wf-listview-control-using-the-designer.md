---
title: "Como habilitar exibição lado a lado em um controle ListView dos Windows Forms usando o designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72fc1212e6e154cf3459d9ae6b94b6a8965fb151
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="69457-102">Como habilitar exibição lado a lado em um controle ListView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="69457-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="69457-103">O recurso de exibição lado a lado do <xref:System.Windows.Forms.ListView> controle permite que você fornecer um equilíbrio visual entre informações gráficas e textuais.</span><span class="sxs-lookup"><span data-stu-id="69457-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="69457-104">As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes.</span><span class="sxs-lookup"><span data-stu-id="69457-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="69457-105">Funções de exibição lado a lado em combinação com o agrupamento ou inserção marcar recursos o <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="69457-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="69457-106">O modo de exibição lado a lado usa um ícone de 32 x 32 e várias linhas de texto, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="69457-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>  
  
 <span data-ttu-id="69457-107">![Exibição lado a lado em um controle ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="69457-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
  
 <span data-ttu-id="69457-108">Propriedades e métodos de exibição lado a lado permitem especificar quais campos de coluna devem ser exibidos para cada item e controlar coletivamente o tamanho e a aparência de todos os itens dentro de uma janela de exibição lado a lado.</span><span class="sxs-lookup"><span data-stu-id="69457-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="69457-109">Para maior clareza, a primeira linha do texto em uma exibição lado a lado é sempre o nome do item; isso não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="69457-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>  
  
 <span data-ttu-id="69457-110">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="69457-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="69457-111">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="69457-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69457-112">A exibição lado a lado está disponível apenas em [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando o aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="69457-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="69457-113">Em sistemas operacionais anteriores, qualquer código relacionado ao modo de exibição lado a lado não tem efeito e o <xref:System.Windows.Forms.ListView> controle exibe no modo de exibição ícones grandes.</span><span class="sxs-lookup"><span data-stu-id="69457-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="69457-114">Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="69457-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="69457-115">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="69457-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="69457-116">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="69457-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="69457-117">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="69457-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="69457-118">Para definir a exibição lado a lado no designer</span><span class="sxs-lookup"><span data-stu-id="69457-118">To set tile view in the designer</span></span>  
  
1.  <span data-ttu-id="69457-119">Selecione o <xref:System.Windows.Forms.ListView> controle do formulário.</span><span class="sxs-lookup"><span data-stu-id="69457-119">Select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>  
  
2.  <span data-ttu-id="69457-120">No **propriedades** janela, selecione o <xref:System.Windows.Forms.ListView.View%2A> propriedade e escolha **bloco**.</span><span class="sxs-lookup"><span data-stu-id="69457-120">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69457-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69457-121">See Also</span></span>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="69457-122">Recursos do Windows XP e controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69457-122">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="69457-123">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="69457-123">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
