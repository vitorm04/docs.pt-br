---
title: "Instruções passo a passo: hospedando um controle ActiveX no WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 25944b3dd28c0bce2646c06ec424b54acc8b8a1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="98bda-102">Instruções passo a passo: hospedando um controle ActiveX no WPF</span><span class="sxs-lookup"><span data-stu-id="98bda-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="98bda-103">Para permitir uma melhor interação com navegadores, você pode usar controles [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] nos seus aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98bda-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="98bda-104">Essa instrução passo a passo demonstra como você pode hospedar o [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] como um controle em uma página [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98bda-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>  
  
 <span data-ttu-id="98bda-105">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="98bda-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="98bda-106">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="98bda-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="98bda-107">Criando o controle ActiveX.</span><span class="sxs-lookup"><span data-stu-id="98bda-107">Creating the ActiveX control.</span></span>  
  
-   <span data-ttu-id="98bda-108">Hospedando o controle ActiveX em uma página do WPF.</span><span class="sxs-lookup"><span data-stu-id="98bda-108">Hosting the ActiveX control on a WPF Page.</span></span>  
  
 <span data-ttu-id="98bda-109">Quando concluir este passo a passo, você entenderá como usar controles [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] no seu aplicativo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98bda-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="98bda-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="98bda-110">Prerequisites</span></span>  
 <span data-ttu-id="98bda-111">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="98bda-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]<span data-ttu-id="98bda-112"> instalado no computador no qual [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] está instalado.</span><span class="sxs-lookup"><span data-stu-id="98bda-112"> installed on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="98bda-113">.</span><span class="sxs-lookup"><span data-stu-id="98bda-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="98bda-114">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="98bda-114">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="98bda-115">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="98bda-115">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="98bda-116">Crie um projeto de aplicativo WPF chamado `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="98bda-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>  
  
2.  <span data-ttu-id="98bda-117">Adicione um projeto de biblioteca de controle do Windows Forms à solução e nomeie-o como `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="98bda-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>  
  
3.  <span data-ttu-id="98bda-118">No projeto WmpAxLib, adicione uma referência ao assembly do Windows Media Player, que é chamado wmp.dll.</span><span class="sxs-lookup"><span data-stu-id="98bda-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>  
  
4.  <span data-ttu-id="98bda-119">Abra a **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="98bda-119">Open the **Toolbox**.</span></span>  
  
5.  <span data-ttu-id="98bda-120">Clique com o botão direito do mouse na **Caixa de ferramentas** e, em seguida, clique em **Escolher Itens**.</span><span class="sxs-lookup"><span data-stu-id="98bda-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>  
  
6.  <span data-ttu-id="98bda-121">Clique na guia **Componentes COM**, selecione o controle **Windows Media Player** e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="98bda-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>  
  
     <span data-ttu-id="98bda-122">O controle do Windows Media Player é adicionado para à **Caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="98bda-122">The Windows Media Player control is added to the **Toolbox**.</span></span>  
  
7.  <span data-ttu-id="98bda-123">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo **UserControl1** e, em seguida, clique em **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="98bda-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>  
  
8.  <span data-ttu-id="98bda-124">Altere o nome para `WmpAxControl.vb` ou `WmpAxControl.cs`, dependendo da linguagem.</span><span class="sxs-lookup"><span data-stu-id="98bda-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>  
  
9. <span data-ttu-id="98bda-125">Se for solicitado que você renomeie todas as referências, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="98bda-125">If you are prompted to rename all references, click **Yes**.</span></span>  
  
## <a name="creating-the-activex-control"></a><span data-ttu-id="98bda-126">Criando o controle ActiveX</span><span class="sxs-lookup"><span data-stu-id="98bda-126">Creating the ActiveX Control</span></span>  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]<span data-ttu-id="98bda-127">gera automaticamente um <xref:System.Windows.Forms.AxHost> classe wrapper para um [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controlar quando o controle é adicionado a uma superfície de design.</span><span class="sxs-lookup"><span data-stu-id="98bda-127"> automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="98bda-128">O procedimento a seguir cria um assembly gerenciado chamado AxInterop.WMPLib.dll.</span><span class="sxs-lookup"><span data-stu-id="98bda-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>  
  
#### <a name="to-create-the-activex-control"></a><span data-ttu-id="98bda-129">Criar o controle ActiveX</span><span class="sxs-lookup"><span data-stu-id="98bda-129">To create the ActiveX control</span></span>  
  
1.  <span data-ttu-id="98bda-130">Abra WmpAxControl.vb ou WmpAxControl.cs no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="98bda-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="98bda-131">Na **Caixa de ferramentas**, adicione o controle do Windows Media Player para a superfície de design.</span><span class="sxs-lookup"><span data-stu-id="98bda-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>  
  
3.  <span data-ttu-id="98bda-132">Na janela Propriedades, defina o valor do controle do Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="98bda-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
4.  <span data-ttu-id="98bda-133">Compile o projeto de biblioteca do controle WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="98bda-133">Build the WmpAxLib control library project.</span></span>  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="98bda-134">Hospedando o controle ActiveX em uma página do WPF</span><span class="sxs-lookup"><span data-stu-id="98bda-134">Hosting the ActiveX Control on a WPF Page</span></span>  
  
#### <a name="to-host-the-activex-control"></a><span data-ttu-id="98bda-135">Hospedar o controle ActiveX</span><span class="sxs-lookup"><span data-stu-id="98bda-135">To host the ActiveX control</span></span>  
  
1.  <span data-ttu-id="98bda-136">No projeto HostingAxInWpf, adicione uma referência ao assembly de interoperabilidade [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] gerado.</span><span class="sxs-lookup"><span data-stu-id="98bda-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>  
  
     <span data-ttu-id="98bda-137">Esse assembly é chamado AxInterop.WMPLib.dll e foi adicionado à pasta Debug do projeto WmpAxLib quando você importou o controle do Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="98bda-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>  
  
2.  <span data-ttu-id="98bda-138">Adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="98bda-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="98bda-139">Adicione uma referência ao assembly [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], que é chamado de System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="98bda-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>  
  
4.  <span data-ttu-id="98bda-140">Abra o MainWindow.xaml no WPF Designer.</span><span class="sxs-lookup"><span data-stu-id="98bda-140">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
5.  <span data-ttu-id="98bda-141">Nome do <xref:System.Windows.Controls.Grid> elemento `grid1`.</span><span class="sxs-lookup"><span data-stu-id="98bda-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  <span data-ttu-id="98bda-142">No modo de Design ou modo de exibição XAML, selecione o <xref:System.Windows.Window> elemento.</span><span class="sxs-lookup"><span data-stu-id="98bda-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
7.  <span data-ttu-id="98bda-143">Na janela Propriedades, clique na guia **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="98bda-143">In the Properties window, click the **Events** tab.</span></span>  
  
8.  <span data-ttu-id="98bda-144">Clique duas vezes o <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="98bda-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
9. <span data-ttu-id="98bda-145">Insira o seguinte código para manipular o <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="98bda-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     <span data-ttu-id="98bda-146">Esse código cria uma instância do <xref:System.Windows.Forms.Integration.WindowsFormsHost> controlar e adiciona uma instância do `AxWindowsMediaPlayer` controle como seu filho.</span><span class="sxs-lookup"><span data-stu-id="98bda-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="98bda-147">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98bda-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98bda-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98bda-148">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="98bda-149">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="98bda-149">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="98bda-150">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="98bda-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="98bda-151">Passo a passo: hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98bda-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
