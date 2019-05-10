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
ms.openlocfilehash: a8f690438136450cb12dbcf5e17ddfcca617457e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211439"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="47bcb-102">Passo a passo: Organizar o conteúdo do WPF nos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="47bcb-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="47bcb-103">Esta instrução passo a passo mostra como usar os recursos de layout dos Windows Forms, como ancoragem e guias de alinhamento para organizar controles do WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="47bcb-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

<span data-ttu-id="47bcb-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="47bcb-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="47bcb-105">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="47bcb-105">Create the project.</span></span>

- <span data-ttu-id="47bcb-106">Crie o controle WPF.</span><span class="sxs-lookup"><span data-stu-id="47bcb-106">Create the WPF control.</span></span>

- <span data-ttu-id="47bcb-107">Hospede controles WPF em um painel de layout.</span><span class="sxs-lookup"><span data-stu-id="47bcb-107">Host WPF controls in a layout panel.</span></span>

- <span data-ttu-id="47bcb-108">Use guias de alinhamento para alinhar controles WPF.</span><span class="sxs-lookup"><span data-stu-id="47bcb-108">Use snaplines to align WPF controls.</span></span>

- <span data-ttu-id="47bcb-109">Ancore e encaixe controles WPF.</span><span class="sxs-lookup"><span data-stu-id="47bcb-109">Anchor and dock WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47bcb-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="47bcb-110">Prerequisites</span></span>

<span data-ttu-id="47bcb-111">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="47bcb-111">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="47bcb-112">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="47bcb-112">Create the project</span></span>

<span data-ttu-id="47bcb-113">Abra o Visual Studio e crie um novo projeto de aplicativo do Windows Forms no Visual Basic ou Visual C# nomeado `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-113">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="47bcb-114">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="47bcb-114">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="47bcb-115">Criar o controle WPF</span><span class="sxs-lookup"><span data-stu-id="47bcb-115">Create the WPF control</span></span>

