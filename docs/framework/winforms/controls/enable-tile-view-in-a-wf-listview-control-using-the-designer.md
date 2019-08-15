---
title: 'Como: Habilitar exibição lado a lado em um controle ListView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040358"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="72c60-102">Como: Habilitar exibição lado a lado em um controle ListView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="72c60-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="72c60-103">O recurso de exibição de bloco <xref:System.Windows.Forms.ListView> do controle permite que você forneça um equilíbrio visual entre informações gráficas e textuais.</span><span class="sxs-lookup"><span data-stu-id="72c60-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="72c60-104">As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes.</span><span class="sxs-lookup"><span data-stu-id="72c60-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="72c60-105">As funções de exibição de bloco em combinação com os recursos de agrupamento ou marca <xref:System.Windows.Forms.ListView> de inserção no controle.</span><span class="sxs-lookup"><span data-stu-id="72c60-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>

 <span data-ttu-id="72c60-106">O modo de exibição lado a lado usa um ícone de 32 x 32 e várias linhas de texto, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="72c60-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>

 <span data-ttu-id="72c60-107">![Exibição de bloco em um controle ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Texto e ícones de exibição de bloco")</span><span class="sxs-lookup"><span data-stu-id="72c60-107">![Tile View in a ListView Control](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>

 <span data-ttu-id="72c60-108">Propriedades e métodos de exibição lado a lado permitem especificar quais campos de coluna devem ser exibidos para cada item e controlar coletivamente o tamanho e a aparência de todos os itens dentro de uma janela de exibição lado a lado.</span><span class="sxs-lookup"><span data-stu-id="72c60-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="72c60-109">Para maior clareza, a primeira linha do texto em uma exibição lado a lado é sempre o nome do item; isso não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="72c60-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>

 <span data-ttu-id="72c60-110">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ListView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="72c60-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="72c60-111">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="72c60-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

> [!NOTE]
> <span data-ttu-id="72c60-112">A exibição de bloco está disponível somente [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] em quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> o método.</span><span class="sxs-lookup"><span data-stu-id="72c60-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="72c60-113">Em sistemas operacionais anteriores, qualquer código relacionado à exibição de bloco não tem nenhum efeito e o <xref:System.Windows.Forms.ListView> controle é exibido na exibição de ícones grandes.</span><span class="sxs-lookup"><span data-stu-id="72c60-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="72c60-114">Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72c60-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="72c60-115">Para definir a exibição lado a lado no designer</span><span class="sxs-lookup"><span data-stu-id="72c60-115">To set tile view in the designer</span></span>

1. <span data-ttu-id="72c60-116">No Visual Studio, selecione o <xref:System.Windows.Forms.ListView> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="72c60-116">In Visual Studio, select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>

2. <span data-ttu-id="72c60-117">Na janela **Propriedades** , selecione a <xref:System.Windows.Forms.ListView.View%2A> Propriedade e escolha **bloco**.</span><span class="sxs-lookup"><span data-stu-id="72c60-117">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>

## <a name="see-also"></a><span data-ttu-id="72c60-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72c60-118">See also</span></span>

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="72c60-119">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="72c60-119">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
