---
title: Como habilitar exibição lado a lado em um controle ListView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 4f51d3a596bc3358942cdfd654b3e4515d96cd07
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960106"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="cd2ae-102">Como habilitar exibição lado a lado em um controle ListView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="cd2ae-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="cd2ae-103">O recurso de exibição de bloco do controle de <xref:System.Windows.Forms.ListView> permite que você forneça um equilíbrio visual entre informações gráficas e textuais.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="cd2ae-104">As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="cd2ae-105">As funções de exibição de bloco em combinação com os recursos de agrupamento ou marca de inserção no controle de <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>

 <span data-ttu-id="cd2ae-106">O modo de exibição lado a lado usa um ícone de 32 x 32 e várias linhas de texto, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>

 <span data-ttu-id="cd2ae-107">![Exibição lado a lado em um controle ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Ícones e texto da exibição lado a lado")</span><span class="sxs-lookup"><span data-stu-id="cd2ae-107">![Tile View in a ListView Control](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>

 <span data-ttu-id="cd2ae-108">Propriedades e métodos de exibição lado a lado permitem especificar quais campos de coluna devem ser exibidos para cada item e controlar coletivamente o tamanho e a aparência de todos os itens dentro de uma janela de exibição lado a lado.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="cd2ae-109">Para maior clareza, a primeira linha do texto em uma exibição lado a lado é sempre o nome do item; isso não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>

 <span data-ttu-id="cd2ae-110">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="cd2ae-111">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cd2ae-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="cd2ae-112">Para definir a exibição lado a lado no designer</span><span class="sxs-lookup"><span data-stu-id="cd2ae-112">To set tile view in the designer</span></span>

1. <span data-ttu-id="cd2ae-113">No Visual Studio, selecione o controle de <xref:System.Windows.Forms.ListView> no formulário.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-113">In Visual Studio, select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>

2. <span data-ttu-id="cd2ae-114">Na janela **Propriedades** , selecione a propriedade <xref:System.Windows.Forms.ListView.View%2A> e escolha **bloco**.</span><span class="sxs-lookup"><span data-stu-id="cd2ae-114">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd2ae-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd2ae-115">See also</span></span>

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="cd2ae-116">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="cd2ae-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
