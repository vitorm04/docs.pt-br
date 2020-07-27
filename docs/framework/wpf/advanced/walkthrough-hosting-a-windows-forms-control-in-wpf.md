---
title: Hospedar um controle de Windows Forms no WPF
description: Saiba como hospedar controles de Windows Forms no Windows Presentation Foundation, que já fornece muitos controles com um rico conjunto de recursos.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164978"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="6b682-103">Passo a passo: hospedar um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="6b682-103">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

<span data-ttu-id="6b682-104">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="6b682-104">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides many controls with a rich feature set.</span></span> <span data-ttu-id="6b682-105">No entanto, às vezes você pode querer usar controles de Windows Forms em suas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] páginas.</span><span class="sxs-lookup"><span data-stu-id="6b682-105">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="6b682-106">Por exemplo, você pode ter um investimento substancial em controles de Windows Forms existentes ou pode ter um controle de Windows Forms que fornece funcionalidade exclusiva.</span><span class="sxs-lookup"><span data-stu-id="6b682-106">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="6b682-107">Este tutorial mostra como hospedar um Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> controle em uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] página usando código.</span><span class="sxs-lookup"><span data-stu-id="6b682-107">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="6b682-108">Para obter uma listagem de código completa das tarefas mostradas neste passo a passos, consulte [hospedando um controle de Windows Forms no exemplo do WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span><span class="sxs-lookup"><span data-stu-id="6b682-108">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b682-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6b682-109">Prerequisites</span></span>

<span data-ttu-id="6b682-110">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="6b682-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="6b682-111">Hospedando o controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b682-111">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="6b682-112">Para hospedar o controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="6b682-112">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="6b682-113">Crie um projeto de aplicativo WPF chamado `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="6b682-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="6b682-114">Adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="6b682-114">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="6b682-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="6b682-115">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="6b682-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="6b682-116">System.Windows.Forms</span></span>

3. <span data-ttu-id="6b682-117">Abra o MainWindow.xaml no WPF Designer.</span><span class="sxs-lookup"><span data-stu-id="6b682-117">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="6b682-118">Nomeie o <xref:System.Windows.Controls.Grid> elemento `grid1` .</span><span class="sxs-lookup"><span data-stu-id="6b682-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="6b682-119">No modo de exibição modo de exibição de Design ou XAML, selecione o <xref:System.Windows.Window> elemento.</span><span class="sxs-lookup"><span data-stu-id="6b682-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="6b682-120">Na janela Propriedades, clique na guia **eventos** .</span><span class="sxs-lookup"><span data-stu-id="6b682-120">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="6b682-121">Clique duas vezes no <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="6b682-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="6b682-122">Insira o código a seguir para manipular o <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="6b682-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="6b682-123">Na parte superior do arquivo, adicione a seguinte `Imports` instrução ou `using` .</span><span class="sxs-lookup"><span data-stu-id="6b682-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="6b682-124">Selecione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6b682-124">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b682-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b682-125">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6b682-126">Criar XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6b682-126">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="6b682-127">Passo a passo: hospedar um controle do Windows Forms no WPF usando XAML</span><span class="sxs-lookup"><span data-stu-id="6b682-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="6b682-128">Passo a passo: hospedar um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="6b682-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="6b682-129">Passo a passo: hospedar um controle composto do WPF nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b682-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="6b682-130">Controles dos Windows Forms e controles WPF equivalentes</span><span class="sxs-lookup"><span data-stu-id="6b682-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="6b682-131">Hospedando um controle de Windows Forms no exemplo do WPF</span><span class="sxs-lookup"><span data-stu-id="6b682-131">Hosting a Windows Forms Control in WPF Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
