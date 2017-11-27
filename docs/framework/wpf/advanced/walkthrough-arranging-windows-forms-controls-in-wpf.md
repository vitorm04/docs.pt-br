---
title: "Instruções passo a passo: organizando controles dos Windows Forms no WPF"
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
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f78da83657c4c1bd913f67c9e612264cc5dbdf99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="ea78a-102">Instruções passo a passo: organizando controles dos Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="ea78a-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="ea78a-103">Este passo a passo mostra como usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] recursos de layout para organizar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles em um aplicativo híbrido.</span><span class="sxs-lookup"><span data-stu-id="ea78a-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="ea78a-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="ea78a-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="ea78a-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="ea78a-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="ea78a-106">Usando as configurações padrão de layout.</span><span class="sxs-lookup"><span data-stu-id="ea78a-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="ea78a-107">Dimensionando o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="ea78a-108">Usando o posicionamento absoluto.</span><span class="sxs-lookup"><span data-stu-id="ea78a-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="ea78a-109">Especificando o tamanho explicitamente.</span><span class="sxs-lookup"><span data-stu-id="ea78a-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="ea78a-110">Definindo propriedades de layout.</span><span class="sxs-lookup"><span data-stu-id="ea78a-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="ea78a-111">Noções básicas sobre limitações da ordem z.</span><span class="sxs-lookup"><span data-stu-id="ea78a-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="ea78a-112">Encaixe.</span><span class="sxs-lookup"><span data-stu-id="ea78a-112">Docking.</span></span>  
  
-   <span data-ttu-id="ea78a-113">Definindo a visibilidade.</span><span class="sxs-lookup"><span data-stu-id="ea78a-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="ea78a-114">Hospedando um controle que não se alonga.</span><span class="sxs-lookup"><span data-stu-id="ea78a-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="ea78a-115">Dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-115">Scaling.</span></span>  
  
-   <span data-ttu-id="ea78a-116">Girando.</span><span class="sxs-lookup"><span data-stu-id="ea78a-116">Rotating.</span></span>  
  
