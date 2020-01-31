---
title: Hospedar controle composto WPF 3D no Windows Forms
titleSuffix: ''
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: aaa726ac90fd75a12054c18be6ec08a1372c1128
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794204"
---
# <a name="walkthrough-host-a-3d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="d8050-102">Walkthrough: hospedar um controle composto do WPF 3D no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8050-102">Walkthrough: Host a 3D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="d8050-103">Este tutorial demonstra como você pode criar um controle de composição [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e hospedá-lo em Windows Forms controles e formulários usando o controle de <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="d8050-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in Windows Forms controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="d8050-104">Neste tutorial, você implementará um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> que contém dois controles filho.</span><span class="sxs-lookup"><span data-stu-id="d8050-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="d8050-105">O <xref:System.Windows.Controls.UserControl> exibe um cone tridimensional (3D).</span><span class="sxs-lookup"><span data-stu-id="d8050-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3D) cone.</span></span> <span data-ttu-id="d8050-106">A renderização de objetos 3D é muito mais fácil com a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do que com Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d8050-106">Rendering 3D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with Windows Forms.</span></span> <span data-ttu-id="d8050-107">Portanto, faz sentido hospedar uma classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> para criar gráficos 3D em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d8050-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3D graphics in Windows Forms.</span></span>

<span data-ttu-id="d8050-108">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="d8050-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="d8050-109">Criando o <xref:System.Windows.Controls.UserControl>de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8050-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

- <span data-ttu-id="d8050-110">Criando o projeto de host do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d8050-110">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="d8050-111">Hospedando o <xref:System.Windows.Controls.UserControl>de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8050-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d8050-112">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d8050-112">Prerequisites</span></span>

<span data-ttu-id="d8050-113">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="d8050-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="d8050-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d8050-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="d8050-115">Criar o UserControl</span><span class="sxs-lookup"><span data-stu-id="d8050-115">Create the UserControl</span></span>

1. <span data-ttu-id="d8050-116">Crie um projeto de **biblioteca de controle de usuário do WPF** chamado `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="d8050-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="d8050-117">Abra UserControl1. XAML no designer do WPF.</span><span class="sxs-lookup"><span data-stu-id="d8050-117">Open UserControl1.xaml in the WPF Designer.</span></span>

3. <span data-ttu-id="d8050-118">Substitua o código gerado pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d8050-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="d8050-119">Esse código define um <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> que contém dois controles filho.</span><span class="sxs-lookup"><span data-stu-id="d8050-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="d8050-120">O primeiro controle filho é um controle de <xref:System.Windows.Controls.Label?displayProperty=nameWithType>; o segundo é um controle <xref:System.Windows.Controls.Viewport3D> que exibe um cone 3D.</span><span class="sxs-lookup"><span data-stu-id="d8050-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="d8050-121">Criar o projeto de host</span><span class="sxs-lookup"><span data-stu-id="d8050-121">Create the host project</span></span>

1. <span data-ttu-id="d8050-122">Adicione um projeto de **.NET Framework (aplicativo Windows Forms)** chamado `WpfUserControlHost` à solução.</span><span class="sxs-lookup"><span data-stu-id="d8050-122">Add a **Windows Forms App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span>

2. <span data-ttu-id="d8050-123">Em **Gerenciador de soluções**, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado de WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="d8050-123">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="d8050-124">Adicione referências aos assemblies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a seguir:</span><span class="sxs-lookup"><span data-stu-id="d8050-124">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    - <span data-ttu-id="d8050-125">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="d8050-125">PresentationCore</span></span>

    - <span data-ttu-id="d8050-126">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="d8050-126">PresentationFramework</span></span>

    - <span data-ttu-id="d8050-127">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="d8050-127">WindowsBase</span></span>

4. <span data-ttu-id="d8050-128">Adicione uma referência ao projeto `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="d8050-128">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="d8050-129">No Gerenciador de Soluções, defina o projeto `WpfUserControlHost` como o projeto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d8050-129">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="d8050-130">Hospedar o UserControl</span><span class="sxs-lookup"><span data-stu-id="d8050-130">Host the UserControl</span></span>

1. <span data-ttu-id="d8050-131">No Designer de Formulários do Windows, abra Form1.</span><span class="sxs-lookup"><span data-stu-id="d8050-131">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="d8050-132">No janela Propriedades, clique em **eventos**e clique duas vezes no evento <xref:System.Windows.Forms.Form.Load> para criar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="d8050-132">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="d8050-133">O Editor de Código abre o manipulador de eventos `Form1_Load` recém gerado.</span><span class="sxs-lookup"><span data-stu-id="d8050-133">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="d8050-134">Substitua o código em Form1.cs pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8050-134">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="d8050-135">O manipulador de eventos `Form1_Load` cria uma instância de `UserControl1` e adiciona com a coleção de controles filho do controle de <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="d8050-135">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="d8050-136">O controle <xref:System.Windows.Forms.Integration.ElementHost> é adicionado à coleção de controles filho do formulário.</span><span class="sxs-lookup"><span data-stu-id="d8050-136">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="d8050-137">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8050-137">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8050-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="d8050-138">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="d8050-139">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8050-139">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="d8050-140">Passo a passo: hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8050-140">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="d8050-141">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="d8050-141">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="d8050-142">Hospedando um controle composto do WPF nos exemplo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8050-142">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)
