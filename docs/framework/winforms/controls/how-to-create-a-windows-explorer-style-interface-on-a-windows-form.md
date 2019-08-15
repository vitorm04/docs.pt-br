---
title: 'Como: Criar uma interface no estilo do Windows Explorer em Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: db2c5431dfb0156c1508a18ef13d2af80eb4981b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039528"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="79d62-102">Como: Criar uma interface no estilo do Windows Explorer em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79d62-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="79d62-103">O Windows Explorer é uma opção de interface do usuário comum para aplicativos devido à sua familiaridade pronta.</span><span class="sxs-lookup"><span data-stu-id="79d62-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>

 <span data-ttu-id="79d62-104">O Windows Explorer é, essencialmente, <xref:System.Windows.Forms.TreeView> um controle e <xref:System.Windows.Forms.ListView> um controle em painéis separados.</span><span class="sxs-lookup"><span data-stu-id="79d62-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="79d62-105">Os painéis são redimensionáveis por um divisor.</span><span class="sxs-lookup"><span data-stu-id="79d62-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="79d62-106">Essa disposição de controles é muito eficiente para exibir e procurar informações.</span><span class="sxs-lookup"><span data-stu-id="79d62-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>

 <span data-ttu-id="79d62-107">As etapas a seguir mostram como organizar controles em um formato semelhante ao Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="79d62-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="79d62-108">Elas não mostram como adicionar a funcionalidade de localização de arquivos do aplicativo Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="79d62-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>

## <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="79d62-109">Para criar um Windows Form no estilo do Windows Explorer</span><span class="sxs-lookup"><span data-stu-id="79d62-109">To create a Windows Explorer-style Windows Form</span></span>

1. <span data-ttu-id="79d62-110">Criar um novo projeto de aplicativo do Windows (**arquivo** > **novo** > **projeto** > **Visual C#**  ou **Visual Basic** > **área de trabalho clássica**  >  **Windows Forms aplicativo**).</span><span class="sxs-lookup"><span data-stu-id="79d62-110">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="79d62-111">Na **Caixa de Ferramentas**:</span><span class="sxs-lookup"><span data-stu-id="79d62-111">From the **Toolbox**:</span></span>

    1. <span data-ttu-id="79d62-112">Arraste um <xref:System.Windows.Forms.SplitContainer> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="79d62-112">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>

    2. <span data-ttu-id="79d62-113">Arraste um <xref:System.Windows.Forms.TreeView> controle para **SplitterPanel1** ( <xref:System.Windows.Forms.SplitContainer> o painel do controle marcado como **Panel1**).</span><span class="sxs-lookup"><span data-stu-id="79d62-113">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>

    3. <span data-ttu-id="79d62-114">Arraste um <xref:System.Windows.Forms.ListView> controle para **SplitterPanel2** ( <xref:System.Windows.Forms.SplitContainer> o painel do controle marcado como **Panel2**).</span><span class="sxs-lookup"><span data-stu-id="79d62-114">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>

3. <span data-ttu-id="79d62-115">Selecione os três controles pressionando a tecla CTRL e clicando neles.</span><span class="sxs-lookup"><span data-stu-id="79d62-115">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="79d62-116">Ao selecionar o <xref:System.Windows.Forms.SplitContainer> controle, clique na barra de divisão, em vez de nos painéis.</span><span class="sxs-lookup"><span data-stu-id="79d62-116">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="79d62-117">Não use o comando **Selecionar Tudo** no menu **Editar**.</span><span class="sxs-lookup"><span data-stu-id="79d62-117">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="79d62-118">Se você fizer isso, a propriedade necessária na próxima etapa não aparecerá na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="79d62-118">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>

4. <span data-ttu-id="79d62-119">Na janela **Propriedades** , defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="79d62-119">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="79d62-120">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79d62-120">Press F5 to run the application.</span></span>

     <span data-ttu-id="79d62-121">O formulário exibe uma interface do usuário de duas partes, semelhante à do Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="79d62-121">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="79d62-122">Quando você arrasta o divisor, os painéis são redimensionados.</span><span class="sxs-lookup"><span data-stu-id="79d62-122">When you drag the splitter, the panels resize themselves.</span></span>

## <a name="see-also"></a><span data-ttu-id="79d62-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79d62-123">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="79d62-124">Como: Criar uma interface do usuário multipainel com Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79d62-124">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="79d62-125">Como: Definir o comportamento de redimensionamento e posicionamento em uma janela de divisão</span><span class="sxs-lookup"><span data-stu-id="79d62-125">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="79d62-126">Como: Dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="79d62-126">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="79d62-127">Controle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="79d62-127">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
