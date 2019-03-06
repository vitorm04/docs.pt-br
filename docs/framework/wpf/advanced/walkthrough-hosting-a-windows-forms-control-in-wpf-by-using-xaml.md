---
title: 'Passo a passo: Hospedando um controle de formulários do Windows no WPF usando XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 1566f27703e2603a5d70cf8cfc7a01a08c407f6a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379530"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="9df60-102">Passo a passo: Hospedando um controle de formulários do Windows no WPF usando XAML</span><span class="sxs-lookup"><span data-stu-id="9df60-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
<span data-ttu-id="9df60-103">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="9df60-103">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides many controls with a rich feature set.</span></span> <span data-ttu-id="9df60-104">No entanto, às vezes, convém usar controles do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em suas páginas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9df60-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="9df60-105">Por exemplo, você pode ter um investimento substancial em controles existentes do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou pode ter um controle do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que fornece funcionalidade exclusiva.</span><span class="sxs-lookup"><span data-stu-id="9df60-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="9df60-106">Este passo a passo mostra como hospedar um Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9df60-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="9df60-107">Para uma listagem de código completa de todas as tarefas mostradas neste passo a passo, veja [Hospedando um controle dos Windows Forms no WPF usando exemplo XAML](https://go.microsoft.com/fwlink/?LinkID=160000).</span><span class="sxs-lookup"><span data-stu-id="9df60-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9df60-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9df60-108">Prerequisites</span></span>  

<span data-ttu-id="9df60-109">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="9df60-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="9df60-110">Hospedando o controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9df60-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="9df60-111">Para hospedar o controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="9df60-111">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="9df60-112">Crie um projeto de aplicativo WPF chamado `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="9df60-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="9df60-113">Adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="9df60-113">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="9df60-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="9df60-114">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="9df60-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="9df60-115">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="9df60-116">Abra MainWindow.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9df60-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="9df60-117">No <xref:System.Windows.Window> elemento, adicione o seguinte mapeamento de namespace.</span><span class="sxs-lookup"><span data-stu-id="9df60-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="9df60-118">O `wf` mapeamento de namespace estabelece uma referência ao assembly que contém o controle de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="9df60-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="9df60-119">No <xref:System.Windows.Controls.Grid> elemento adicionar o XAML a seguir.</span><span class="sxs-lookup"><span data-stu-id="9df60-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="9df60-120">O <xref:System.Windows.Forms.MaskedTextBox> controle é criado como um filho de <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle.</span><span class="sxs-lookup"><span data-stu-id="9df60-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="9df60-121">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9df60-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df60-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9df60-122">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="9df60-123">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9df60-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="9df60-124">Passo a passo: Hospedando um controle de formulários do Windows no WPF</span><span class="sxs-lookup"><span data-stu-id="9df60-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="9df60-125">Passo a passo: Hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="9df60-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="9df60-126">Passo a passo: Hospedando um controle composto do WPF nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9df60-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="9df60-127">Controles dos Windows Forms e controles WPF equivalentes</span><span class="sxs-lookup"><span data-stu-id="9df60-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="9df60-128">Hospedando um controle dos Windows Forms no WPF usando um exemplo XAML</span><span class="sxs-lookup"><span data-stu-id="9df60-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
