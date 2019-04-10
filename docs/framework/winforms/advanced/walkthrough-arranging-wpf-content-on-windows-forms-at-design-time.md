---
title: 'Passo a passo: organizar conteúdo WPF no Windows Forms na hora do design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 306c042fe432f0c087ceb1b5ff6b5aec0fe0bbc7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327302"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="23d48-102">Passo a passo: organizar conteúdo WPF no Windows Forms na hora do design</span><span class="sxs-lookup"><span data-stu-id="23d48-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="23d48-103">Esta instrução passo a passo mostra como usar os recursos de layout dos Windows Forms, como ancoragem e guias de alinhamento para organizar controles do WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="23d48-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

 <span data-ttu-id="23d48-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="23d48-104">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="23d48-105">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="23d48-105">Create the project.</span></span>

-   <span data-ttu-id="23d48-106">Crie o controle WPF.</span><span class="sxs-lookup"><span data-stu-id="23d48-106">Create the WPF control.</span></span>

-   <span data-ttu-id="23d48-107">Hospede controles WPF em um painel de layout.</span><span class="sxs-lookup"><span data-stu-id="23d48-107">Host WPF controls in a layout panel.</span></span>

-   <span data-ttu-id="23d48-108">Use guias de alinhamento para alinhar controles WPF.</span><span class="sxs-lookup"><span data-stu-id="23d48-108">Use snaplines to align WPF controls.</span></span>

-   <span data-ttu-id="23d48-109">Ancore e encaixe controles WPF.</span><span class="sxs-lookup"><span data-stu-id="23d48-109">Anchor and dock WPF controls.</span></span>

> [!NOTE]
>  <span data-ttu-id="23d48-110">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="23d48-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="23d48-111">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="23d48-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="23d48-112">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="23d48-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="23d48-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="23d48-113">Prerequisites</span></span>  
 <span data-ttu-id="23d48-114">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="23d48-114">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="23d48-115">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="23d48-115">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="23d48-116">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="23d48-116">Creating the Project</span></span>  
 <span data-ttu-id="23d48-117">A primeira etapa é criar o projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="23d48-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23d48-118">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="23d48-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="23d48-119">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="23d48-119">To create the project</span></span>  
  
-   <span data-ttu-id="23d48-120">Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="23d48-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="23d48-121">Criando o controle WPF</span><span class="sxs-lookup"><span data-stu-id="23d48-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="23d48-122">Depois de adicionar um controle WPF ao projeto, você pode organizá-lo no formulário.</span><span class="sxs-lookup"><span data-stu-id="23d48-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="23d48-123">Para criar controles WPF</span><span class="sxs-lookup"><span data-stu-id="23d48-123">To create WPF controls</span></span>  
  
