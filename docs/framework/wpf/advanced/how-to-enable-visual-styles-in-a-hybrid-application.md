---
title: Como habilitar estilos visuais em um aplicativo híbrido
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 251c53a8665d2eae7c3b5bb23b0a388009362dcc
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960120"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="a2ca7-102">Como habilitar estilos visuais em um aplicativo híbrido</span><span class="sxs-lookup"><span data-stu-id="a2ca7-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="a2ca7-103">Este tópico mostra como habilitar estilos visuais em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado em um aplicativo baseado em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2ca7-103">This topic shows how to enable visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="a2ca7-104">Se seu aplicativo chamar o método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, a maioria dos seus controles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] usará automaticamente estilos visuais.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles.</span></span> <span data-ttu-id="a2ca7-105">Saiba mais em [Renderizar controles com estilos visuais](../../winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="a2ca7-105">For more information, see [Rendering Controls with Visual Styles](../../winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="a2ca7-106">Para obter uma listagem de código completa das tarefas ilustradas neste tópico, consulte [habilitando estilos visuais em um exemplo de aplicativo híbrido](https://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="a2ca7-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="a2ca7-107">Habilitando estilos visuais no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a2ca7-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="a2ca7-108">Para habilitar estilos visuais no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a2ca7-108">To enable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="a2ca7-109">Crie um projeto de aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamado `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2. <span data-ttu-id="a2ca7-110">No Gerenciador de Soluções, adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="a2ca7-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="a2ca7-111">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="a2ca7-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="a2ca7-112">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="a2ca7-113">Na caixa de ferramentas, clique duas vezes no ícone de <xref:System.Windows.Controls.Grid> para posicionar um elemento de <xref:System.Windows.Controls.Grid> na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4. <span data-ttu-id="a2ca7-114">Na janela Propriedades, defina os valores das propriedades <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> como **automático**.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5. <span data-ttu-id="a2ca7-115">Na exibição modo de exibição de Design ou XAML, selecione o <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6. <span data-ttu-id="a2ca7-116">Na janela Propriedades, clique na guia **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-116">In the Properties window, click the **Events** tab.</span></span>  
  
7. <span data-ttu-id="a2ca7-117">Clique duas vezes no evento <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8. <span data-ttu-id="a2ca7-118">Em MainWindow. XAML. vb ou MainWindow.xaml.cs, insira o código a seguir para manipular o evento de <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="a2ca7-119">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="a2ca7-120">O controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é pintado com estilos visuais.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="a2ca7-121">Desabilitando estilos visuais do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a2ca7-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="a2ca7-122">Para desabilitar os estilos visuais, basta remover a chamada para o método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="a2ca7-123">Para desabilitar estilos visuais do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a2ca7-123">To disable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="a2ca7-124">Abra MainWindow.xaml.vb ou MainWindow.xaml.cs no editor de código.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2. <span data-ttu-id="a2ca7-125">Comente a chamada para o método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3. <span data-ttu-id="a2ca7-126">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="a2ca7-127">O controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é pintado com o estilo de sistema padrão.</span><span class="sxs-lookup"><span data-stu-id="a2ca7-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ca7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2ca7-128">See also</span></span>

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a2ca7-129">Renderizando controles com estilos visuais</span><span class="sxs-lookup"><span data-stu-id="a2ca7-129">Rendering Controls with Visual Styles</span></span>](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [<span data-ttu-id="a2ca7-130">Passo a passo: hospedando um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="a2ca7-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
