---
title: Hospedar um controle de Windows Forms no WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 2ed4e153a2513dc99d22a1538399156c138eb9e5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123825"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="8b273-102">Instruções passo a passo: hospedando um controle dos Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="8b273-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

<span data-ttu-id="8b273-103">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="8b273-103">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides many controls with a rich feature set.</span></span> <span data-ttu-id="8b273-104">No entanto, às vezes você pode querer usar controles de Windows Forms em suas páginas de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b273-104">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="8b273-105">Por exemplo, você pode ter um investimento substancial em controles de Windows Forms existentes ou pode ter um controle de Windows Forms que fornece funcionalidade exclusiva.</span><span class="sxs-lookup"><span data-stu-id="8b273-105">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="8b273-106">Este tutorial mostra como hospedar um Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> controle em uma página [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando código.</span><span class="sxs-lookup"><span data-stu-id="8b273-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="8b273-107">Para obter uma listagem de código completa das tarefas mostradas neste passo a passos, consulte [hospedando um controle de Windows Forms no exemplo do WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span><span class="sxs-lookup"><span data-stu-id="8b273-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8b273-108">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8b273-108">Prerequisites</span></span>

<span data-ttu-id="8b273-109">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="8b273-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="8b273-110">Hospedando o controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b273-110">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="8b273-111">Para hospedar o controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="8b273-111">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="8b273-112">Crie um projeto de aplicativo WPF chamado `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="8b273-112">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="8b273-113">Adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b273-113">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="8b273-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="8b273-114">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="8b273-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="8b273-115">System.Windows.Forms</span></span>

3. <span data-ttu-id="8b273-116">Abra o MainWindow.xaml no WPF Designer.</span><span class="sxs-lookup"><span data-stu-id="8b273-116">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="8b273-117">Nomeie o elemento de <xref:System.Windows.Controls.Grid> `grid1`.</span><span class="sxs-lookup"><span data-stu-id="8b273-117">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="8b273-118">No modo de exibição modo de exibição de Design ou XAML, selecione o elemento <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="8b273-118">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="8b273-119">Na janela Propriedades, clique na guia **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="8b273-119">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="8b273-120">Clique duas vezes no evento <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="8b273-120">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="8b273-121">Insira o código a seguir para manipular o evento <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="8b273-121">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="8b273-122">Na parte superior do arquivo, adicione o seguinte `Imports` ou `using` instrução.</span><span class="sxs-lookup"><span data-stu-id="8b273-122">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="8b273-123">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b273-123">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b273-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b273-124">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="8b273-125">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b273-125">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="8b273-126">Passo a passo: hospedando um controle do Windows Forms no WPF usando XAML</span><span class="sxs-lookup"><span data-stu-id="8b273-126">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="8b273-127">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="8b273-127">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="8b273-128">Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b273-128">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="8b273-129">Controles dos Windows Forms e controles WPF equivalentes</span><span class="sxs-lookup"><span data-stu-id="8b273-129">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="8b273-130">Hospedando um controle de Windows Forms no exemplo do WPF</span><span class="sxs-lookup"><span data-stu-id="8b273-130">Hosting a Windows Forms Control in WPF Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
