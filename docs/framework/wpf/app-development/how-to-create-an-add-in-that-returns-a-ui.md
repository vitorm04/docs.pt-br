---
title: Como criar um suplemento que retorne uma interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174583"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="aaf7f-102">Como criar um suplemento que retorne uma interface do usuário</span><span class="sxs-lookup"><span data-stu-id="aaf7f-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="aaf7f-103">Este exemplo mostra como criar um complemento que retorna um WPF (Windows Presentation Foundation, fundação de apresentação do Windows) para um aplicativo autônomo wpf host.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="aaf7f-104">O complemento retorna uma UI que é um controle de usuário WPF.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="aaf7f-105">O conteúdo do controle de usuário é um único botão que, quando clicado, exibe uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="aaf7f-106">O aplicativo autônomo WPF hospeda o complemento e exibe o controle do usuário (retornado pelo complemento) como o conteúdo da janela principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="aaf7f-107">**Pré-requisitos**</span><span class="sxs-lookup"><span data-stu-id="aaf7f-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="aaf7f-108">Este exemplo destaca as extensões do WPF para o modelo de complemento .NET Framework que habilita esse cenário e assume o seguinte:</span><span class="sxs-lookup"><span data-stu-id="aaf7f-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="aaf7f-109">Conhecimento do modelo de complemento do .NET Framework, incluindo pipeline, complemento e desenvolvimento de host.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="aaf7f-110">Se você não está familiarizado com esses conceitos, consulte [Add-ins e Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="aaf7f-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="aaf7f-111">Para obter um tutorial que demonstre a implementação de um pipeline, um complemento e um aplicativo host, consulte [Passo a Passo: Criando um Aplicativo Extensível](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span><span class="sxs-lookup"><span data-stu-id="aaf7f-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="aaf7f-112">Conhecimento das extensões do WPF para o modelo de complemento do Framework .NET, que pode ser encontrado aqui: [Visão geral do WPF Add-Ins](wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="aaf7f-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf7f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aaf7f-113">Example</span></span>  
 <span data-ttu-id="aaf7f-114">Para criar um complemento que devolva uma UI WPF requer código específico para cada segmento de pipeline, o complemento e o aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="aaf7f-115">Implementando o segmento de pipeline de contrato</span><span class="sxs-lookup"><span data-stu-id="aaf7f-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="aaf7f-116">Um método deve ser definido pelo contrato de devolução de uma <xref:System.AddIn.Contract.INativeHandleContract>UI, e seu valor de retorno deve ser do tipo .</span><span class="sxs-lookup"><span data-stu-id="aaf7f-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="aaf7f-117">Isso é demonstrado `GetAddInUI` pelo `IWPFAddInContract` método do contrato no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="aaf7f-118">Implementando o segmento de pipeline de exibição de suplemento</span><span class="sxs-lookup"><span data-stu-id="aaf7f-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="aaf7f-119">Como o complemento implementa as UIs que <xref:System.Windows.FrameworkElement>fornece como subclasses de , o `IWPFAddInView.GetAddInUI` método na exibição <xref:System.Windows.FrameworkElement>de complemento que se correlaciona deve retornar um valor do tipo .</span><span class="sxs-lookup"><span data-stu-id="aaf7f-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="aaf7f-120">O código a seguir mostra a exibição de suplemento do contrato, implementada como uma interface.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="aaf7f-121">Implementando o segmento de pipeline do adaptador no lado do suplemento</span><span class="sxs-lookup"><span data-stu-id="aaf7f-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="aaf7f-122">O método de <xref:System.AddIn.Contract.INativeHandleContract>contrato retorna um , <xref:System.Windows.FrameworkElement> mas o complemento retorna a (conforme especificado pela exibição de complemento).</span><span class="sxs-lookup"><span data-stu-id="aaf7f-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="aaf7f-123">Consequentemente, <xref:System.Windows.FrameworkElement> o deve ser <xref:System.AddIn.Contract.INativeHandleContract> convertido em um antes de cruzar o limite de isolamento.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="aaf7f-124">Este trabalho é realizado pelo adaptador add-in-side, chamando, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="aaf7f-125">Implementando o segmento de pipeline de exibição de host</span><span class="sxs-lookup"><span data-stu-id="aaf7f-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="aaf7f-126">Como o aplicativo host <xref:System.Windows.FrameworkElement>exibirá um , o método `IWPFAddInHostView.GetAddInUI` na exibição host <xref:System.Windows.FrameworkElement>que se correlaciona deve retornar um valor do tipo .</span><span class="sxs-lookup"><span data-stu-id="aaf7f-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="aaf7f-127">O código a seguir mostra a exibição do host do contrato, implementada como uma interface.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="aaf7f-128">Implementando o segmento de pipeline do adaptador no lado do host</span><span class="sxs-lookup"><span data-stu-id="aaf7f-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="aaf7f-129">O método de <xref:System.AddIn.Contract.INativeHandleContract>contrato retorna um <xref:System.Windows.FrameworkElement> , mas o aplicativo host espera um (conforme especificado pela exibição host).</span><span class="sxs-lookup"><span data-stu-id="aaf7f-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="aaf7f-130">Consequentemente, <xref:System.AddIn.Contract.INativeHandleContract> o deve ser <xref:System.Windows.FrameworkElement> convertido para um após cruzar o limite de isolamento.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="aaf7f-131">Este trabalho é realizado pelo adaptador <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>do lado do host, chamando, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a><span data-ttu-id="aaf7f-132">Implementando os suplementos</span><span class="sxs-lookup"><span data-stu-id="aaf7f-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="aaf7f-133">Com o adaptador add-in e a exibição de complemento`WPFAddIn1.AddIn`criada, `IWPFAddInView.GetAddInUI` o complemento <xref:System.Windows.FrameworkElement> ( <xref:System.Windows.Controls.UserControl> ) deve implementar o método para retornar um objeto (a neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="aaf7f-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="aaf7f-134">A implementação <xref:System.Windows.Controls.UserControl> `AddInUI`do , , é mostrado pelo seguinte código.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="aaf7f-135">A implementação `IWPFAddInView.GetAddInUI` do complemento simplesmente precisa retornar uma `AddInUI`nova instância de , como mostrado pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a><span data-ttu-id="aaf7f-136">Implementando o aplicativo host</span><span class="sxs-lookup"><span data-stu-id="aaf7f-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="aaf7f-137">Com o adaptador do lado do host e a exibição do host criadas, o aplicativo host pode usar o modelo `IWPFAddInHostView.GetAddInUI` de complemento .NET Framework para abrir o pipeline, adquirir uma visão host do complemento e chamar o método.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="aaf7f-138">Essas etapas são mostradas no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="aaf7f-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf7f-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="aaf7f-139">See also</span></span>

- <span data-ttu-id="aaf7f-140">[Suplementos e extensibilidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="aaf7f-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="aaf7f-141">Visão geral dos suplementos do WPF</span><span class="sxs-lookup"><span data-stu-id="aaf7f-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
