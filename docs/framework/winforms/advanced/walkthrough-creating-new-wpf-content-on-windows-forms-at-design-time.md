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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e5112aa0b025648ce68a93f0f3da026ec99fe89
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987141"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="259e5-102">Passo a passo: Criar novo conteúdo do WPF em Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="259e5-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="259e5-103">Este artigo mostra como criar um controle Windows Presentation Foundation (WPF) para uso em seus aplicativos baseados em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="259e5-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="259e5-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="259e5-104">Prerequisites</span></span>

<span data-ttu-id="259e5-105">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="259e5-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="259e5-106">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="259e5-106">Create the project</span></span>

<span data-ttu-id="259e5-107">Abra o Visual Studio e crie um novo projeto de **aplicativo de Windows Forms (.NET Framework)** em C# Visual Basic `HostingWpf`ou Visual chamado.</span><span class="sxs-lookup"><span data-stu-id="259e5-107">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="259e5-108">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="259e5-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="259e5-109">Criar um novo controle WPF</span><span class="sxs-lookup"><span data-stu-id="259e5-109">Create a new WPF control</span></span>

<span data-ttu-id="259e5-110">Criar um novo controle WPF e adicioná-lo ao projeto é tão fácil quanto adicionar qualquer outro item ao projeto.</span><span class="sxs-lookup"><span data-stu-id="259e5-110">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="259e5-111">O Designer de Formulários do Windows funciona com um determinado tipo de controle, chamado *controle de composição* ou *controle de usuário*.</span><span class="sxs-lookup"><span data-stu-id="259e5-111">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="259e5-112">Para obter mais informações sobre controles de usuário do <xref:System.Windows.Controls.UserControl>WPF, consulte.</span><span class="sxs-lookup"><span data-stu-id="259e5-112">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="259e5-113">O <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> tipo de WPF é diferente do tipo de controle de usuário fornecido pelo Windows Forms, que também é <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>chamado de.</span><span class="sxs-lookup"><span data-stu-id="259e5-113">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="259e5-114">Para criar um novo controle WPF:</span><span class="sxs-lookup"><span data-stu-id="259e5-114">To create a new WPF control:</span></span>

1. <span data-ttu-id="259e5-115">No **Gerenciador de soluções**, adicione um novo projeto de **.NET Framework (biblioteca de controle de usuário) do WPF** à solução.</span><span class="sxs-lookup"><span data-stu-id="259e5-115">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="259e5-116">Use o nome padrão da biblioteca de controle, `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="259e5-116">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="259e5-117">O nome de controle padrão é `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="259e5-117">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="259e5-118">Adicionar o novo controle tem os seguintes efeitos:</span><span class="sxs-lookup"><span data-stu-id="259e5-118">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="259e5-119">O arquivo UserControl1.xaml será adicionado.</span><span class="sxs-lookup"><span data-stu-id="259e5-119">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="259e5-120">O arquivo UserControl1.xaml.cs (ou UserControl1. XAML. vb) é adicionado.</span><span class="sxs-lookup"><span data-stu-id="259e5-120">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="259e5-121">Este arquivo contém o code-behind para manipuladores de eventos e outras implementações.</span><span class="sxs-lookup"><span data-stu-id="259e5-121">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="259e5-122">Referências a assemblies WPF serão adicionadas.</span><span class="sxs-lookup"><span data-stu-id="259e5-122">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="259e5-123">O arquivo UserControl1. XAML é aberto no designer do WPF para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="259e5-123">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="259e5-124">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="259e5-124">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="259e5-125">Na janela **Propriedades** , defina o valor das <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.</span><span class="sxs-lookup"><span data-stu-id="259e5-125">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="259e5-126">Na **caixa de ferramentas**, arraste <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> um controle para a superfície de design.</span><span class="sxs-lookup"><span data-stu-id="259e5-126">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="259e5-127">Na janela **Propriedades** , defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> Propriedade como **conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="259e5-127">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="259e5-128">No geral, é necessário hospedar conteúdos do WPF mais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="259e5-128">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="259e5-129">O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.</span><span class="sxs-lookup"><span data-stu-id="259e5-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="259e5-130">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="259e5-130">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="259e5-131">Adicionar um controle WPF a um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="259e5-131">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="259e5-132">O novo controle WPF está pronto para uso no formulário.</span><span class="sxs-lookup"><span data-stu-id="259e5-132">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="259e5-133">Windows Forms usa o <xref:System.Windows.Forms.Integration.ElementHost> controle para hospedar o conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="259e5-133">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="259e5-134">Para adicionar um controle WPF a um formulário do Windows:</span><span class="sxs-lookup"><span data-stu-id="259e5-134">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="259e5-135">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="259e5-135">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="259e5-136">Na **Caixa de Ferramentas**, localize a guia com o rótulo **Controles de Usuário WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="259e5-136">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="259e5-137">Arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="259e5-137">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="259e5-138">Um <xref:System.Windows.Forms.Integration.ElementHost> controle é criado automaticamente no formulário para hospedar o controle WPF.</span><span class="sxs-lookup"><span data-stu-id="259e5-138">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="259e5-139">O <xref:System.Windows.Forms.Integration.ElementHost> controle é nomeado `elementHost1` e na janela **Propriedades** , você pode ver que sua <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> Propriedade está definida como **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="259e5-139">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="259e5-140">Referências a assemblies WPF serão adicionadas ao projeto.</span><span class="sxs-lookup"><span data-stu-id="259e5-140">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="259e5-141">O controle `elementHost1` tem um painel de smart tag que mostra as opções de hospedagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="259e5-141">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="259e5-142">No painel de smart tag **ElementHost Tasks**, selecione **Encaixar no Contêiner Pai**.</span><span class="sxs-lookup"><span data-stu-id="259e5-142">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="259e5-143">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="259e5-143">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="259e5-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="259e5-144">Next steps</span></span>

<span data-ttu-id="259e5-145">O Windows Forms e o WPF são tecnologias diferentes, mas são projetados para interoperar estreitamente.</span><span class="sxs-lookup"><span data-stu-id="259e5-145">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="259e5-146">Para fornecer aparência e comportamento mais ricos em seus aplicativos, tente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="259e5-146">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="259e5-147">Hospedar um controle dos Windows Forms em uma página WPF.</span><span class="sxs-lookup"><span data-stu-id="259e5-147">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="259e5-148">Para obter mais informações, confira [Passo a passo: Hospedagem de um controle de Windows Forms](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)no WPF.</span><span class="sxs-lookup"><span data-stu-id="259e5-148">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="259e5-149">Aplique estilos visuais dos Windows Forms ao conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="259e5-149">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="259e5-150">Para obter mais informações, confira [Como: Habilitar estilos visuais em um aplicativo](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)híbrido.</span><span class="sxs-lookup"><span data-stu-id="259e5-150">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="259e5-151">Altere o estilo do conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="259e5-151">Change the style of your WPF content.</span></span> <span data-ttu-id="259e5-152">Para obter mais informações, confira [Passo a passo: Estilizando conteúdo](walkthrough-styling-wpf-content.md)do WPF.</span><span class="sxs-lookup"><span data-stu-id="259e5-152">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="259e5-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="259e5-153">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="259e5-154">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="259e5-154">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="259e5-155">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="259e5-155">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="259e5-156">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="259e5-156">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