1. <span data-ttu-id="23d48-124">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao projeto.</span><span class="sxs-lookup"><span data-stu-id="23d48-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="23d48-125">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="23d48-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="23d48-126">Para obter mais informações, confira [Passo a passo: Criando novo conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="23d48-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2. <span data-ttu-id="23d48-127">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="23d48-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="23d48-128">Para obter mais informações, confira [Como: Selecionar e mover elementos na superfície de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="23d48-128">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3. <span data-ttu-id="23d48-129">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades a serem `200`.</span><span class="sxs-lookup"><span data-stu-id="23d48-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4. <span data-ttu-id="23d48-130">Definir o valor de <xref:System.Windows.Controls.Control.Background%2A> propriedade para `Blue`.</span><span class="sxs-lookup"><span data-stu-id="23d48-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5. <span data-ttu-id="23d48-131">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="23d48-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="23d48-132">Hospedando controles WPF em um painel de layout</span><span class="sxs-lookup"><span data-stu-id="23d48-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="23d48-133">Você pode usar controles WPF nos painéis de layout da mesma maneira que você usa outros controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="23d48-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="23d48-134">Para hospedar controles WPF em um painel de layout</span><span class="sxs-lookup"><span data-stu-id="23d48-134">To host WPF controls in a layout panel</span></span>  
  
1. <span data-ttu-id="23d48-135">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="23d48-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="23d48-136">No **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="23d48-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3. <span data-ttu-id="23d48-137">Sobre o <xref:System.Windows.Forms.TableLayoutPanel> painel de smart tag do controle, selecione **Remover última linha**.</span><span class="sxs-lookup"><span data-stu-id="23d48-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4. <span data-ttu-id="23d48-138">Redimensionar o <xref:System.Windows.Forms.TableLayoutPanel> controle para uma largura e altura maior.</span><span class="sxs-lookup"><span data-stu-id="23d48-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5. <span data-ttu-id="23d48-139">No **caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância do `UserControl1` na primeira célula do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="23d48-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="23d48-140">A instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="23d48-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6. <span data-ttu-id="23d48-141">No **caixa de ferramentas**, clique duas vezes em `UserControl1` para criar outra instância na segunda célula do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="23d48-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7. <span data-ttu-id="23d48-142">Na janela **Estrutura de Tópicos do Documento**, selecione `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="23d48-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="23d48-143">Para obter mais informações, consulte a [Janela de Estrutura de Tópicos do Documento](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span><span class="sxs-lookup"><span data-stu-id="23d48-143">For more information, see [Document Outline Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span></span>  
  
8. <span data-ttu-id="23d48-144">No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Control.Padding%2A> propriedade `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="23d48-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="23d48-145">Ambos <xref:System.Windows.Forms.Integration.ElementHost> controles são redimensionados para caber no novo layout.</span><span class="sxs-lookup"><span data-stu-id="23d48-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="23d48-146">Usando guias de alinhamento para alinhar controles WPF</span><span class="sxs-lookup"><span data-stu-id="23d48-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="23d48-147">Guias de alinhamento permitem fácil alinhamento de controles em um formulário.</span><span class="sxs-lookup"><span data-stu-id="23d48-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="23d48-148">Você também pode usar guias de alinhamento para alinhar os controles WPF.</span><span class="sxs-lookup"><span data-stu-id="23d48-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="23d48-149">Para obter mais informações, confira [Passo a passo: Organizando controles nos Windows Forms usando guias de alinhamento](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="23d48-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="23d48-150">Para usar guias de alinhamento para alinhar controles WPF</span><span class="sxs-lookup"><span data-stu-id="23d48-150">To use snaplines to align WPF controls</span></span>  
  
1. <span data-ttu-id="23d48-151">Dos **caixa de ferramentas**, arraste uma instância de `UserControl1` para o formulário e coloque-o no espaço abaixo o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="23d48-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="23d48-152">A instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="23d48-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2. <span data-ttu-id="23d48-153">Usando guias de alinhamento, alinhe a borda esquerda da `elementHost3` com a borda esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="23d48-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3. <span data-ttu-id="23d48-154">Usando guias de alinhamento, dimensione `elementHost3` para a mesma largura que o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="23d48-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4. <span data-ttu-id="23d48-155">Mover `elementHost3` em direção a <xref:System.Windows.Forms.TableLayoutPanel> até que uma guia de alinhamento central apareça entre os controles de controle.</span><span class="sxs-lookup"><span data-stu-id="23d48-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5. <span data-ttu-id="23d48-156">Na janela **Propriedades**, defina o valor da propriedade Margem como `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="23d48-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6. <span data-ttu-id="23d48-157">Mover o `elementHost3` longe o <xref:System.Windows.Forms.TableLayoutPanel> controlar até que o guia de alinhamento central apareça novamente.</span><span class="sxs-lookup"><span data-stu-id="23d48-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="23d48-158">A guia de alinhamento central agora indica uma margem de 20.</span><span class="sxs-lookup"><span data-stu-id="23d48-158">The center snapline now indicates a margin of 20.</span></span>  
  
7. <span data-ttu-id="23d48-159">Mova `elementHost3` para a direita, até que sua borda esquerda se alinhe com a borda esquerda de `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="23d48-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8. <span data-ttu-id="23d48-160">Altere a largura de `elementHost3` até que a borda direita alinhe com a borda direita de `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="23d48-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="23d48-161">Ancorando e encaixando controles WPF</span><span class="sxs-lookup"><span data-stu-id="23d48-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="23d48-162">Um controle WPF hospedado em um formulário tem o mesmo comportamento de ancoragem e encaixe que outros controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="23d48-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="23d48-163">Para ancorar e encaixar controles WPF</span><span class="sxs-lookup"><span data-stu-id="23d48-163">To anchor and dock WPF controls</span></span>  
  
1. <span data-ttu-id="23d48-164">Selecione `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="23d48-164">Select `elementHost1`.</span></span>  
  
2. <span data-ttu-id="23d48-165">No **propriedades** janela, defina as <xref:System.Windows.Forms.Control.Anchor%2A> propriedade **superior, inferior, esquerda, direita**.</span><span class="sxs-lookup"><span data-stu-id="23d48-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3. <span data-ttu-id="23d48-166">Redimensionar o <xref:System.Windows.Forms.TableLayoutPanel> controle para um tamanho maior.</span><span class="sxs-lookup"><span data-stu-id="23d48-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="23d48-167">O controle `elementHost1` será redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="23d48-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4. <span data-ttu-id="23d48-168">Selecione `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="23d48-168">Select `elementHost2`.</span></span>  
  
5. <span data-ttu-id="23d48-169">No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="23d48-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="23d48-170">O controle `elementHost2` será redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="23d48-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6. <span data-ttu-id="23d48-171">Selecione o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="23d48-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7. <span data-ttu-id="23d48-172">Defina o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="23d48-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8. <span data-ttu-id="23d48-173">Selecione `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="23d48-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="23d48-174">Defina o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="23d48-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="23d48-175">O controle `elementHost3` será redimensionado para preencher o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="23d48-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="23d48-176">Redimensione o formulário.</span><span class="sxs-lookup"><span data-stu-id="23d48-176">Resize the form.</span></span>  
  
     <span data-ttu-id="23d48-177">Todos os três <xref:System.Windows.Forms.Integration.ElementHost> controles são redimensionados adequadamente.</span><span class="sxs-lookup"><span data-stu-id="23d48-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="23d48-178">Para obter mais informações, confira [Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="23d48-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d48-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23d48-179">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="23d48-180">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="23d48-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="23d48-181">Como: Alinhar um controle às bordas de formulários no tempo de design</span><span class="sxs-lookup"><span data-stu-id="23d48-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="23d48-182">Passo a passo: Organizar controles nos Windows Forms usando linhas de alinhamento</span><span class="sxs-lookup"><span data-stu-id="23d48-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="23d48-183">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="23d48-183">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="23d48-184">Usando controles WPF</span><span class="sxs-lookup"><span data-stu-id="23d48-184">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="23d48-185">Criar XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="23d48-185">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
