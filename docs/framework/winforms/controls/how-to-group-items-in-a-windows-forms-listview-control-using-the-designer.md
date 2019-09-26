---
title: 'Como: Agrupar itens em um controle ListView do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69039406"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="34105-102">Como: Agrupar itens em um controle ListView do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="34105-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="34105-103">O recurso de agrupamento do <xref:System.Windows.Forms.ListView> controle permite que você exiba conjuntos de itens relacionados em grupos.</span><span class="sxs-lookup"><span data-stu-id="34105-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="34105-104">Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo.</span><span class="sxs-lookup"><span data-stu-id="34105-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="34105-105">Você pode usar <xref:System.Windows.Forms.ListView> grupos para facilitar a navegação de listas grandes ao agrupar itens em ordem alfabética, por data ou por qualquer outro agrupamento lógico.</span><span class="sxs-lookup"><span data-stu-id="34105-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="34105-106">A imagem a seguir mostra alguns itens agrupados:</span><span class="sxs-lookup"><span data-stu-id="34105-106">The following image shows some grouped items:</span></span>

![Números separados em grupos ímpares e pares.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="34105-108">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ListView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="34105-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="34105-109">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="34105-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="34105-110">Para habilitar o agrupamento, você deve primeiro criar um ou <xref:System.Windows.Forms.ListViewGroup> mais objetos no designer ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="34105-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="34105-111">Depois que um grupo tiver sido definido, você poderá atribuir itens a ele.</span><span class="sxs-lookup"><span data-stu-id="34105-111">Once a group has been defined, you can assign items to it.</span></span>

> [!NOTE]
> <span data-ttu-id="34105-112"><xref:System.Windows.Forms.ListView>os grupos estão disponíveis somente [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] em quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> o método.</span><span class="sxs-lookup"><span data-stu-id="34105-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="34105-113">Em sistemas operacionais anteriores, nenhum código relacionado a grupos tem efeito e os grupos não serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="34105-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="34105-114">Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34105-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="34105-115">Adicionar ou remover grupos no designer</span><span class="sxs-lookup"><span data-stu-id="34105-115">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="34105-116">Na janela **Propriedades** , clique nas **reticências** (![o botão de reticências (...) no janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) botão ao lado <xref:System.Windows.Forms.ListView.Groups%2A> da propriedade.</span><span class="sxs-lookup"><span data-stu-id="34105-116">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="34105-117">O **Editor de coleção de ListViewGroup** é exibido.</span><span class="sxs-lookup"><span data-stu-id="34105-117">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="34105-118">Para adicionar um grupo, clique no botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="34105-118">To add a group, click the **Add** button.</span></span> <span data-ttu-id="34105-119">Em seguida, você pode definir as propriedades do novo grupo, como <xref:System.Windows.Forms.ListViewGroup.Header%2A> as <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> Propriedades e.</span><span class="sxs-lookup"><span data-stu-id="34105-119">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="34105-120">Para remover um grupo, selecione-o e clique no botão **Remover**.</span><span class="sxs-lookup"><span data-stu-id="34105-120">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="34105-121">Atribuir itens aos grupos no designer</span><span class="sxs-lookup"><span data-stu-id="34105-121">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="34105-122">Na janela **Propriedades** , clique nas **reticências** (![o botão de reticências (...) no janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) botão ao lado <xref:System.Windows.Forms.ListView.Items%2A> da propriedade.</span><span class="sxs-lookup"><span data-stu-id="34105-122">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="34105-123">O **Editor de coleção de ListViewItem** é exibido.</span><span class="sxs-lookup"><span data-stu-id="34105-123">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="34105-124">Para adicionar um novo item, clique no botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="34105-124">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="34105-125">Em seguida, você pode definir as propriedades do novo item, como <xref:System.Windows.Forms.ListViewItem.Text%2A> as <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> Propriedades e.</span><span class="sxs-lookup"><span data-stu-id="34105-125">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="34105-126">Selecione a <xref:System.Windows.Forms.ListViewItem.Group%2A> Propriedade e escolha um grupo na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="34105-126">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="34105-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34105-127">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="34105-128">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="34105-128">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="34105-129">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="34105-129">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="34105-130">Como: Adicionar e remover itens com o controle Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="34105-130">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
