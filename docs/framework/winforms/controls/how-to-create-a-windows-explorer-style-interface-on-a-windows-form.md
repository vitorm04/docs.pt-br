---
title: 'Como: Criar uma interface no estilo do Windows Explorer em Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: dd70feaba29e29748ac56729632fa359582a6914
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327367"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="97ad5-102">Como: Criar uma interface no estilo do Windows Explorer em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97ad5-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="97ad5-103">O Windows Explorer é uma opção de interface do usuário comum para aplicativos devido à sua familiaridade pronta.</span><span class="sxs-lookup"><span data-stu-id="97ad5-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="97ad5-104">Windows Explorer é, essencialmente, uma <xref:System.Windows.Forms.TreeView> controle e um <xref:System.Windows.Forms.ListView> controle em painéis separados.</span><span class="sxs-lookup"><span data-stu-id="97ad5-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="97ad5-105">Os painéis são redimensionáveis por um divisor.</span><span class="sxs-lookup"><span data-stu-id="97ad5-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="97ad5-106">Essa disposição de controles é muito eficiente para exibir e procurar informações.</span><span class="sxs-lookup"><span data-stu-id="97ad5-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="97ad5-107">As etapas a seguir mostram como organizar controles em um formato semelhante ao Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="97ad5-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="97ad5-108">Elas não mostram como adicionar a funcionalidade de localização de arquivos do aplicativo Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="97ad5-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97ad5-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="97ad5-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="97ad5-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="97ad5-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="97ad5-111">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="97ad5-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="97ad5-112">Para criar um Windows Form no estilo do Windows Explorer</span><span class="sxs-lookup"><span data-stu-id="97ad5-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1. <span data-ttu-id="97ad5-113">Criar um novo projeto de aplicativo do Windows (**arquivo** > **New** > **projeto** > **Visual C#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).</span><span class="sxs-lookup"><span data-stu-id="97ad5-113">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2. <span data-ttu-id="97ad5-114">Na **Caixa de Ferramentas**:</span><span class="sxs-lookup"><span data-stu-id="97ad5-114">From the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="97ad5-115">Arraste um <xref:System.Windows.Forms.SplitContainer> controle para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="97ad5-115">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2.  <span data-ttu-id="97ad5-116">Arraste uma <xref:System.Windows.Forms.TreeView> controlar em **SplitterPanel1** (o painel do <xref:System.Windows.Forms.SplitContainer> controle marcado **Painel1**).</span><span class="sxs-lookup"><span data-stu-id="97ad5-116">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3.  <span data-ttu-id="97ad5-117">Arraste uma <xref:System.Windows.Forms.ListView> controlar em **SplitterPanel2** (o painel do <xref:System.Windows.Forms.SplitContainer> controle marcado **Painel2**).</span><span class="sxs-lookup"><span data-stu-id="97ad5-117">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3. <span data-ttu-id="97ad5-118">Selecione os três controles pressionando a tecla CTRL e clicando neles.</span><span class="sxs-lookup"><span data-stu-id="97ad5-118">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="97ad5-119">Quando você seleciona o <xref:System.Windows.Forms.SplitContainer> de controle, clique na barra de divisão, em vez dos painéis.</span><span class="sxs-lookup"><span data-stu-id="97ad5-119">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="97ad5-120">Não use o comando **Selecionar Tudo** no menu **Editar**.</span><span class="sxs-lookup"><span data-stu-id="97ad5-120">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="97ad5-121">Se você fizer isso, a propriedade necessária na próxima etapa não aparecerá na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="97ad5-121">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="97ad5-122">No **propriedades** janela, defina as <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="97ad5-122">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5. <span data-ttu-id="97ad5-123">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97ad5-123">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="97ad5-124">O formulário exibe uma interface do usuário de duas partes, semelhante à do Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="97ad5-124">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="97ad5-125">Quando você arrasta o divisor, os painéis são redimensionados.</span><span class="sxs-lookup"><span data-stu-id="97ad5-125">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97ad5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97ad5-126">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="97ad5-127">Como: Criar uma Interface do usuário Multipainel com Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97ad5-127">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="97ad5-128">Como: Definir redimensionamento e posicionamento de comportamento em uma janela dividida</span><span class="sxs-lookup"><span data-stu-id="97ad5-128">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="97ad5-129">Como: Dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="97ad5-129">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="97ad5-130">Controle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="97ad5-130">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