<span data-ttu-id="47bcb-116">Depois de adicionar um controle WPF ao projeto, você pode organizá-lo no formulário.</span><span class="sxs-lookup"><span data-stu-id="47bcb-116">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="47bcb-117">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao projeto.</span><span class="sxs-lookup"><span data-stu-id="47bcb-117">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="47bcb-118">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="47bcb-119">Para obter mais informações, confira [Passo a passo: Criando novo conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="47bcb-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="47bcb-120">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="47bcb-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="47bcb-121">Para obter mais informações, confira [Como: Selecionar e mover elementos na superfície de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="47bcb-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="47bcb-122">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades a serem `200`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="47bcb-123">Definir o valor de <xref:System.Windows.Controls.Control.Background%2A> propriedade para `Blue`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-123">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

5. <span data-ttu-id="47bcb-124">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="47bcb-124">Build the project.</span></span>

## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="47bcb-125">Hospedando controles WPF em um painel de layout</span><span class="sxs-lookup"><span data-stu-id="47bcb-125">Hosting WPF Controls in a Layout Panel</span></span>
 <span data-ttu-id="47bcb-126">Você pode usar controles WPF nos painéis de layout da mesma maneira que você usa outros controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="47bcb-126">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="47bcb-127">Para hospedar controles WPF em um painel de layout</span><span class="sxs-lookup"><span data-stu-id="47bcb-127">To host WPF controls in a layout panel</span></span>

1. <span data-ttu-id="47bcb-128">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="47bcb-128">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="47bcb-129">No **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="47bcb-129">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="47bcb-130">Sobre o <xref:System.Windows.Forms.TableLayoutPanel> painel de smart tag do controle, selecione **Remover última linha**.</span><span class="sxs-lookup"><span data-stu-id="47bcb-130">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="47bcb-131">Redimensionar o <xref:System.Windows.Forms.TableLayoutPanel> controle para uma largura e altura maior.</span><span class="sxs-lookup"><span data-stu-id="47bcb-131">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="47bcb-132">No **caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância do `UserControl1` na primeira célula do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="47bcb-132">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="47bcb-133">A instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="47bcb-134">No **caixa de ferramentas**, clique duas vezes em `UserControl1` para criar outra instância na segunda célula do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="47bcb-134">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="47bcb-135">Na janela **Estrutura de Tópicos do Documento**, selecione `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-135">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="47bcb-136">Para obter mais informações, consulte a [Janela de Estrutura de Tópicos do Documento](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span><span class="sxs-lookup"><span data-stu-id="47bcb-136">For more information, see [Document Outline Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span></span>

8. <span data-ttu-id="47bcb-137">No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Control.Padding%2A> propriedade `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-137">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>

     <span data-ttu-id="47bcb-138">Ambos <xref:System.Windows.Forms.Integration.ElementHost> controles são redimensionados para caber no novo layout.</span><span class="sxs-lookup"><span data-stu-id="47bcb-138">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="47bcb-139">Usando guias de alinhamento para alinhar controles WPF</span><span class="sxs-lookup"><span data-stu-id="47bcb-139">Using Snaplines to Align WPF Controls</span></span>
 <span data-ttu-id="47bcb-140">Guias de alinhamento permitem fácil alinhamento de controles em um formulário.</span><span class="sxs-lookup"><span data-stu-id="47bcb-140">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="47bcb-141">Você também pode usar guias de alinhamento para alinhar os controles WPF.</span><span class="sxs-lookup"><span data-stu-id="47bcb-141">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="47bcb-142">Para obter mais informações, confira [Passo a passo: Organizando controles nos Windows Forms usando guias de alinhamento](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="47bcb-142">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="47bcb-143">Para usar guias de alinhamento para alinhar controles WPF</span><span class="sxs-lookup"><span data-stu-id="47bcb-143">To use snaplines to align WPF controls</span></span>

1. <span data-ttu-id="47bcb-144">Dos **caixa de ferramentas**, arraste uma instância de `UserControl1` para o formulário e coloque-o no espaço abaixo o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="47bcb-144">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="47bcb-145">A instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-145">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="47bcb-146">Usando guias de alinhamento, alinhe a borda esquerda da `elementHost3` com a borda esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="47bcb-146">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="47bcb-147">Usando guias de alinhamento, dimensione `elementHost3` para a mesma largura que o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="47bcb-147">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="47bcb-148">Mover `elementHost3` em direção a <xref:System.Windows.Forms.TableLayoutPanel> até que uma guia de alinhamento central apareça entre os controles de controle.</span><span class="sxs-lookup"><span data-stu-id="47bcb-148">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="47bcb-149">Na janela **Propriedades**, defina o valor da propriedade Margem como `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-149">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>

6. <span data-ttu-id="47bcb-150">Mover o `elementHost3` longe o <xref:System.Windows.Forms.TableLayoutPanel> controlar até que o guia de alinhamento central apareça novamente.</span><span class="sxs-lookup"><span data-stu-id="47bcb-150">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="47bcb-151">A guia de alinhamento central agora indica uma margem de 20.</span><span class="sxs-lookup"><span data-stu-id="47bcb-151">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="47bcb-152">Mova `elementHost3` para a direita, até que sua borda esquerda se alinhe com a borda esquerda de `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-152">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="47bcb-153">Altere a largura de `elementHost3` até que a borda direita alinhe com a borda direita de `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-153">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="47bcb-154">Ancorando e encaixando controles WPF</span><span class="sxs-lookup"><span data-stu-id="47bcb-154">Anchoring and Docking WPF Controls</span></span>
 <span data-ttu-id="47bcb-155">Um controle WPF hospedado em um formulário tem o mesmo comportamento de ancoragem e encaixe que outros controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="47bcb-155">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="47bcb-156">Para ancorar e encaixar controles WPF</span><span class="sxs-lookup"><span data-stu-id="47bcb-156">To anchor and dock WPF controls</span></span>

1. <span data-ttu-id="47bcb-157">Selecione `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-157">Select `elementHost1`.</span></span>

2. <span data-ttu-id="47bcb-158">No **propriedades** janela, defina as <xref:System.Windows.Forms.Control.Anchor%2A> propriedade **superior, inferior, esquerda, direita**.</span><span class="sxs-lookup"><span data-stu-id="47bcb-158">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="47bcb-159">Redimensionar o <xref:System.Windows.Forms.TableLayoutPanel> controle para um tamanho maior.</span><span class="sxs-lookup"><span data-stu-id="47bcb-159">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

     <span data-ttu-id="47bcb-160">O controle `elementHost1` será redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="47bcb-160">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="47bcb-161">Selecione `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-161">Select `elementHost2`.</span></span>

5. <span data-ttu-id="47bcb-162">No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="47bcb-162">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="47bcb-163">O controle `elementHost2` será redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="47bcb-163">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="47bcb-164">Selecione o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="47bcb-164">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="47bcb-165">Defina o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="47bcb-165">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="47bcb-166">Selecione `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="47bcb-166">Select `elementHost3`.</span></span>

9. <span data-ttu-id="47bcb-167">Defina o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="47bcb-167">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="47bcb-168">O controle `elementHost3` será redimensionado para preencher o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="47bcb-168">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="47bcb-169">Redimensione o formulário.</span><span class="sxs-lookup"><span data-stu-id="47bcb-169">Resize the form.</span></span>

     <span data-ttu-id="47bcb-170">Todos os três <xref:System.Windows.Forms.Integration.ElementHost> controles são redimensionados adequadamente.</span><span class="sxs-lookup"><span data-stu-id="47bcb-170">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

     <span data-ttu-id="47bcb-171">Para obter mais informações, confira [Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="47bcb-171">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47bcb-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47bcb-172">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="47bcb-173">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="47bcb-173">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="47bcb-174">Como: Alinhar um controle às bordas de formulários no tempo de Design</span><span class="sxs-lookup"><span data-stu-id="47bcb-174">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="47bcb-175">Passo a passo: Organizando controles nos formulários do Windows usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="47bcb-175">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="47bcb-176">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="47bcb-176">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="47bcb-177">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="47bcb-177">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="47bcb-178">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47bcb-178">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
