---
title: 'Instruções passo a passo: criando novo conteúdo WPF em Windows Forms na hora do design'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 1ea0160530fea0f35c6d4746dc4bbca9439bc462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529003"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="6b0e0-102">Instruções passo a passo: criando novo conteúdo WPF em Windows Forms na hora do design</span><span class="sxs-lookup"><span data-stu-id="6b0e0-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="6b0e0-103">Este tópico mostra como criar um controle do Windows Presentation Foundation (WPF) para uso em aplicativos baseados nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>  
  
 <span data-ttu-id="6b0e0-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="6b0e0-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="6b0e0-105">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-105">Create the project.</span></span>  
  
-   <span data-ttu-id="6b0e0-106">Criar um novo controle WPF.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-106">Create a new WPF control.</span></span>  
  
-   <span data-ttu-id="6b0e0-107">Adicionar o novo controle WPF a um formulário do Windows Form.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="6b0e0-108">O controle WPF é hospedado em um <xref:System.Windows.Forms.Integration.ElementHost> controle.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b0e0-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6b0e0-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6b0e0-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="6b0e0-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6b0e0-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6b0e0-112">Prerequisites</span></span>  
 <span data-ttu-id="6b0e0-113">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="6b0e0-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="6b0e0-114">.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="6b0e0-115">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="6b0e0-115">Creating the Project</span></span>  
 <span data-ttu-id="6b0e0-116">A primeira etapa é criar o projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b0e0-117">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="6b0e0-118">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="6b0e0-118">To create the project</span></span>  
  
-   <span data-ttu-id="6b0e0-119">Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `HostingWpf`.</span></span>  
  
## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="6b0e0-120">Criar um novo controle WPF</span><span class="sxs-lookup"><span data-stu-id="6b0e0-120">Creating a New WPF Control</span></span>  
 <span data-ttu-id="6b0e0-121">Criar um novo controle WPF e adicioná-lo ao projeto é tão fácil quanto adicionar qualquer outro item ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-121">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="6b0e0-122">O Designer de Formulários do Windows funciona com um determinado tipo de controle, chamado *controle de composição* ou *controle de usuário*.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-122">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="6b0e0-123">Para obter mais informações sobre controles de usuário do WPF, consulte <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-123">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b0e0-124">O <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> de WPF é distinto do tipo de controle de usuário fornecido pelo Windows Forms, que também é chamado de tipo <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-124">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>  
  
#### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="6b0e0-125">Criar um novo controle WPF</span><span class="sxs-lookup"><span data-stu-id="6b0e0-125">To create a new WPF control</span></span>  
  
