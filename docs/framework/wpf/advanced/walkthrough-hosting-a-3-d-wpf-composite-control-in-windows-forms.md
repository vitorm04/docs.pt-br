---
title: 'Instruções passo a passo: hospedando um controle composto do WPF 3D nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: a9aca5d1aff1057d85509be517bb352b4b27bf9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="73cd8-102">Instruções passo a passo: hospedando um controle composto do WPF 3D nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73cd8-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>
<span data-ttu-id="73cd8-103">Este passo a passo demonstra como você pode criar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composto controlar e hospedá-lo em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles e formulários usando o <xref:System.Windows.Forms.Integration.ElementHost> controle.</span><span class="sxs-lookup"><span data-stu-id="73cd8-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
 <span data-ttu-id="73cd8-104">Neste passo a passo, você irá implementar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> que contém dois controles filho.</span><span class="sxs-lookup"><span data-stu-id="73cd8-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="73cd8-105">O <xref:System.Windows.Controls.UserControl> exibe um cone tridimensional (3D).</span><span class="sxs-lookup"><span data-stu-id="73cd8-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="73cd8-106">É muito mais fácil renderizar objetos 3D com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que com [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73cd8-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="73cd8-107">Portanto, faz sentido para hospedar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> classe para criar gráficos 3D em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73cd8-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="73cd8-108">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="73cd8-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="73cd8-109">Criando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="73cd8-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
-   <span data-ttu-id="73cd8-110">Criando o projeto de host do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="73cd8-110">Creating the Windows Forms host project.</span></span>  
  
-   <span data-ttu-id="73cd8-111">Hospedando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="73cd8-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
 <span data-ttu-id="73cd8-112">Para ver uma listagem de código completa das tarefas ilustradas nesta instrução passo a passo, consulte [Exemplo de hospedagem de um controle composto 3D do WPF no Windows Forms](http://go.microsoft.com/fwlink/?LinkID=160001).</span><span class="sxs-lookup"><span data-stu-id="73cd8-112">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a 3-D WPF Composite Control in Windows Forms Sample](http://go.microsoft.com/fwlink/?LinkID=160001).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="73cd8-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="73cd8-113">Prerequisites</span></span>  
 <span data-ttu-id="73cd8-114">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="73cd8-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="73cd8-115">.</span><span class="sxs-lookup"><span data-stu-id="73cd8-115">.</span></span>  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a><span data-ttu-id="73cd8-116">Criando o UserControl</span><span class="sxs-lookup"><span data-stu-id="73cd8-116">Creating the UserControl</span></span>  
  
#### <a name="to-create-the-usercontrol"></a><span data-ttu-id="73cd8-117">Criar o UserControl</span><span class="sxs-lookup"><span data-stu-id="73cd8-117">To create the UserControl</span></span>  
  
1.  <span data-ttu-id="73cd8-118">Criar um projeto de biblioteca de controle de usuário de WPF chamada `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="73cd8-118">Create a WPF User Control Library project named `HostingWpfUserControlInWf`.</span></span>  
  
2.  <span data-ttu-id="73cd8-119">Abra UserControl1.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73cd8-119">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
3.  <span data-ttu-id="73cd8-120">Substitua o código gerado pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="73cd8-120">Replace the generated code with the following code.</span></span>  
  
     <span data-ttu-id="73cd8-121">Esse código define uma <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> que contém dois controles filho.</span><span class="sxs-lookup"><span data-stu-id="73cd8-121">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="73cd8-122">O primeiro controle filho é um <xref:System.Windows.Controls.Label?displayProperty=nameWithType> controle; o segundo é um <xref:System.Windows.Controls.Viewport3D> controle que exibe um cone 3D.</span><span class="sxs-lookup"><span data-stu-id="73cd8-122">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="73cd8-123">Criando o projeto de host do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73cd8-123">Creating the Windows Forms Host Project</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="73cd8-124">Criar o projeto de host</span><span class="sxs-lookup"><span data-stu-id="73cd8-124">To create the host project</span></span>  
  
1.  <span data-ttu-id="73cd8-125">Adicione um projeto de Aplicativos do Windows chamado `WpfUserControlHost` à solução.</span><span class="sxs-lookup"><span data-stu-id="73cd8-125">Add a Windows application project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="73cd8-126">Para obter mais informações, consulte [Como criar um novo projeto de aplicativo do WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="73cd8-126">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="73cd8-127">No Gerenciador de Soluções, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado de WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="73cd8-127">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="73cd8-128">Adicione referências aos assemblies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a seguir:</span><span class="sxs-lookup"><span data-stu-id="73cd8-128">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>  
  
    -   <span data-ttu-id="73cd8-129">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="73cd8-129">PresentationCore</span></span>  
  
    -   <span data-ttu-id="73cd8-130">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="73cd8-130">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="73cd8-131">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="73cd8-131">WindowsBase</span></span>  
  
4.  <span data-ttu-id="73cd8-132">Adicione uma referência ao projeto `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="73cd8-132">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>  
  
5.  <span data-ttu-id="73cd8-133">No Gerenciador de Soluções, defina o projeto `WpfUserControlHost` como o projeto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="73cd8-133">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a><span data-ttu-id="73cd8-134">Hospedando o UserControl do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="73cd8-134">Hosting the Windows Presentation Foundation UserControl</span></span>  
  
#### <a name="to-host-the-usercontrol"></a><span data-ttu-id="73cd8-135">Hospedar o UserControl</span><span class="sxs-lookup"><span data-stu-id="73cd8-135">To host the UserControl</span></span>  
  
1.  <span data-ttu-id="73cd8-136">No Designer de Formulários do Windows, abra Form1.</span><span class="sxs-lookup"><span data-stu-id="73cd8-136">In the Windows Forms Designer, open Form1.</span></span>  
  
2.  <span data-ttu-id="73cd8-137">Na janela Propriedades, clique em **eventos**e, em seguida, clique duas vezes o <xref:System.Windows.Forms.Form.Load> evento para criar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="73cd8-137">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>  
  
     <span data-ttu-id="73cd8-138">O Editor de Código abre o manipulador de eventos `Form1_Load` recém gerado.</span><span class="sxs-lookup"><span data-stu-id="73cd8-138">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>  
  
3.  <span data-ttu-id="73cd8-139">Substitua o código em Form1.cs pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="73cd8-139">Replace the code in Form1.cs with the following code.</span></span>  
  
     <span data-ttu-id="73cd8-140">O `Form1_Load` manipulador de eventos cria uma instância de `UserControl1` e adiciona a forma de <xref:System.Windows.Forms.Integration.ElementHost> coleção de controles filho do controle.</span><span class="sxs-lookup"><span data-stu-id="73cd8-140">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="73cd8-141">O <xref:System.Windows.Forms.Integration.ElementHost> controle é adicionado à coleção do formulário de controles filho.</span><span class="sxs-lookup"><span data-stu-id="73cd8-141">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="73cd8-142">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="73cd8-142">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cd8-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73cd8-143">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="73cd8-144">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="73cd8-144">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="73cd8-145">Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73cd8-145">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="73cd8-146">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="73cd8-146">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="73cd8-147">Hospedando um controle composto do WPF nos exemplo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73cd8-147">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160001)
