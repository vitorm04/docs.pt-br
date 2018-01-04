---
title: "Instruções passo a passo: hospedando um controle dos Windows Forms no WPF usando XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f99dc055c5b5dc2f71008dce4e489025304bfceb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="dda62-102">Instruções passo a passo: hospedando um controle dos Windows Forms no WPF usando XAML</span><span class="sxs-lookup"><span data-stu-id="dda62-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
<span data-ttu-id="dda62-103">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="dda62-103">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides many controls with a rich feature set.</span></span> <span data-ttu-id="dda62-104">No entanto, às vezes, convém usar controles do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em suas páginas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dda62-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="dda62-105">Por exemplo, você pode ter um investimento substancial em controles existentes do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou pode ter um controle do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que fornece funcionalidade exclusiva.</span><span class="sxs-lookup"><span data-stu-id="dda62-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="dda62-106">Este passo a passo mostra como hospedar um Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dda62-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="dda62-107">Para uma listagem de código completa de todas as tarefas mostradas neste passo a passo, veja [Hospedando um controle dos Windows Forms no WPF usando exemplo XAML](http://go.microsoft.com/fwlink/?LinkID=160000).</span><span class="sxs-lookup"><span data-stu-id="dda62-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](http://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dda62-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dda62-108">Prerequisites</span></span>  
 <span data-ttu-id="dda62-109">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="dda62-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="dda62-110">.</span><span class="sxs-lookup"><span data-stu-id="dda62-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="dda62-111">Hospedando o controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dda62-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="dda62-112">Para hospedar o controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="dda62-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="dda62-113">Crie um projeto de aplicativo WPF chamado `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="dda62-113">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="dda62-114">Adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="dda62-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="dda62-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="dda62-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="dda62-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="dda62-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="dda62-117">Abra MainWindow.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dda62-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="dda62-118">No <xref:System.Windows.Window> elemento, adicione o seguinte mapeamento de namespace.</span><span class="sxs-lookup"><span data-stu-id="dda62-118">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="dda62-119">O mapeamento de namespace `wf` estabelece uma referência ao assembly que contém o controle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dda62-119">The `wf` namespace mapping establishes a reference to the assembly that contains the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="dda62-120">No <xref:System.Windows.Controls.Grid> elemento adicionar o XAML a seguir.</span><span class="sxs-lookup"><span data-stu-id="dda62-120">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="dda62-121">O <xref:System.Windows.Forms.MaskedTextBox> controle é criado como um filho de <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle.</span><span class="sxs-lookup"><span data-stu-id="dda62-121">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="dda62-122">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dda62-122">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda62-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dda62-123">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="dda62-124">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="dda62-124">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="dda62-125">Passo a passo: hospedando um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="dda62-125">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="dda62-126">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="dda62-126">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="dda62-127">Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dda62-127">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="dda62-128">Controles dos Windows Forms e controles WPF equivalentes</span><span class="sxs-lookup"><span data-stu-id="dda62-128">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="dda62-129">Hospedando um controle dos Windows Forms no WPF usando um exemplo XAML</span><span class="sxs-lookup"><span data-stu-id="dda62-129">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160000)
