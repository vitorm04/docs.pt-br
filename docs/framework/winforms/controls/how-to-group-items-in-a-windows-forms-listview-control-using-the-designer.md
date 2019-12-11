---
title: Como agrupar itens em um controle ListView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 03958109d4daa3fc369660de66973bb659e29c60
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960183"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="7a8a2-102">Como agrupar itens em um controle ListView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="7a8a2-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="7a8a2-103">O recurso de agrupamento do controle de <xref:System.Windows.Forms.ListView> permite que você exiba conjuntos de itens relacionados em grupos.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="7a8a2-104">Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="7a8a2-105">Você pode usar grupos de <xref:System.Windows.Forms.ListView> para facilitar a navegação de listas grandes ao agrupar itens em ordem alfabética, por data ou por qualquer outro agrupamento lógico.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="7a8a2-106">A imagem a seguir mostra alguns itens agrupados:</span><span class="sxs-lookup"><span data-stu-id="7a8a2-106">The following image shows some grouped items:</span></span>

![Números separados em grupos ímpares e pares.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="7a8a2-108">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="7a8a2-109">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7a8a2-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="7a8a2-110">Para habilitar o agrupamento, você deve primeiro criar um ou mais objetos <xref:System.Windows.Forms.ListViewGroup> no designer ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="7a8a2-111">Depois que um grupo tiver sido definido, você poderá atribuir itens a ele.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-111">Once a group has been defined, you can assign items to it.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="7a8a2-112">Adicionar ou remover grupos no designer</span><span class="sxs-lookup"><span data-stu-id="7a8a2-112">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="7a8a2-113">Na janela **Propriedades** , clique nas **reticências** (![botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-113">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="7a8a2-114">O **Editor de coleção de ListViewGroup** é exibido.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-114">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="7a8a2-115">Para adicionar um grupo, clique no botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-115">To add a group, click the **Add** button.</span></span> <span data-ttu-id="7a8a2-116">Em seguida, você pode definir as propriedades do novo grupo, como as propriedades <xref:System.Windows.Forms.ListViewGroup.Header%2A> e <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-116">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="7a8a2-117">Para remover um grupo, selecione-o e clique no botão **Remover**.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-117">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="7a8a2-118">Atribuir itens aos grupos no designer</span><span class="sxs-lookup"><span data-stu-id="7a8a2-118">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="7a8a2-119">Na janela **Propriedades** , clique nas **reticências** (![botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-119">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="7a8a2-120">O **Editor de coleção de ListViewItem** é exibido.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-120">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="7a8a2-121">Para adicionar um novo item, clique no botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-121">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="7a8a2-122">Em seguida, você pode definir as propriedades do novo item, como as propriedades <xref:System.Windows.Forms.ListViewItem.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-122">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="7a8a2-123">Selecione a propriedade <xref:System.Windows.Forms.ListViewItem.Group%2A> e escolha um grupo na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="7a8a2-123">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a8a2-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a8a2-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="7a8a2-125">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="7a8a2-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="7a8a2-126">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="7a8a2-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="7a8a2-127">Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a8a2-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
