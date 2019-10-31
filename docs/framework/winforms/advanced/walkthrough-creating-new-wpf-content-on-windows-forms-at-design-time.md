---
title: 'Instruções passo a passo: criando novo conteúdo WPF em Windows Forms na hora do design'
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
ms.openlocfilehash: fc6f988d6ffd270eba4abe277ca34fa2eeec56fd
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197429"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="4428e-102">Walkthrough: criar novo conteúdo do WPF em Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="4428e-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="4428e-103">Este artigo mostra como criar um controle Windows Presentation Foundation (WPF) para uso em seus aplicativos baseados em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4428e-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4428e-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4428e-104">Prerequisites</span></span>

<span data-ttu-id="4428e-105">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="4428e-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="4428e-106">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="4428e-106">Create the project</span></span>

<span data-ttu-id="4428e-107">Abra o Visual Studio e crie um novo projeto de **aplicativo de Windows Forms (.NET Framework)** em C# Visual Basic ou Visual chamado `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="4428e-107">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="4428e-108">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4428e-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="4428e-109">Criar um novo controle WPF</span><span class="sxs-lookup"><span data-stu-id="4428e-109">Create a new WPF control</span></span>

<span data-ttu-id="4428e-110">Criar um novo controle WPF e adicioná-lo ao projeto é tão fácil quanto adicionar qualquer outro item ao projeto.</span><span class="sxs-lookup"><span data-stu-id="4428e-110">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="4428e-111">O Designer de Formulários do Windows funciona com um determinado tipo de controle, chamado *controle de composição* ou *controle de usuário*.</span><span class="sxs-lookup"><span data-stu-id="4428e-111">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="4428e-112">Para obter mais informações sobre controles de usuário do WPF, consulte <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="4428e-112">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="4428e-113">O tipo de <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> para WPF é diferente do tipo de controle de usuário fornecido pelo Windows Forms, que também é chamado de <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4428e-113">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4428e-114">Para criar um novo controle WPF:</span><span class="sxs-lookup"><span data-stu-id="4428e-114">To create a new WPF control:</span></span>

1. <span data-ttu-id="4428e-115">No **Gerenciador de soluções**, adicione um novo projeto de **.NET Framework (biblioteca de controle de usuário) do WPF** à solução.</span><span class="sxs-lookup"><span data-stu-id="4428e-115">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="4428e-116">Use o nome padrão da biblioteca de controle, `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="4428e-116">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="4428e-117">O nome de controle padrão é `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="4428e-117">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="4428e-118">Adicionar o novo controle tem os seguintes efeitos:</span><span class="sxs-lookup"><span data-stu-id="4428e-118">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="4428e-119">O arquivo UserControl1.xaml será adicionado.</span><span class="sxs-lookup"><span data-stu-id="4428e-119">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="4428e-120">O arquivo UserControl1.xaml.cs (ou UserControl1. XAML. vb) é adicionado.</span><span class="sxs-lookup"><span data-stu-id="4428e-120">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="4428e-121">Este arquivo contém o code-behind para manipuladores de eventos e outras implementações.</span><span class="sxs-lookup"><span data-stu-id="4428e-121">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="4428e-122">Referências a assemblies WPF serão adicionadas.</span><span class="sxs-lookup"><span data-stu-id="4428e-122">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="4428e-123">O arquivo UserControl1. XAML é aberto no designer do WPF para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4428e-123">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="4428e-124">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="4428e-124">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="4428e-125">Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.</span><span class="sxs-lookup"><span data-stu-id="4428e-125">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="4428e-126">Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> para a superfície de design.</span><span class="sxs-lookup"><span data-stu-id="4428e-126">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="4428e-127">Na janela **Propriedades** , defina o valor da propriedade <xref:System.Windows.Controls.TextBox.Text%2A> como **conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="4428e-127">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="4428e-128">No geral, é necessário hospedar conteúdos do WPF mais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="4428e-128">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="4428e-129">O controle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> é usado aqui apenas para fins ilustrativos.</span><span class="sxs-lookup"><span data-stu-id="4428e-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="4428e-130">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="4428e-130">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="4428e-131">Adicionar um controle WPF a um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="4428e-131">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="4428e-132">O novo controle WPF está pronto para uso no formulário.</span><span class="sxs-lookup"><span data-stu-id="4428e-132">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="4428e-133">Windows Forms usa o controle <xref:System.Windows.Forms.Integration.ElementHost> para hospedar o conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="4428e-133">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="4428e-134">Para adicionar um controle WPF a um formulário do Windows:</span><span class="sxs-lookup"><span data-stu-id="4428e-134">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="4428e-135">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="4428e-135">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="4428e-136">Na **Caixa de Ferramentas**, localize a guia com o rótulo **Controles de Usuário WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="4428e-136">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="4428e-137">Arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="4428e-137">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="4428e-138">Um controle de <xref:System.Windows.Forms.Integration.ElementHost> é criado automaticamente no formulário para hospedar o controle WPF.</span><span class="sxs-lookup"><span data-stu-id="4428e-138">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="4428e-139">O controle <xref:System.Windows.Forms.Integration.ElementHost> é denominado `elementHost1` e, na janela **Propriedades** , você pode ver que sua propriedade <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> está definida como **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="4428e-139">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="4428e-140">Referências a assemblies WPF serão adicionadas ao projeto.</span><span class="sxs-lookup"><span data-stu-id="4428e-140">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="4428e-141">O controle `elementHost1` tem um painel de smart tag que mostra as opções de hospedagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="4428e-141">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="4428e-142">No painel de smart tag **ElementHost Tasks**, selecione **Encaixar no Contêiner Pai**.</span><span class="sxs-lookup"><span data-stu-id="4428e-142">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="4428e-143">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4428e-143">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4428e-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4428e-144">Next steps</span></span>

<span data-ttu-id="4428e-145">O Windows Forms e o WPF são tecnologias diferentes, mas são projetados para interoperar estreitamente.</span><span class="sxs-lookup"><span data-stu-id="4428e-145">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="4428e-146">Para fornecer aparência e comportamento mais ricos em seus aplicativos, tente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4428e-146">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="4428e-147">Hospedar um controle dos Windows Forms em uma página WPF.</span><span class="sxs-lookup"><span data-stu-id="4428e-147">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="4428e-148">Para obter mais informações, consulte [Instruções Passo a Passo: Hospedando um Controle dos Windows Forms no WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="4428e-148">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="4428e-149">Aplique estilos visuais dos Windows Forms ao conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="4428e-149">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="4428e-150">Para obter mais informações, consulte [Como Habilitar Estilos Visuais em um Aplicativo Híbrido](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="4428e-150">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="4428e-151">Altere o estilo do conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="4428e-151">Change the style of your WPF content.</span></span> <span data-ttu-id="4428e-152">Para obter mais informações, consulte [Instruções Passo a Passo: Definindo o Estilo do Conteúdo do WPF](walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="4428e-152">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4428e-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4428e-153">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="4428e-154">Migração e Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="4428e-154">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="4428e-155">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="4428e-155">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="4428e-156">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4428e-156">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
