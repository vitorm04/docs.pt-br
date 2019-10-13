---
title: 'Como: Criar um suplemento que retorne uma interface do usuário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: e32987355a6c7ad32b5e0e8522dc4daa63783fdd
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291251"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="7a064-102">Como: Criar um suplemento que retorne uma interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7a064-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="7a064-103">Este exemplo mostra como criar um suplemento que retorna um Windows Presentation Foundation (WPF) para um aplicativo host autônomo do WPF.</span><span class="sxs-lookup"><span data-stu-id="7a064-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="7a064-104">O suplemento retorna uma IU que é um controle de usuário do WPF.</span><span class="sxs-lookup"><span data-stu-id="7a064-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="7a064-105">O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7a064-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="7a064-106">O aplicativo autônomo do WPF hospeda o suplemento e exibe o controle de usuário (retornado pelo suplemento) como o conteúdo da janela principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a064-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="7a064-107">**Pré-requisitos**</span><span class="sxs-lookup"><span data-stu-id="7a064-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="7a064-108">Este exemplo realça as extensões do WPF para o modelo de suplemento .NET Framework que habilita esse cenário e pressupõe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7a064-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="7a064-109">Conhecimento do modelo de suplemento .NET Framework, incluindo pipeline, suplemento e desenvolvimento de host.</span><span class="sxs-lookup"><span data-stu-id="7a064-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="7a064-110">Se você não estiver familiarizado com esses conceitos, consulte [suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="7a064-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="7a064-111">Para obter um tutorial que demonstre a implementação de um pipeline, um suplemento e um aplicativo host, consulte [Walkthrough: Criando um aplicativo extensível @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="7a064-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
- <span data-ttu-id="7a064-112">Conhecimento das extensões do WPF para o modelo de suplemento .NET Framework, que pode ser encontrado aqui: [Visão geral dos suplementos do WPF](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7a064-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a064-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7a064-113">Example</span></span>  
 <span data-ttu-id="7a064-114">Para criar um suplemento que retorna uma interface do usuário do WPF, é necessário um código específico para cada segmento de pipeline, o suplemento e o aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="7a064-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="7a064-115">Implementando o segmento de pipeline de contrato</span><span class="sxs-lookup"><span data-stu-id="7a064-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="7a064-116">Um método deve ser definido pelo contrato para retornar uma interface do usuário, e seu valor de retorno deve ser do tipo <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="7a064-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="7a064-117">Isso é demonstrado pelo método `GetAddInUI` do contrato `IWPFAddInContract` no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a064-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="7a064-118">Implementando o segmento de pipeline de exibição de suplemento</span><span class="sxs-lookup"><span data-stu-id="7a064-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="7a064-119">Como o suplemento implementa as UIs que ele fornece como subclasses de <xref:System.Windows.FrameworkElement>, o método na exibição do suplemento que se correlaciona com `IWPFAddInView.GetAddInUI` deve retornar um valor do tipo <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="7a064-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="7a064-120">O código a seguir mostra a exibição de suplemento do contrato, implementada como uma interface.</span><span class="sxs-lookup"><span data-stu-id="7a064-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="7a064-121">Implementando o segmento de pipeline do adaptador no lado do suplemento</span><span class="sxs-lookup"><span data-stu-id="7a064-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="7a064-122">O método Contract retorna um <xref:System.AddIn.Contract.INativeHandleContract>, mas o suplemento retorna um <xref:System.Windows.FrameworkElement> (conforme especificado pela exibição do suplemento).</span><span class="sxs-lookup"><span data-stu-id="7a064-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="7a064-123">Consequentemente, o <xref:System.Windows.FrameworkElement> deve ser convertido em um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento.</span><span class="sxs-lookup"><span data-stu-id="7a064-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="7a064-124">Esse trabalho é executado pelo adaptador do lado do suplemento chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a064-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="7a064-125">Implementando o segmento de pipeline de exibição de host</span><span class="sxs-lookup"><span data-stu-id="7a064-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="7a064-126">Como o aplicativo host exibirá um <xref:System.Windows.FrameworkElement>, o método na exibição do host que se correlaciona com `IWPFAddInHostView.GetAddInUI` deve retornar um valor do tipo <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="7a064-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="7a064-127">O código a seguir mostra a exibição do host do contrato, implementada como uma interface.</span><span class="sxs-lookup"><span data-stu-id="7a064-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="7a064-128">Implementando o segmento de pipeline do adaptador no lado do host</span><span class="sxs-lookup"><span data-stu-id="7a064-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="7a064-129">O método Contract retorna um <xref:System.AddIn.Contract.INativeHandleContract>, mas o aplicativo host espera um <xref:System.Windows.FrameworkElement> (conforme especificado pela exibição do host).</span><span class="sxs-lookup"><span data-stu-id="7a064-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="7a064-130">Consequentemente, o <xref:System.AddIn.Contract.INativeHandleContract> deve ser convertido em um <xref:System.Windows.FrameworkElement> depois de cruzar o limite de isolamento.</span><span class="sxs-lookup"><span data-stu-id="7a064-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="7a064-131">Esse trabalho é executado pelo adaptador do lado do host chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a064-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="7a064-132">Implementando os suplementos</span><span class="sxs-lookup"><span data-stu-id="7a064-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="7a064-133">Com o adaptador do lado do suplemento e a exibição do suplemento criados, o suplemento (`WPFAddIn1.AddIn`) deve implementar o método `IWPFAddInView.GetAddInUI` para retornar um objeto <xref:System.Windows.FrameworkElement> (um <xref:System.Windows.Controls.UserControl> neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="7a064-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="7a064-134">A implementação do <xref:System.Windows.Controls.UserControl>, `AddInUI`, é mostrada pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a064-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="7a064-135">A implementação do `IWPFAddInView.GetAddInUI` pelo suplemento simplesmente precisa retornar uma nova instância de `AddInUI`, conforme mostrado pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a064-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="7a064-136">Implementando o aplicativo host</span><span class="sxs-lookup"><span data-stu-id="7a064-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="7a064-137">Com o adaptador do lado do host e o modo de exibição do host criados, o aplicativo host pode usar o modelo de suplemento .NET Framework para abrir o pipeline, adquirir uma exibição do host do suplemento e chamar o método `IWPFAddInHostView.GetAddInUI`.</span><span class="sxs-lookup"><span data-stu-id="7a064-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="7a064-138">Essas etapas são mostradas no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a064-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="7a064-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a064-139">See also</span></span>

- <span data-ttu-id="7a064-140">[Suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="7a064-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="7a064-141">Visão geral dos suplementos do WPF</span><span class="sxs-lookup"><span data-stu-id="7a064-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
