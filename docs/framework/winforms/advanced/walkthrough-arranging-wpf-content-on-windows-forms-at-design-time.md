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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658518"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="ec46c-102">Passo a passo: Organizar o conteúdo do WPF em Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="ec46c-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="ec46c-103">Este artigo mostra como usar os recursos de layout de Windows Forms, como ancoragem e snaplines, para organizar os controles de Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ec46c-103">This article shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec46c-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ec46c-104">Prerequisites</span></span>

<span data-ttu-id="ec46c-105">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ec46c-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="ec46c-106">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="ec46c-106">Create the project</span></span>

<span data-ttu-id="ec46c-107">Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou `ArrangeElementHost`Visual chamado.</span><span class="sxs-lookup"><span data-stu-id="ec46c-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="ec46c-108">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ec46c-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="ec46c-109">Criar o controle WPF</span><span class="sxs-lookup"><span data-stu-id="ec46c-109">Create the WPF control</span></span>

<span data-ttu-id="ec46c-110">Depois de adicionar um controle WPF ao projeto, você pode organizá-lo no formulário.</span><span class="sxs-lookup"><span data-stu-id="ec46c-110">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="ec46c-111">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ec46c-111">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="ec46c-112">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="ec46c-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="ec46c-113">Para obter mais informações, confira [Passo a passo: Criando novo conteúdo do WPF em Windows Forms em tempo](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de design.</span><span class="sxs-lookup"><span data-stu-id="ec46c-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="ec46c-114">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="ec46c-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="ec46c-115">Na janela **Propriedades** , defina o valor das <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.</span><span class="sxs-lookup"><span data-stu-id="ec46c-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="ec46c-116">Defina o valor da <xref:System.Windows.Controls.Control.Background%2A> Propriedade como **azul**.</span><span class="sxs-lookup"><span data-stu-id="ec46c-116">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

5. <span data-ttu-id="ec46c-117">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="ec46c-117">Build the project.</span></span>

## <a name="host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="ec46c-118">Hospedar controles WPF em um painel de layout</span><span class="sxs-lookup"><span data-stu-id="ec46c-118">Host WPF controls in a layout panel</span></span>

<span data-ttu-id="ec46c-119">Você pode usar controles WPF nos painéis de layout da mesma maneira que você usa outros controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ec46c-119">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

1. <span data-ttu-id="ec46c-120">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="ec46c-120">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="ec46c-121">Na **caixa de ferramentas**, arraste <xref:System.Windows.Forms.TableLayoutPanel> um controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="ec46c-121">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="ec46c-122">No painel de marcas inteligentes do controle,selecioneremoverúltimalinha.<xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="ec46c-122">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="ec46c-123">Redimensione o <xref:System.Windows.Forms.TableLayoutPanel> controle para uma largura e altura maiores.</span><span class="sxs-lookup"><span data-stu-id="ec46c-123">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="ec46c-124">Na **caixa de ferramentas**, `UserControl1` clique duas vezes para criar uma instância do `UserControl1` na primeira célula do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="ec46c-124">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="ec46c-125">A instância do `UserControl1` é hospedada em um <xref:System.Windows.Forms.Integration.ElementHost> novo controle `elementHost1`chamado.</span><span class="sxs-lookup"><span data-stu-id="ec46c-125">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="ec46c-126">Na **caixa de ferramentas**, clique `UserControl1` duas vezes para criar outra instância na <xref:System.Windows.Forms.TableLayoutPanel> segunda célula do controle.</span><span class="sxs-lookup"><span data-stu-id="ec46c-126">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="ec46c-127">Na janela **Estrutura de Tópicos do Documento**, selecione `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="ec46c-127">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span>

8. <span data-ttu-id="ec46c-128">Na janela **Propriedades** , defina o valor da <xref:System.Windows.Forms.Control.Padding%2A> Propriedade como **10, 10, 10, 10**.</span><span class="sxs-lookup"><span data-stu-id="ec46c-128">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to **10, 10, 10, 10**.</span></span>

   <span data-ttu-id="ec46c-129">Ambos <xref:System.Windows.Forms.Integration.ElementHost> os controles são redimensionados para caber no novo layout.</span><span class="sxs-lookup"><span data-stu-id="ec46c-129">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="ec46c-130">Usar snaplines para alinhar controles WPF</span><span class="sxs-lookup"><span data-stu-id="ec46c-130">Use snaplines to align WPF controls</span></span>

<span data-ttu-id="ec46c-131">Guias de alinhamento permitem fácil alinhamento de controles em um formulário.</span><span class="sxs-lookup"><span data-stu-id="ec46c-131">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="ec46c-132">Você também pode usar guias de alinhamento para alinhar os controles WPF.</span><span class="sxs-lookup"><span data-stu-id="ec46c-132">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="ec46c-133">Para obter mais informações, confira [Passo a passo: Organizando controles em Windows Forms usando Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="ec46c-133">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

1. <span data-ttu-id="ec46c-134">Na **caixa de ferramentas**, arraste uma instância `UserControl1` do para o formulário e coloque-a no espaço abaixo do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="ec46c-134">From the **Toolbox**, drag an instance of `UserControl1` onto the form, and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="ec46c-135">A instância do `UserControl1` é hospedada em um <xref:System.Windows.Forms.Integration.ElementHost> novo controle `elementHost3`chamado.</span><span class="sxs-lookup"><span data-stu-id="ec46c-135">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="ec46c-136">Usando Snaplines, alinhe a borda esquerda de `elementHost3` com a borda esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="ec46c-136">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="ec46c-137">Usando Snaplines, dimensione o tamanho `elementHost3` para a mesma largura do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="ec46c-137">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="ec46c-138">Mover `elementHost3` para o <xref:System.Windows.Forms.TableLayoutPanel> controle até que uma SnapLine central apareça entre os controles.</span><span class="sxs-lookup"><span data-stu-id="ec46c-138">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="ec46c-139">Na janela **Propriedades** , defina o valor da propriedade Margin como **20, 20, 20, 20**.</span><span class="sxs-lookup"><span data-stu-id="ec46c-139">In the **Properties** window, set the value of the Margin property to **20, 20, 20, 20**.</span></span>

6. <span data-ttu-id="ec46c-140">Mova a `elementHost3` distância <xref:System.Windows.Forms.TableLayoutPanel> do controle até que a SnapLine do centro seja exibida novamente.</span><span class="sxs-lookup"><span data-stu-id="ec46c-140">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="ec46c-141">A guia de alinhamento central agora indica uma margem de 20.</span><span class="sxs-lookup"><span data-stu-id="ec46c-141">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="ec46c-142">Mova `elementHost3` para a direita até que sua borda esquerda fique alinhada com a borda `elementHost1`esquerda de.</span><span class="sxs-lookup"><span data-stu-id="ec46c-142">Move `elementHost3` to the right until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="ec46c-143">Altere a largura de `elementHost3` até que a borda direita alinhe com a borda direita de `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="ec46c-143">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchor-and-dock-wpf-controls"></a><span data-ttu-id="ec46c-144">Ancorar e encaixar controles WPF</span><span class="sxs-lookup"><span data-stu-id="ec46c-144">Anchor and dock WPF controls</span></span>

<span data-ttu-id="ec46c-145">Um controle WPF hospedado em um formulário tem o mesmo comportamento de ancoragem e encaixe que outros controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ec46c-145">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

1. <span data-ttu-id="ec46c-146">Selecione `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="ec46c-146">Select `elementHost1`.</span></span>

2. <span data-ttu-id="ec46c-147">Na janela **Propriedades** , defina a <xref:System.Windows.Forms.Control.Anchor%2A> Propriedade como **superior, inferior, esquerda, direita**.</span><span class="sxs-lookup"><span data-stu-id="ec46c-147">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="ec46c-148">Redimensione o <xref:System.Windows.Forms.TableLayoutPanel> controle para um tamanho maior.</span><span class="sxs-lookup"><span data-stu-id="ec46c-148">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

   <span data-ttu-id="ec46c-149">O controle `elementHost1` será redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="ec46c-149">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="ec46c-150">Selecione `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="ec46c-150">Select `elementHost2`.</span></span>

5. <span data-ttu-id="ec46c-151">Na janela **Propriedades** , defina o valor da <xref:System.Windows.Forms.Control.Dock%2A> Propriedade como. <xref:System.Windows.Forms.DockStyle.Fill></span><span class="sxs-lookup"><span data-stu-id="ec46c-151">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="ec46c-152">O controle `elementHost2` será redimensionado para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="ec46c-152">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="ec46c-153">Selecione o controle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="ec46c-153">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="ec46c-154">Defina o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="ec46c-154">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="ec46c-155">Selecione `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="ec46c-155">Select `elementHost3`.</span></span>

9. <span data-ttu-id="ec46c-156">Defina o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="ec46c-156">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="ec46c-157">O controle `elementHost3` será redimensionado para preencher o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="ec46c-157">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="ec46c-158">Redimensione o formulário.</span><span class="sxs-lookup"><span data-stu-id="ec46c-158">Resize the form.</span></span>

    <span data-ttu-id="ec46c-159">Todos os <xref:System.Windows.Forms.Integration.ElementHost> três controles são redimensionados adequadamente.</span><span class="sxs-lookup"><span data-stu-id="ec46c-159">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

    <span data-ttu-id="ec46c-160">Para obter mais informações, confira [Como: Ancorar e encaixar controles filho](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)em um controle TableLayoutPanel.</span><span class="sxs-lookup"><span data-stu-id="ec46c-160">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec46c-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec46c-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="ec46c-162">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ec46c-162">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="ec46c-163">Como: Alinhar um controle às bordas dos formulários no tempo de design</span><span class="sxs-lookup"><span data-stu-id="ec46c-163">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="ec46c-164">Passo a passo: Organizando controles em Windows Forms usando Snaplines</span><span class="sxs-lookup"><span data-stu-id="ec46c-164">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="ec46c-165">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ec46c-165">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="ec46c-166">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="ec46c-166">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="ec46c-167">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec46c-167">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
