---
title: 'Instruções passo a passo: hospedando um controle composto do WPF 3D nos Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: 748ab027fa8206c163578c89b94460665563cbce
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197873"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="67c26-102">Instruções passo a passo: hospedando um controle composto do WPF 3D nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67c26-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="67c26-103">Este tutorial demonstra como você pode criar um controle de composição [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e hospedá-lo em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles e formulários usando o controle de <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="67c26-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="67c26-104">Neste tutorial, você implementará um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> que contém dois controles filho.</span><span class="sxs-lookup"><span data-stu-id="67c26-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="67c26-105">O <xref:System.Windows.Controls.UserControl> exibe um cone tridimensional (3D).</span><span class="sxs-lookup"><span data-stu-id="67c26-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="67c26-106">É muito mais fácil renderizar objetos 3D com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que com [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67c26-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="67c26-107">Portanto, faz sentido hospedar uma classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> para criar gráficos 3D em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67c26-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

<span data-ttu-id="67c26-108">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="67c26-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="67c26-109">Criando o <xref:System.Windows.Controls.UserControl>de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67c26-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

- <span data-ttu-id="67c26-110">Criando o projeto de host do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="67c26-110">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="67c26-111">Hospedando o <xref:System.Windows.Controls.UserControl>de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67c26-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="67c26-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="67c26-112">Prerequisites</span></span>

<span data-ttu-id="67c26-113">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="67c26-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="67c26-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="67c26-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="67c26-115">Criar o UserControl</span><span class="sxs-lookup"><span data-stu-id="67c26-115">Create the UserControl</span></span>

1. <span data-ttu-id="67c26-116">Crie um projeto de **biblioteca de controle de usuário do WPF** chamado `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="67c26-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="67c26-117">Abra UserControl1.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67c26-117">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

3. <span data-ttu-id="67c26-118">Substitua o código gerado pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="67c26-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="67c26-119">Esse código define um <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> que contém dois controles filho.</span><span class="sxs-lookup"><span data-stu-id="67c26-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="67c26-120">O primeiro controle filho é um controle de <xref:System.Windows.Controls.Label?displayProperty=nameWithType>; o segundo é um controle <xref:System.Windows.Controls.Viewport3D> que exibe um cone 3D.</span><span class="sxs-lookup"><span data-stu-id="67c26-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="67c26-121">Criar o projeto de host</span><span class="sxs-lookup"><span data-stu-id="67c26-121">Create the host project</span></span>

1. <span data-ttu-id="67c26-122">Adicione um projeto de **.NET Framework (aplicativo Windows Forms)** chamado `WpfUserControlHost` à solução.</span><span class="sxs-lookup"><span data-stu-id="67c26-122">Add a **Windows Forms App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span>

2. <span data-ttu-id="67c26-123">Em **Gerenciador de soluções**, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado de WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="67c26-123">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="67c26-124">Adicione referências aos assemblies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a seguir:</span><span class="sxs-lookup"><span data-stu-id="67c26-124">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    - <span data-ttu-id="67c26-125">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="67c26-125">PresentationCore</span></span>

    - <span data-ttu-id="67c26-126">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="67c26-126">PresentationFramework</span></span>

    - <span data-ttu-id="67c26-127">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="67c26-127">WindowsBase</span></span>

4. <span data-ttu-id="67c26-128">Adicione uma referência ao projeto `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="67c26-128">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="67c26-129">No Gerenciador de Soluções, defina o projeto `WpfUserControlHost` como o projeto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="67c26-129">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="67c26-130">Hospedar o UserControl</span><span class="sxs-lookup"><span data-stu-id="67c26-130">Host the UserControl</span></span>

1. <span data-ttu-id="67c26-131">No Designer de Formulários do Windows, abra Form1.</span><span class="sxs-lookup"><span data-stu-id="67c26-131">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="67c26-132">No janela Propriedades, clique em **eventos**e clique duas vezes no evento <xref:System.Windows.Forms.Form.Load> para criar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="67c26-132">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="67c26-133">O Editor de Código abre o manipulador de eventos `Form1_Load` recém gerado.</span><span class="sxs-lookup"><span data-stu-id="67c26-133">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="67c26-134">Substitua o código em Form1.cs pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="67c26-134">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="67c26-135">O manipulador de eventos `Form1_Load` cria uma instância de `UserControl1` e adiciona com a coleção de controles filho do controle de <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="67c26-135">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="67c26-136">O controle <xref:System.Windows.Forms.Integration.ElementHost> é adicionado à coleção de controles filho do formulário.</span><span class="sxs-lookup"><span data-stu-id="67c26-136">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="67c26-137">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="67c26-137">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="67c26-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67c26-138">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="67c26-139">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67c26-139">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="67c26-140">Passo a passo: hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67c26-140">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="67c26-141">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="67c26-141">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="67c26-142">Hospedando um controle composto do WPF nos exemplo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67c26-142">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)