-   <span data-ttu-id="ea78a-117">Margens e preenchimento de configuração.</span><span class="sxs-lookup"><span data-stu-id="ea78a-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="ea78a-118">Usando contêineres de layout dinâmico.</span><span class="sxs-lookup"><span data-stu-id="ea78a-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="ea78a-119">Para uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [Organizando controles dos Windows Forms no WPF exemplo](http://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="ea78a-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="ea78a-120">Quando tiver terminado, você terá uma compreensão de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] recursos de layout no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-com base em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ea78a-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea78a-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ea78a-121">Prerequisites</span></span>  
 <span data-ttu-id="ea78a-122">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="ea78a-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="ea78a-123">.</span><span class="sxs-lookup"><span data-stu-id="ea78a-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="ea78a-124">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="ea78a-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="ea78a-125">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="ea78a-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="ea78a-126">Crie um projeto de aplicativo WPF chamado `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="ea78a-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="ea78a-127">No Gerenciador de Soluções, adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea78a-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="ea78a-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="ea78a-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="ea78a-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="ea78a-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="ea78a-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="ea78a-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="ea78a-131">Clique duas vezes em MainWindow.xaml para abri-lo no modo de exibição XAML.</span><span class="sxs-lookup"><span data-stu-id="ea78a-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="ea78a-132">No <xref:System.Windows.Window> elemento, adicione o seguinte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapeamento de namespace.</span><span class="sxs-lookup"><span data-stu-id="ea78a-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="ea78a-133">No <xref:System.Windows.Controls.Grid> conjunto de elementos de <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriedade `true` e definir cinco linhas e três colunas.</span><span class="sxs-lookup"><span data-stu-id="ea78a-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="ea78a-134">Usando as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="ea78a-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="ea78a-135">Por padrão, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento manipula o layout para hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="ea78a-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="ea78a-136">Para usar as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="ea78a-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="ea78a-137">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="ea78a-138">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-139">O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> controle aparece no <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="ea78a-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="ea78a-140">O controle hospedado é dimensionado com base em seu conteúdo e o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é dimensionado para acomodar o controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="ea78a-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="ea78a-141">Dimensionando para o conteúdo</span><span class="sxs-lookup"><span data-stu-id="ea78a-141">Sizing to Content</span></span>  
 <span data-ttu-id="ea78a-142">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento garante que o controle hospedado é dimensionado para exibir seu conteúdo corretamente.</span><span class="sxs-lookup"><span data-stu-id="ea78a-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="ea78a-143">Para dimensionar para o Conteúdo</span><span class="sxs-lookup"><span data-stu-id="ea78a-143">To size to content</span></span>  
  
1.  <span data-ttu-id="ea78a-144">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="ea78a-145">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-146">Os dois novos controles de botão são dimensionados para exibir a cadeia de caracteres de texto mais longa e maior tamanho da fonte corretamente e o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos são redimensionados para acomodar os controles hospedados.</span><span class="sxs-lookup"><span data-stu-id="ea78a-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="ea78a-147">Usando o posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="ea78a-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="ea78a-148">Você pode usar o posicionamento absoluto para colocar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento em qualquer lugar na interface do usuário (IU).</span><span class="sxs-lookup"><span data-stu-id="ea78a-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="ea78a-149">Para usar posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="ea78a-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="ea78a-150">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="ea78a-151">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-152">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é colocado 20 pixels, do lado superior da célula da grade e a 20 pixels da esquerda.</span><span class="sxs-lookup"><span data-stu-id="ea78a-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="ea78a-153">Especificando o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="ea78a-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="ea78a-154">Você pode especificar o tamanho do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento usando o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="ea78a-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="ea78a-155">Para especificar o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="ea78a-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="ea78a-156">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="ea78a-157">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-158">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> é definido como um tamanho de 50 pixels de largura por 70 pixels de altura, que é menor do que as configurações de layout padrão.</span><span class="sxs-lookup"><span data-stu-id="ea78a-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="ea78a-159">O conteúdo a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é reorganizado adequadamente.</span><span class="sxs-lookup"><span data-stu-id="ea78a-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="ea78a-160">Definindo propriedades de layout</span><span class="sxs-lookup"><span data-stu-id="ea78a-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="ea78a-161">Sempre defina propriedades relacionadas ao layout no controle hospedado usando as propriedades do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="ea78a-162">Definindo propriedades de layout diretamente no controle hospedado produzirá resultados indesejados.</span><span class="sxs-lookup"><span data-stu-id="ea78a-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="ea78a-163">A definição de propriedades relacionadas ao layout no controle hospedado em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="ea78a-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="ea78a-164">Para ver os efeitos da definição das propriedades no controle hospedado</span><span class="sxs-lookup"><span data-stu-id="ea78a-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="ea78a-165">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="ea78a-166">No Gerenciador de Soluções, clique duas vezes em MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ea78a-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="ea78a-167">Abrir vb ou MainWindow.xaml.cs no Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ea78a-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="ea78a-168">Copie o seguinte código para o `MainWindow` definição da classe.</span><span class="sxs-lookup"><span data-stu-id="ea78a-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="ea78a-169">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="ea78a-170">Clique o **clique me** botão.</span><span class="sxs-lookup"><span data-stu-id="ea78a-170">Click the **Click me** button.</span></span> <span data-ttu-id="ea78a-171">O `button1_Click` conjuntos de manipulador de eventos de <xref:System.Windows.Forms.Control.Top%2A> e <xref:System.Windows.Forms.Control.Left%2A> propriedades no controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="ea78a-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="ea78a-172">Isso faz com que o controle hospedado seja reposicionado dentro de <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="ea78a-173">O host mantém a mesma área da tela, mas o controle hospedado é cortado.</span><span class="sxs-lookup"><span data-stu-id="ea78a-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="ea78a-174">Em vez disso, o controle hospedado sempre deve preencher o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="ea78a-175">Noções básicas sobre limitações da ordem z</span><span class="sxs-lookup"><span data-stu-id="ea78a-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="ea78a-176">Por padrão, visível <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos sempre são desenhados sobre outros [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos e eles não são afetados pela ordem z.</span><span class="sxs-lookup"><span data-stu-id="ea78a-176">By default, visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="ea78a-177">Para habilitar a ordem z, defina o <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> propriedade do <xref:System.Windows.Forms.Integration.WindowsFormsHost> como true e o <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> propriedade <xref:System.Windows.Interop.CompositionMode.Full> ou <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="ea78a-177">To enable z-ordering, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-default-z-order-behavior"></a><span data-ttu-id="ea78a-178">Para ver o comportamento da ordem z padrão</span><span class="sxs-lookup"><span data-stu-id="ea78a-178">To see the default z-order behavior</span></span>  
  
1.  <span data-ttu-id="ea78a-179">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-179">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  <span data-ttu-id="ea78a-180">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-180">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-181">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é pintado sobre o elemento de rótulo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-181">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a><span data-ttu-id="ea78a-182">Para ver o comportamento da ordem z quando IsRedirected é verdadeiro</span><span class="sxs-lookup"><span data-stu-id="ea78a-182">To see the z-order behavior when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="ea78a-183">Substitua o exemplo de ordem z anterior com o XAML a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea78a-183">Replace the previous z-order example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     <span data-ttu-id="ea78a-184">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-184">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-185">O elemento de rótulo é pintado sobre o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-185">The label element is painted over the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="docking"></a><span data-ttu-id="ea78a-186">Encaixe</span><span class="sxs-lookup"><span data-stu-id="ea78a-186">Docking</span></span>  
 <span data-ttu-id="ea78a-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost>elemento suporta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] encaixe.</span><span class="sxs-lookup"><span data-stu-id="ea78a-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="ea78a-188">Definir o <xref:System.Windows.Controls.DockPanel.Dock%2A> propriedade anexa para encaixar o controle hospedado em um <xref:System.Windows.Controls.DockPanel> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-188">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="ea78a-189">Para encaixar o controle hospedado</span><span class="sxs-lookup"><span data-stu-id="ea78a-189">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="ea78a-190">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-190">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="ea78a-191">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-191">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-192">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> está encaixado à direita do elemento de <xref:System.Windows.Controls.DockPanel> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-192">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="ea78a-193">Definindo a visibilidade</span><span class="sxs-lookup"><span data-stu-id="ea78a-193">Setting Visibility</span></span>  
 <span data-ttu-id="ea78a-194">Você pode tornar seu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle invisível ou recolhê-lo definindo o <xref:System.Windows.UIElement.Visibility%2A> propriedade no <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-194">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="ea78a-195">Quando um controle estiver invisível, ele não será exibido, mas ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="ea78a-195">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="ea78a-196">Quando um controle estiver recolhido, ele não será exibido, mas também não ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="ea78a-196">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="ea78a-197">Para definir a visibilidade de um controle hospedado</span><span class="sxs-lookup"><span data-stu-id="ea78a-197">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="ea78a-198">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-198">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="ea78a-199">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, copie o código a seguir para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="ea78a-199">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="ea78a-200">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-200">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="ea78a-201">Clique o **clique para tornar invisível** botão para fazer o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento invisível.</span><span class="sxs-lookup"><span data-stu-id="ea78a-201">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="ea78a-202">Clique o **clique para recolher** botão para ocultar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento do layout inteiramente.</span><span class="sxs-lookup"><span data-stu-id="ea78a-202">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="ea78a-203">Quando o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] está recolhido, os elementos adjacentes serão reorganizados para ocupar o seu espaço.</span><span class="sxs-lookup"><span data-stu-id="ea78a-203">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="ea78a-204">Hospedando um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="ea78a-204">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="ea78a-205">Alguns [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles têm um tamanho fixo e não ser esticada para preencher o espaço disponível no layout.</span><span class="sxs-lookup"><span data-stu-id="ea78a-205">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="ea78a-206">Por exemplo, o <xref:System.Windows.Forms.MonthCalendar> controle exibe um mês em um espaço fixo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-206">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="ea78a-207">Para hospedar um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="ea78a-207">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="ea78a-208">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-208">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="ea78a-209">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-209">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-210">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é centralizado na linha de grade, mas ele não é estendido para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="ea78a-210">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="ea78a-211">Se a janela for grande o suficiente, você pode ver dois ou mais meses exibidos pelo hospedado <xref:System.Windows.Forms.MonthCalendar> controle, mas eles são centralizados na linha.</span><span class="sxs-lookup"><span data-stu-id="ea78a-211">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="ea78a-212">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de layout centraliza os elementos que não podem ser dimensionados para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="ea78a-212">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="ea78a-213">Dimensionamento</span><span class="sxs-lookup"><span data-stu-id="ea78a-213">Scaling</span></span>  
 <span data-ttu-id="ea78a-214">Ao contrário de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos, a maioria dos [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles não são escalonáveis continuamente.</span><span class="sxs-lookup"><span data-stu-id="ea78a-214">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, most [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls are not continuously scalable.</span></span> <span data-ttu-id="ea78a-215">Por padrão, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento dimensiona o seu controle hospedado quando possível.</span><span class="sxs-lookup"><span data-stu-id="ea78a-215">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element scales its hosted control when possible.</span></span>  <span data-ttu-id="ea78a-216">Para habilitar o escalonamento completos, defina o <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> propriedade o <xref:System.Windows.Forms.Integration.WindowsFormsHost> como true e o <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> propriedade <xref:System.Windows.Interop.CompositionMode.Full> ou <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="ea78a-216">To enable full-fledged scaling, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="ea78a-217">Para dimensionar um controle hospedado usando o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="ea78a-217">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="ea78a-218">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-218">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="ea78a-219">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-219">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-220">O controle hospedado e seus elementos adjacentes são dimensionados por um fator de 0,5.</span><span class="sxs-lookup"><span data-stu-id="ea78a-220">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="ea78a-221">No entanto, a fonte do controle hospedada não é redimensionada.</span><span class="sxs-lookup"><span data-stu-id="ea78a-221">However, the hosted control's font is not scaled.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a><span data-ttu-id="ea78a-222">Dimensionar um controle hospedado definindo IsRedirected como verdadeiro</span><span class="sxs-lookup"><span data-stu-id="ea78a-222">To scale a hosted control by setting IsRedirected to true</span></span>  
  
1.  <span data-ttu-id="ea78a-223">Substitua o exemplo anterior de dimensionamento com o seguinte XAML.</span><span class="sxs-lookup"><span data-stu-id="ea78a-223">Replace the previous scaling example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  <span data-ttu-id="ea78a-224">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-224">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-225">Fonte do controle hospedado, o controle hospedado e seus elementos adjacentes são dimensionadas por um fator de 0,5.</span><span class="sxs-lookup"><span data-stu-id="ea78a-225">The hosted control, its surrounding elements, and the hosted control's font are scaled by a factor of 0.5.</span></span>  
  
## <a name="rotating"></a><span data-ttu-id="ea78a-226">Girando</span><span class="sxs-lookup"><span data-stu-id="ea78a-226">Rotating</span></span>  
 <span data-ttu-id="ea78a-227">Ao contrário de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles não oferecem suporte a rotação.</span><span class="sxs-lookup"><span data-stu-id="ea78a-227">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls do not support rotation.</span></span> <span data-ttu-id="ea78a-228">Por padrão, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento gira com outros [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos quando uma transformação de rotação é aplicada.</span><span class="sxs-lookup"><span data-stu-id="ea78a-228">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements when a rotation transformation is applied.</span></span> <span data-ttu-id="ea78a-229">Qualquer valor de rotação diferente de 180 graus gera o <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> evento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-229">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>  <span data-ttu-id="ea78a-230">Para habilitar a rotação de qualquer ângulo, defina o <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> propriedade do <xref:System.Windows.Forms.Integration.WindowsFormsHost> como true e o <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> propriedade <xref:System.Windows.Interop.CompositionMode.Full> ou <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="ea78a-230">To enable rotating to any angle, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="ea78a-231">Para ver o efeito de rotação em um aplicativo híbrido</span><span class="sxs-lookup"><span data-stu-id="ea78a-231">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="ea78a-232">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-232">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="ea78a-233">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-233">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-234">O controle hospedado não é girado, mas seus elementos adjacentes são girados por um ângulo de 180 graus.</span><span class="sxs-lookup"><span data-stu-id="ea78a-234">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="ea78a-235">Você terá que redimensionar a janela para ver os elementos.</span><span class="sxs-lookup"><span data-stu-id="ea78a-235">You may have to resize the window to see the elements.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a><span data-ttu-id="ea78a-236">Para ver o efeito de rotação em um aplicativo híbrido quando IsRedirected é verdadeiro</span><span class="sxs-lookup"><span data-stu-id="ea78a-236">To see the effect of rotation in a hybrid application when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="ea78a-237">Substitua o exemplo anterior de rotação pelo seguinte XAML.</span><span class="sxs-lookup"><span data-stu-id="ea78a-237">Replace the previous rotation example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  <span data-ttu-id="ea78a-238">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-239">O controle hospedado é girado.</span><span class="sxs-lookup"><span data-stu-id="ea78a-239">The hosted control is rotated.</span></span>  <span data-ttu-id="ea78a-240">Observe que o <xref:System.Windows.Media.RotateTransform.Angle%2A> propriedade pode ser definida como qualquer valor.</span><span class="sxs-lookup"><span data-stu-id="ea78a-240">Note that the <xref:System.Windows.Media.RotateTransform.Angle%2A> property can be set to any value.</span></span> <span data-ttu-id="ea78a-241">Você terá que redimensionar a janela para ver os elementos.</span><span class="sxs-lookup"><span data-stu-id="ea78a-241">You may have to resize the window to see the elements.</span></span>  
  
## <a name="setting-padding-and-margins"></a><span data-ttu-id="ea78a-242">Margens e preenchimento de configuração</span><span class="sxs-lookup"><span data-stu-id="ea78a-242">Setting Padding and Margins</span></span>  
 <span data-ttu-id="ea78a-243">Preenchimento e margens de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout são semelhantes a enchimento e margens em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea78a-243">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="ea78a-244">Basta definir o <xref:System.Windows.Controls.Control.Padding%2A> e <xref:System.Windows.FrameworkElement.Margin%2A> propriedades de <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-244">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="ea78a-245">Para definir o preenchimento e margens de um controle hospedado</span><span class="sxs-lookup"><span data-stu-id="ea78a-245">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="ea78a-246">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-246">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="ea78a-247">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-247">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-248">As configurações de preenchimento e margem são aplicadas para hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles da mesma maneira que seriam aplicadas em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea78a-248">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="ea78a-249">Usando contêineres de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="ea78a-249">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="ea78a-250">fornece dois contêineres de layout dinâmico, <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="ea78a-250"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="ea78a-251">Você também pode usar esses contêineres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span><span class="sxs-lookup"><span data-stu-id="ea78a-251">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="ea78a-252">Para usar um contêiner de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="ea78a-252">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="ea78a-253">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="ea78a-253">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="ea78a-254">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, copie o código a seguir para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="ea78a-254">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="ea78a-255">Adicionar uma chamada para o `InitializeFlowLayoutPanel` método no construtor.</span><span class="sxs-lookup"><span data-stu-id="ea78a-255">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="ea78a-256">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea78a-256">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea78a-257">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento preenche o <xref:System.Windows.Controls.DockPanel>, e <xref:System.Windows.Forms.FlowLayoutPanel> organiza seus controles filhos no padrão <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea78a-257">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea78a-258">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea78a-258">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="ea78a-259">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="ea78a-259">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="ea78a-260">Considerações sobre o layout do elemento WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="ea78a-260">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="ea78a-261">Organizar janelas controles de formulários no exemplo do WPF</span><span class="sxs-lookup"><span data-stu-id="ea78a-261">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="ea78a-262">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="ea78a-262">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="ea78a-263">Passo a passo: hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea78a-263">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
