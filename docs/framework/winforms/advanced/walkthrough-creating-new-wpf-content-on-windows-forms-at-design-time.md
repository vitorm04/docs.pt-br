---
title: 'Passo a passo: criar novo conteúdo WPF no Windows Forms na hora do design'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 889e81053d4e2264755468446a4e1681216ae22e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040370"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="1bbb4-102">Passo a passo: Criar novo conteúdo do WPF em Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="1bbb4-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="1bbb4-103">Este artigo mostra como criar um controle Windows Presentation Foundation (WPF) para uso em seus aplicativos baseados em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

<span data-ttu-id="1bbb4-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="1bbb4-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="1bbb4-105">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-105">Create the project.</span></span>

- <span data-ttu-id="1bbb4-106">Criar um novo controle WPF.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-106">Create a new WPF control.</span></span>

- <span data-ttu-id="1bbb4-107">Adicionar o novo controle WPF a um formulário do Windows Form.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="1bbb4-108">O controle WPF é hospedado em um <xref:System.Windows.Forms.Integration.ElementHost> controle.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bbb4-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1bbb4-109">Prerequisites</span></span>

<span data-ttu-id="1bbb4-110">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="1bbb4-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="1bbb4-111">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1bbb4-111">Visual Studio</span></span>

## <a name="create-the-project"></a><span data-ttu-id="1bbb4-112">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="1bbb4-112">Create the project</span></span>

<span data-ttu-id="1bbb4-113">A primeira etapa é criar o projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-113">The first step is to create the Windows Forms project.</span></span> <span data-ttu-id="1bbb4-114">Abra o Visual Studio e crie um novo projeto de **aplicativo de Windows Forms (.NET Framework)** em C# Visual Basic `HostingWpf`ou Visual chamado.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-114">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="1bbb4-115">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="1bbb4-116">Criar um novo controle WPF</span><span class="sxs-lookup"><span data-stu-id="1bbb4-116">Create a new WPF control</span></span>

<span data-ttu-id="1bbb4-117">Criar um novo controle WPF e adicioná-lo ao projeto é tão fácil quanto adicionar qualquer outro item ao projeto.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-117">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="1bbb4-118">O Designer de Formulários do Windows funciona com um determinado tipo de controle, chamado *controle de composição* ou *controle de usuário*.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-118">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="1bbb4-119">Para obter mais informações sobre controles de usuário do <xref:System.Windows.Controls.UserControl>WPF, consulte.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-119">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="1bbb4-120">O <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> tipo de WPF é diferente do tipo de controle de usuário fornecido pelo Windows Forms, que também é <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>chamado de.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-120">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1bbb4-121">Para criar um novo controle WPF:</span><span class="sxs-lookup"><span data-stu-id="1bbb4-121">To create a new WPF control:</span></span>

1. <span data-ttu-id="1bbb4-122">No **Gerenciador de soluções**, adicione um novo projeto de **.NET Framework (biblioteca de controle de usuário) do WPF** à solução.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-122">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="1bbb4-123">Use o nome padrão da biblioteca de controle, `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-123">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="1bbb4-124">O nome de controle padrão é `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-124">The default control name is `UserControl1.xaml`.</span></span>

     <span data-ttu-id="1bbb4-125">Adicionar o novo controle tem os seguintes efeitos:</span><span class="sxs-lookup"><span data-stu-id="1bbb4-125">Adding the new control has the following effects:</span></span>

    - <span data-ttu-id="1bbb4-126">O arquivo UserControl1.xaml será adicionado.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-126">File UserControl1.xaml is added.</span></span>

    - <span data-ttu-id="1bbb4-127">O arquivo UserControl1.xaml.cs ou UserControl1.xaml.vb será adicionado.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-127">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="1bbb4-128">Este arquivo contém o code-behind para manipuladores de eventos e outras implementações.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-128">This file contains the code-behind for event handlers and other implementation.</span></span>

    - <span data-ttu-id="1bbb4-129">Referências a assemblies WPF serão adicionadas.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-129">References to WPF assemblies are added.</span></span>

    - <span data-ttu-id="1bbb4-130">O arquivo UserControl1.xaml será aberto no [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1bbb4-130">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>

2. <span data-ttu-id="1bbb4-131">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-131">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="1bbb4-132">Para obter mais informações, confira [Como: Selecione e mova elementos no Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1bbb4-132">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="1bbb4-133">Na janela **Propriedades** , defina o valor das <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-133">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="1bbb4-134">Na **caixa de ferramentas**, arraste <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> um controle para a superfície de design.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-134">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="1bbb4-135">Na janela **Propriedades** , defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> Propriedade como **conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-135">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1bbb4-136">No geral, é necessário hospedar conteúdos do WPF mais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-136">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="1bbb4-137">O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-137">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="1bbb4-138">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-138">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="1bbb4-139">Adicionar um controle WPF a um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="1bbb4-139">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="1bbb4-140">O novo controle WPF está pronto para uso no formulário.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-140">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="1bbb4-141">Windows Forms usa o <xref:System.Windows.Forms.Integration.ElementHost> controle para hospedar o conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-141">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="1bbb4-142">Para adicionar um controle WPF a um formulário do Windows:</span><span class="sxs-lookup"><span data-stu-id="1bbb4-142">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="1bbb4-143">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-143">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="1bbb4-144">Na **Caixa de Ferramentas**, localize a guia com o rótulo **Controles de Usuário WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-144">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="1bbb4-145">Arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-145">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="1bbb4-146">Um <xref:System.Windows.Forms.Integration.ElementHost> controle é criado automaticamente no formulário para hospedar o controle WPF.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-146">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="1bbb4-147">O <xref:System.Windows.Forms.Integration.ElementHost> controle é nomeado `elementHost1` e na janela **Propriedades** , você pode ver que sua <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> Propriedade está definida como **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-147">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="1bbb4-148">Referências a assemblies WPF serão adicionadas ao projeto.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-148">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="1bbb4-149">O controle `elementHost1` tem um painel de smart tag que mostra as opções de hospedagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-149">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="1bbb4-150">No painel de smart tag **ElementHost Tasks**, selecione **Encaixar no Contêiner Pai**.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-150">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="1bbb4-151">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-151">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bbb4-152">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="1bbb4-152">Next steps</span></span>

<span data-ttu-id="1bbb4-153">O Windows Forms e o WPF são tecnologias diferentes, mas são projetados para interoperar estreitamente.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-153">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="1bbb4-154">Para fornecer aparência e comportamento mais ricos em seus aplicativos, tente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1bbb4-154">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="1bbb4-155">Hospedar um controle dos Windows Forms em uma página WPF.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-155">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="1bbb4-156">Para obter mais informações, confira [Passo a passo: Hospedagem de um controle de Windows Forms](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)no WPF.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-156">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="1bbb4-157">Aplique estilos visuais dos Windows Forms ao conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-157">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="1bbb4-158">Para obter mais informações, confira [Como: Habilitar estilos visuais em um aplicativo](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)híbrido.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-158">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="1bbb4-159">Altere o estilo do conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-159">Change the style of your WPF content.</span></span> <span data-ttu-id="1bbb4-160">Para obter mais informações, confira [Passo a passo: Estilizando conteúdo](walkthrough-styling-wpf-content.md)do WPF.</span><span class="sxs-lookup"><span data-stu-id="1bbb4-160">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1bbb4-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bbb4-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="1bbb4-162">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="1bbb4-162">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="1bbb4-163">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="1bbb4-163">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="1bbb4-164">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1bbb4-164">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
