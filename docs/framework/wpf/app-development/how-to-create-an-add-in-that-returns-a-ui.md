---
title: "Como criar um suplemento que retorne uma interface do usuário"
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
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd6956f1934f8594a941b57066cc2d4d6214a9a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="1596c-102">Como criar um suplemento que retorne uma interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1596c-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="1596c-103">Este exemplo mostra como criar um suplemento que retorna um [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para um host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo autônomo.</span><span class="sxs-lookup"><span data-stu-id="1596c-103">This example shows how to create an add-in that returns a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)][!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to a host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application.</span></span>  
  
 <span data-ttu-id="1596c-104">O suplemento retorna um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que é um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="1596c-104">The add-in returns a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that is a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] user control.</span></span> <span data-ttu-id="1596c-105">O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1596c-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="1596c-106">O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo autônomo hospeda o suplemento e exibe o controle de usuário (retornado pelo suplemento) como o conteúdo da janela principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1596c-106">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="1596c-107">**Pré-requisitos**</span><span class="sxs-lookup"><span data-stu-id="1596c-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="1596c-108">Este exemplo realça o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensões para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adicionar no modelo de habilitar esse cenário e assume o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1596c-108">This example highlights the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="1596c-109">Conhecimento sobre o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adicionar no modelo, incluindo o pipeline de suplemento e desenvolvimento de host.</span><span class="sxs-lookup"><span data-stu-id="1596c-109">Knowledge of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="1596c-110">Se você estiver familiarizado com esses conceitos, consulte [suplementos e extensibilidade](../../../../docs/framework/add-ins/index.md).</span><span class="sxs-lookup"><span data-stu-id="1596c-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](../../../../docs/framework/add-ins/index.md).</span></span> <span data-ttu-id="1596c-111">Para obter um tutorial que demonstra a implementação de um pipeline, um suplemento e um aplicativo host, consulte [passo a passo: Criando um aplicativo extensível](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="1596c-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="1596c-112">Conhecimento do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensões para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adicionar no modelo, que pode ser encontrado aqui: [visão geral de suplementos WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1596c-112">Knowledge of the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1596c-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1596c-113">Example</span></span>  
 <span data-ttu-id="1596c-114">Para criar um suplemento que retorna um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requer código específico para cada segmento de pipeline, o suplemento e o aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="1596c-114">To create an add-in that returns a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="1596c-115">Implementando o segmento de pipeline de contrato</span><span class="sxs-lookup"><span data-stu-id="1596c-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="1596c-116">Um método deve ser definido pelo contrato para retornar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], e seu valor de retorno deve ser do tipo <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="1596c-116">A method must be defined by the contract for returning a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="1596c-117">Isso é demonstrado pelo `GetAddInUI` método o `IWPFAddInContract` de contrato no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1596c-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="1596c-118">Implementando o segmento de pipeline de exibição de suplemento</span><span class="sxs-lookup"><span data-stu-id="1596c-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="1596c-119">Como o suplemento implementa o [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fornece como subclasses de <xref:System.Windows.FrameworkElement>, o método da exibição do suplemento que se correlaciona com `IWPFAddInView.GetAddInUI` deve retornar um valor do tipo <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="1596c-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="1596c-120">O código a seguir mostra a exibição de suplemento do contrato, implementada como uma interface.</span><span class="sxs-lookup"><span data-stu-id="1596c-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="1596c-121">Implementando o segmento de pipeline do adaptador no lado do suplemento</span><span class="sxs-lookup"><span data-stu-id="1596c-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="1596c-122">O método do contrato retorna um <xref:System.AddIn.Contract.INativeHandleContract>, mas o suplemento retorna um <xref:System.Windows.FrameworkElement> (especificado como o modo de exibição).</span><span class="sxs-lookup"><span data-stu-id="1596c-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="1596c-123">Consequentemente, o <xref:System.Windows.FrameworkElement> devem ser convertidos para um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento.</span><span class="sxs-lookup"><span data-stu-id="1596c-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="1596c-124">O trabalho é executado pelo adaptador do lado do suplemento chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1596c-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="1596c-125">Implementando o segmento de pipeline de exibição de host</span><span class="sxs-lookup"><span data-stu-id="1596c-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="1596c-126">Como o aplicativo de host irá exibir um <xref:System.Windows.FrameworkElement>, o método no modo de host que se correlaciona com `IWPFAddInHostView.GetAddInUI` deve retornar um valor do tipo <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="1596c-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="1596c-127">O código a seguir mostra a exibição do host do contrato, implementada como uma interface.</span><span class="sxs-lookup"><span data-stu-id="1596c-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="1596c-128">Implementando o segmento de pipeline do adaptador no lado do host</span><span class="sxs-lookup"><span data-stu-id="1596c-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="1596c-129">O método do contrato retorna um <xref:System.AddIn.Contract.INativeHandleContract>, mas o aplicativo de host espera um <xref:System.Windows.FrameworkElement> (como especificado pelo modo de host).</span><span class="sxs-lookup"><span data-stu-id="1596c-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="1596c-130">Consequentemente, o <xref:System.AddIn.Contract.INativeHandleContract> devem ser convertidos para um <xref:System.Windows.FrameworkElement> após cruzar o limite de isolamento.</span><span class="sxs-lookup"><span data-stu-id="1596c-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="1596c-131">O trabalho é executado pelo adaptador do lado do host chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1596c-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="1596c-132">Implementando os suplementos</span><span class="sxs-lookup"><span data-stu-id="1596c-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="1596c-133">Com o adaptador do lado do suplemento e o suplemento exibição criada, o suplemento (`WPFAddIn1.AddIn`) deve implementar o `IWPFAddInView.GetAddInUI` método para retornar um <xref:System.Windows.FrameworkElement> objeto (um <xref:System.Windows.Controls.UserControl> neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="1596c-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="1596c-134">A implementação de <xref:System.Windows.Controls.UserControl>, `AddInUI`, é mostrado pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1596c-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="1596c-135">A implementação de `IWPFAddInView.GetAddInUI` pelo suplemento simplesmente precisa retornar uma nova instância da `AddInUI`, conforme mostrado pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1596c-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="1596c-136">Implementando o aplicativo host</span><span class="sxs-lookup"><span data-stu-id="1596c-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="1596c-137">Com o adaptador do lado do host e o modo de host criados, o aplicativo de host pode usar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelo de suplemento para abrir a pipeline, adquirir um modo de host do suplemento e chamada de `IWPFAddInHostView.GetAddInUI` método.</span><span class="sxs-lookup"><span data-stu-id="1596c-137">With the host-side adapter and host view created, the host application can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="1596c-138">Essas etapas são mostradas no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1596c-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="1596c-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1596c-139">See Also</span></span>  
 [<span data-ttu-id="1596c-140">Suplementos e extensibilidade</span><span class="sxs-lookup"><span data-stu-id="1596c-140">Add-ins and Extensibility</span></span>](../../../../docs/framework/add-ins/index.md)  
 [<span data-ttu-id="1596c-141">Visão geral dos suplementos do WPF</span><span class="sxs-lookup"><span data-stu-id="1596c-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
