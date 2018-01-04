---
title: "Como habilitar estilos visuais em um aplicativo híbrido"
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
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73f611eab7f75d1578652a8a9f5bb05d9720e851
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="1f4dc-102">Como habilitar estilos visuais em um aplicativo híbrido</span><span class="sxs-lookup"><span data-stu-id="1f4dc-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="1f4dc-103">Este tópico mostra como habilitar [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] estilos visuais em um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle hospedado em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-aplicativo com base em.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-103">This topic shows how to enable [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="1f4dc-104">Se o aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método, a maioria das suas [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles usará automaticamente estilos visuais quando seu aplicativo é executado em [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f4dc-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles when your application is run on [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span> <span data-ttu-id="1f4dc-105">Para obter mais informações, consulte [renderização de controles com estilos visuais](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="1f4dc-105">For more information, see [Rendering Controls with Visual Styles](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="1f4dc-106">Para uma listagem de código completa das tarefas ilustradas neste tópico, consulte [habilitar estilos visuais em um exemplo de aplicativo híbrido](http://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="1f4dc-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](http://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="1f4dc-107">Habilitando estilos visuais no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f4dc-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="1f4dc-108">Para habilitar estilos visuais no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f4dc-108">To enable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="1f4dc-109">Criar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projeto de aplicativo chamado `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2.  <span data-ttu-id="1f4dc-110">No Gerenciador de Soluções, adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="1f4dc-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="1f4dc-111">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="1f4dc-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="1f4dc-112">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="1f4dc-113">Na caixa de ferramentas, clique duas vezes o <xref:System.Windows.Controls.Grid> ícone para colocar um <xref:System.Windows.Controls.Grid> elemento na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4.  <span data-ttu-id="1f4dc-114">Na janela Propriedades, defina os valores da <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> propriedades **automática**.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5.  <span data-ttu-id="1f4dc-115">No modo de Design ou modo de exibição XAML, selecione a <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6.  <span data-ttu-id="1f4dc-116">Na janela Propriedades, clique na guia **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-116">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="1f4dc-117">Clique duas vezes o <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8.  <span data-ttu-id="1f4dc-118">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, insira o seguinte código para manipular o <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="1f4dc-119">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="1f4dc-120">O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é pintado com estilos visuais.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="1f4dc-121">Desabilitando estilos visuais do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f4dc-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="1f4dc-122">Para desativar estilos visuais, simplesmente remova a chamada para o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="1f4dc-123">Para desabilitar estilos visuais do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f4dc-123">To disable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="1f4dc-124">Abra MainWindow.xaml.vb ou MainWindow.xaml.cs no editor de código.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="1f4dc-125">Comente a chamada para o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3.  <span data-ttu-id="1f4dc-126">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="1f4dc-127">O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é pintado com o estilo padrão do sistema.</span><span class="sxs-lookup"><span data-stu-id="1f4dc-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4dc-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f4dc-128">See Also</span></span>  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="1f4dc-129">Renderizando controles com estilos visuais</span><span class="sxs-lookup"><span data-stu-id="1f4dc-129">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [<span data-ttu-id="1f4dc-130">Passo a passo: hospedando um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="1f4dc-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