1.  <span data-ttu-id="6b0e0-126">No **Gerenciador de Soluções**, adicione um novo projeto de **Biblioteca de Controle de Usuário do WPF** à solução.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-126">In **Solution Explorer**, add a new **WPF User Control Library** project to the solution.</span></span> <span data-ttu-id="6b0e0-127">Use o nome padrão da biblioteca de controle, `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-127">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="6b0e0-128">O nome de controle padrão é `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-128">The default control name is `UserControl1.xaml`.</span></span>  
  
     <span data-ttu-id="6b0e0-129">Adicionar o novo controle causa os seguintes efeitos.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-129">Adding the new control has the following effects.</span></span>  
  
    -   <span data-ttu-id="6b0e0-130">O arquivo UserControl1.xaml será adicionado.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-130">File UserControl1.xaml is added.</span></span>  
  
    -   <span data-ttu-id="6b0e0-131">O arquivo UserControl1.xaml.cs ou UserControl1.xaml.vb será adicionado.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-131">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="6b0e0-132">Este arquivo contém o code-behind para manipuladores de eventos e outras implementações.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-132">This file contains the code-behind for event handlers and other implementation.</span></span>  
  
    -   <span data-ttu-id="6b0e0-133">Referências a assemblies WPF serão adicionadas.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-133">References to WPF assemblies are added.</span></span>  
  
    -   <span data-ttu-id="6b0e0-134">O arquivo UserControl1.xaml será aberto no [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b0e0-134">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="6b0e0-135">No modo de exibição de Design, verifique se `UserControl1` está selecionado.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-135">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="6b0e0-136">Para obter mais informações, consulte [Como Selecionar e Mover Elementos na Superfície de Design](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="6b0e0-136">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="6b0e0-137">No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades `200`.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-137">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="6b0e0-138">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-138">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>  
  
5.  <span data-ttu-id="6b0e0-139">No **propriedades** janela, defina o valor da <xref:System.Windows.Controls.TextBox.Text%2A> propriedade **conteúdo hospedado**.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-139">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6b0e0-140">No geral, é necessário hospedar conteúdos do WPF mais sofisticados.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-140">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="6b0e0-141">O <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> controle é usado aqui apenas para fins ilustrativos.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-141">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
6.  <span data-ttu-id="6b0e0-142">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-142">Build the project.</span></span>  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="6b0e0-143">Adicionar um controle WPF a um formulário do Windows Form</span><span class="sxs-lookup"><span data-stu-id="6b0e0-143">Adding a WPF Control to a Windows Form</span></span>  
 <span data-ttu-id="6b0e0-144">O novo controle WPF está pronto para uso no formulário.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-144">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="6b0e0-145">Windows Forms usa o <xref:System.Windows.Forms.Integration.ElementHost> controle para hospedar conteúdo WPF</span><span class="sxs-lookup"><span data-stu-id="6b0e0-145">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content</span></span>  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="6b0e0-146">Adicionar um controle WPF a um formulário do Windows Form</span><span class="sxs-lookup"><span data-stu-id="6b0e0-146">To add a WPF control to a Windows Form</span></span>  
  
1.  <span data-ttu-id="6b0e0-147">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-147">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="6b0e0-148">Na **Caixa de Ferramentas**, localize a guia com o rótulo **Controles de Usuário WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-148">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>  
  
3.  <span data-ttu-id="6b0e0-149">Arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-149">Drag an instance of `UserControl1` onto the form.</span></span>  
  
    -   <span data-ttu-id="6b0e0-150">Um <xref:System.Windows.Forms.Integration.ElementHost> controle é criado automaticamente no formulário para hospedar o controle WPF.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-150">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>  
  
    -   <span data-ttu-id="6b0e0-151">O <xref:System.Windows.Forms.Integration.ElementHost> controle é chamado de `elementHost1` e no **propriedades** janela, você pode ver sua <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> está definida como **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-151">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>  
  
    -   <span data-ttu-id="6b0e0-152">Referências a assemblies WPF serão adicionadas ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-152">References to WPF assemblies are added to the project.</span></span>  
  
    -   <span data-ttu-id="6b0e0-153">O controle `elementHost1` tem um painel de smart tag que mostra as opções de hospedagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-153">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>  
  
4.  <span data-ttu-id="6b0e0-154">No painel de smart tag **ElementHost Tasks**, selecione **Encaixar no Contêiner Pai**.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-154">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>  
  
5.  <span data-ttu-id="6b0e0-155">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-155">Press F5 to build and run the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6b0e0-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6b0e0-156">Next Steps</span></span>  
 <span data-ttu-id="6b0e0-157">O Windows Forms e o WPF são tecnologias diferentes, mas são projetados para interoperar estreitamente.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-157">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="6b0e0-158">Para oferecer uma aparência e um comportamento mais ricos em aplicativos, tente o seguinte.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-158">To provide richer appearance and behavior in your applications, try the following.</span></span>  
  
-   <span data-ttu-id="6b0e0-159">Hospedar um controle dos Windows Forms em uma página WPF.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-159">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="6b0e0-160">Para obter mais informações, consulte [Instruções Passo a Passo: Hospedando um Controle dos Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="6b0e0-160">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
-   <span data-ttu-id="6b0e0-161">Aplique estilos visuais dos Windows Forms ao conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-161">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="6b0e0-162">Para obter mais informações, consulte [Como Habilitar Estilos Visuais em um Aplicativo Híbrido](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="6b0e0-162">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>  
  
-   <span data-ttu-id="6b0e0-163">Altere o estilo do conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="6b0e0-163">Change the style of your WPF content.</span></span> <span data-ttu-id="6b0e0-164">Para obter mais informações, consulte [Instruções Passo a Passo: Definindo o Estilo do Conteúdo do WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="6b0e0-164">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b0e0-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b0e0-165">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="6b0e0-166">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="6b0e0-166">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="6b0e0-167">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="6b0e0-167">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="6b0e0-168">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="6b0e0-168">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
