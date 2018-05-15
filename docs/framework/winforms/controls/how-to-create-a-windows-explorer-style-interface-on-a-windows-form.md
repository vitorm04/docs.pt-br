---
title: Como criar uma interface no estilo do Windows Explorer em Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 2d5b79244d867ea4b6134413d42710b2eadc871e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="8634e-102">Como criar uma interface no estilo do Windows Explorer em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8634e-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="8634e-103">O Windows Explorer é uma opção de interface do usuário comum para aplicativos devido à sua familiaridade pronta.</span><span class="sxs-lookup"><span data-stu-id="8634e-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="8634e-104">O Windows Explorer é, essencialmente, um <xref:System.Windows.Forms.TreeView> controle e um <xref:System.Windows.Forms.ListView> controle em painéis separados.</span><span class="sxs-lookup"><span data-stu-id="8634e-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="8634e-105">Os painéis são redimensionáveis por um divisor.</span><span class="sxs-lookup"><span data-stu-id="8634e-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="8634e-106">Essa disposição de controles é muito eficiente para exibir e procurar informações.</span><span class="sxs-lookup"><span data-stu-id="8634e-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="8634e-107">As etapas a seguir mostram como organizar controles em um formato semelhante ao Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="8634e-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="8634e-108">Elas não mostram como adicionar a funcionalidade de localização de arquivos do aplicativo Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="8634e-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8634e-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="8634e-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8634e-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="8634e-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8634e-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8634e-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="8634e-112">Para criar um Windows Form no estilo do Windows Explorer</span><span class="sxs-lookup"><span data-stu-id="8634e-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1.  <span data-ttu-id="8634e-113">Crie um novo projeto de aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="8634e-113">Create a new Windows Application project.</span></span> <span data-ttu-id="8634e-114">Para obter detalhes, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="8634e-114">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="8634e-115">Na **Caixa de Ferramentas**:</span><span class="sxs-lookup"><span data-stu-id="8634e-115">From the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="8634e-116">Arraste um <xref:System.Windows.Forms.SplitContainer> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="8634e-116">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2.  <span data-ttu-id="8634e-117">Arraste um <xref:System.Windows.Forms.TreeView> controlar em **SplitterPanel1** (o painel do <xref:System.Windows.Forms.SplitContainer> controle marcado **Panel1**).</span><span class="sxs-lookup"><span data-stu-id="8634e-117">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3.  <span data-ttu-id="8634e-118">Arraste um <xref:System.Windows.Forms.ListView> controlar em **SplitterPanel2** (o painel do <xref:System.Windows.Forms.SplitContainer> controle marcado **Panel2**).</span><span class="sxs-lookup"><span data-stu-id="8634e-118">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3.  <span data-ttu-id="8634e-119">Selecione os três controles pressionando a tecla CTRL e clicando neles.</span><span class="sxs-lookup"><span data-stu-id="8634e-119">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="8634e-120">Quando você seleciona o <xref:System.Windows.Forms.SplitContainer> de controle, clique na barra de divisão, em vez dos painéis.</span><span class="sxs-lookup"><span data-stu-id="8634e-120">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8634e-121">Não use o comando **Selecionar Tudo** no menu **Editar**.</span><span class="sxs-lookup"><span data-stu-id="8634e-121">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="8634e-122">Se você fizer isso, a propriedade necessária na próxima etapa não aparecerá na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8634e-122">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="8634e-123">No **propriedades** janela, defina o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="8634e-123">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="8634e-124">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8634e-124">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="8634e-125">O formulário exibe uma interface do usuário de duas partes, semelhante à do Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="8634e-125">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8634e-126">Quando você arrasta o divisor, os painéis são redimensionados.</span><span class="sxs-lookup"><span data-stu-id="8634e-126">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8634e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8634e-127">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="8634e-128">Como criar uma interface do usuário multipainel com o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8634e-128">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [<span data-ttu-id="8634e-129">Como definir o comportamento de redimensionamento e posicionamento em uma janela dividida</span><span class="sxs-lookup"><span data-stu-id="8634e-129">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [<span data-ttu-id="8634e-130">Como dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="8634e-130">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [<span data-ttu-id="8634e-131">Controle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="8634e-131">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
