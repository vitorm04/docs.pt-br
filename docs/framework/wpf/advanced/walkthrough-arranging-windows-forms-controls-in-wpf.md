---
title: 'Instruções passo a passo: organizando controles dos Windows Forms no WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: f2cf82c54724a43a60fb9077c5731d4b4ad2cfd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549653"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="052d3-102">Instruções passo a passo: organizando controles dos Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="052d3-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="052d3-103">Este passo a passo mostra como usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] recursos de layout para organizar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles em um aplicativo híbrido.</span><span class="sxs-lookup"><span data-stu-id="052d3-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="052d3-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="052d3-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="052d3-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="052d3-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="052d3-106">Usando as configurações padrão de layout.</span><span class="sxs-lookup"><span data-stu-id="052d3-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="052d3-107">Dimensionando o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="052d3-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="052d3-108">Usando o posicionamento absoluto.</span><span class="sxs-lookup"><span data-stu-id="052d3-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="052d3-109">Especificando o tamanho explicitamente.</span><span class="sxs-lookup"><span data-stu-id="052d3-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="052d3-110">Definindo propriedades de layout.</span><span class="sxs-lookup"><span data-stu-id="052d3-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="052d3-111">Noções básicas sobre limitações da ordem z.</span><span class="sxs-lookup"><span data-stu-id="052d3-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="052d3-112">Encaixe.</span><span class="sxs-lookup"><span data-stu-id="052d3-112">Docking.</span></span>  
  
-   <span data-ttu-id="052d3-113">Definindo a visibilidade.</span><span class="sxs-lookup"><span data-stu-id="052d3-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="052d3-114">Hospedando um controle que não se alonga.</span><span class="sxs-lookup"><span data-stu-id="052d3-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="052d3-115">Dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="052d3-115">Scaling.</span></span>  
  
-   <span data-ttu-id="052d3-116">Girando.</span><span class="sxs-lookup"><span data-stu-id="052d3-116">Rotating.</span></span>  
  
-   <span data-ttu-id="052d3-117">Margens e preenchimento de configuração.</span><span class="sxs-lookup"><span data-stu-id="052d3-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="052d3-118">Usando contêineres de layout dinâmico.</span><span class="sxs-lookup"><span data-stu-id="052d3-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="052d3-119">Para uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [Organizando controles dos Windows Forms no WPF exemplo](http://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="052d3-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="052d3-120">Quando tiver terminado, você terá uma compreensão de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] recursos de layout no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-com base em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="052d3-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="052d3-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="052d3-121">Prerequisites</span></span>  
 <span data-ttu-id="052d3-122">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="052d3-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="052d3-123">.</span><span class="sxs-lookup"><span data-stu-id="052d3-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="052d3-124">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="052d3-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="052d3-125">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="052d3-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="052d3-126">Crie um projeto de aplicativo WPF chamado `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="052d3-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="052d3-127">No Gerenciador de Soluções, adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="052d3-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="052d3-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="052d3-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="052d3-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="052d3-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="052d3-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="052d3-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="052d3-131">Clique duas vezes em MainWindow.xaml para abri-lo no modo de exibição XAML.</span><span class="sxs-lookup"><span data-stu-id="052d3-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="052d3-132">No <xref:System.Windows.Window> elemento, adicione o seguinte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapeamento de namespace.</span><span class="sxs-lookup"><span data-stu-id="052d3-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="052d3-133">No <xref:System.Windows.Controls.Grid> conjunto de elementos de <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriedade `true` e definir cinco linhas e três colunas.</span><span class="sxs-lookup"><span data-stu-id="052d3-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="052d3-134">Usando as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="052d3-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="052d3-135">Por padrão, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento manipula o layout para hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="052d3-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="052d3-136">Para usar as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="052d3-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="052d3-137">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="052d3-138">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-139">O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> controle aparece no <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="052d3-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="052d3-140">O controle hospedado é dimensionado com base em seu conteúdo e o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é dimensionado para acomodar o controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="052d3-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="052d3-141">Dimensionando para o conteúdo</span><span class="sxs-lookup"><span data-stu-id="052d3-141">Sizing to Content</span></span>  
 <span data-ttu-id="052d3-142">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento garante que o controle hospedado é dimensionado para exibir seu conteúdo corretamente.</span><span class="sxs-lookup"><span data-stu-id="052d3-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="052d3-143">Para dimensionar para o Conteúdo</span><span class="sxs-lookup"><span data-stu-id="052d3-143">To size to content</span></span>  
  
1.  <span data-ttu-id="052d3-144">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="052d3-145">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-146">Os dois novos controles de botão são dimensionados para exibir a cadeia de caracteres de texto mais longa e maior tamanho da fonte corretamente e o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos são redimensionados para acomodar os controles hospedados.</span><span class="sxs-lookup"><span data-stu-id="052d3-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="052d3-147">Usando o posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="052d3-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="052d3-148">Você pode usar o posicionamento absoluto para colocar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento em qualquer lugar na interface do usuário (IU).</span><span class="sxs-lookup"><span data-stu-id="052d3-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="052d3-149">Para usar posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="052d3-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="052d3-150">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="052d3-151">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-152">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é colocado 20 pixels, do lado superior da célula da grade e a 20 pixels da esquerda.</span><span class="sxs-lookup"><span data-stu-id="052d3-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="052d3-153">Especificando o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="052d3-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="052d3-154">Você pode especificar o tamanho do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento usando o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="052d3-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="052d3-155">Para especificar o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="052d3-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="052d3-156">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="052d3-157">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-158">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> é definido como um tamanho de 50 pixels de largura por 70 pixels de altura, que é menor do que as configurações de layout padrão.</span><span class="sxs-lookup"><span data-stu-id="052d3-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="052d3-159">O conteúdo a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é reorganizado adequadamente.</span><span class="sxs-lookup"><span data-stu-id="052d3-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="052d3-160">Definindo propriedades de layout</span><span class="sxs-lookup"><span data-stu-id="052d3-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="052d3-161">Sempre defina propriedades relacionadas ao layout no controle hospedado usando as propriedades do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="052d3-162">Definindo propriedades de layout diretamente no controle hospedado produzirá resultados indesejados.</span><span class="sxs-lookup"><span data-stu-id="052d3-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="052d3-163">A definição de propriedades relacionadas ao layout no controle hospedado em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="052d3-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="052d3-164">Para ver os efeitos da definição das propriedades no controle hospedado</span><span class="sxs-lookup"><span data-stu-id="052d3-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="052d3-165">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="052d3-166">No Gerenciador de Soluções, clique duas vezes em MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="052d3-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="052d3-167">Abrir vb ou MainWindow.xaml.cs no Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="052d3-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="052d3-168">Copie o seguinte código para o `MainWindow` definição da classe.</span><span class="sxs-lookup"><span data-stu-id="052d3-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="052d3-169">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="052d3-170">Clique o **clique me** botão.</span><span class="sxs-lookup"><span data-stu-id="052d3-170">Click the **Click me** button.</span></span> <span data-ttu-id="052d3-171">O `button1_Click` conjuntos de manipulador de eventos de <xref:System.Windows.Forms.Control.Top%2A> e <xref:System.Windows.Forms.Control.Left%2A> propriedades no controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="052d3-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="052d3-172">Isso faz com que o controle hospedado seja reposicionado dentro de <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="052d3-173">O host mantém a mesma área da tela, mas o controle hospedado é cortado.</span><span class="sxs-lookup"><span data-stu-id="052d3-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="052d3-174">Em vez disso, o controle hospedado sempre deve preencher o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="052d3-175">Noções básicas sobre limitações da ordem z</span><span class="sxs-lookup"><span data-stu-id="052d3-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="052d3-176">Visível <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos sempre são desenhados sobre outros elementos do WPF e eles não são afetados pela ordem z.</span><span class="sxs-lookup"><span data-stu-id="052d3-176">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="052d3-177">Para ver esse comportamento de ordem z, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="052d3-177">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="052d3-178">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-178">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  <span data-ttu-id="052d3-179">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-179">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-180">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é pintado sobre o elemento de rótulo.</span><span class="sxs-lookup"><span data-stu-id="052d3-180">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  


## <a name="docking"></a><span data-ttu-id="052d3-181">Encaixe</span><span class="sxs-lookup"><span data-stu-id="052d3-181">Docking</span></span>  
 <span data-ttu-id="052d3-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento suporta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] encaixe.</span><span class="sxs-lookup"><span data-stu-id="052d3-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="052d3-183">Definir o <xref:System.Windows.Controls.DockPanel.Dock%2A> propriedade anexa para encaixar o controle hospedado em um <xref:System.Windows.Controls.DockPanel> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-183">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="052d3-184">Para encaixar o controle hospedado</span><span class="sxs-lookup"><span data-stu-id="052d3-184">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="052d3-185">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-185">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="052d3-186">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-186">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-187">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> está encaixado à direita do elemento de <xref:System.Windows.Controls.DockPanel> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-187">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="052d3-188">Definindo a visibilidade</span><span class="sxs-lookup"><span data-stu-id="052d3-188">Setting Visibility</span></span>  
 <span data-ttu-id="052d3-189">Você pode tornar seu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle invisível ou recolhê-lo definindo o <xref:System.Windows.UIElement.Visibility%2A> propriedade no <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-189">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="052d3-190">Quando um controle estiver invisível, ele não será exibido, mas ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="052d3-190">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="052d3-191">Quando um controle estiver recolhido, ele não será exibido, mas também não ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="052d3-191">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="052d3-192">Para definir a visibilidade de um controle hospedado</span><span class="sxs-lookup"><span data-stu-id="052d3-192">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="052d3-193">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-193">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="052d3-194">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, copie o código a seguir para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="052d3-194">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="052d3-195">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-195">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="052d3-196">Clique o **clique para tornar invisível** botão para fazer o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento invisível.</span><span class="sxs-lookup"><span data-stu-id="052d3-196">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="052d3-197">Clique o **clique para recolher** botão para ocultar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento do layout inteiramente.</span><span class="sxs-lookup"><span data-stu-id="052d3-197">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="052d3-198">Quando o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] está recolhido, os elementos adjacentes serão reorganizados para ocupar o seu espaço.</span><span class="sxs-lookup"><span data-stu-id="052d3-198">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="052d3-199">Hospedando um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="052d3-199">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="052d3-200">Alguns [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles têm um tamanho fixo e não ser esticada para preencher o espaço disponível no layout.</span><span class="sxs-lookup"><span data-stu-id="052d3-200">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="052d3-201">Por exemplo, o <xref:System.Windows.Forms.MonthCalendar> controle exibe um mês em um espaço fixo.</span><span class="sxs-lookup"><span data-stu-id="052d3-201">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="052d3-202">Para hospedar um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="052d3-202">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="052d3-203">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-203">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="052d3-204">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-204">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-205">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é centralizado na linha de grade, mas ele não é estendido para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="052d3-205">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="052d3-206">Se a janela for grande o suficiente, você pode ver dois ou mais meses exibidos pelo hospedado <xref:System.Windows.Forms.MonthCalendar> controle, mas eles são centralizados na linha.</span><span class="sxs-lookup"><span data-stu-id="052d3-206">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="052d3-207">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de layout centraliza os elementos que não podem ser dimensionados para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="052d3-207">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="052d3-208">Dimensionamento</span><span class="sxs-lookup"><span data-stu-id="052d3-208">Scaling</span></span>  
 <span data-ttu-id="052d3-209">Diferentemente dos elementos do WPF, a maioria dos controles de formulários do Windows não são escalonáveis continuamente.</span><span class="sxs-lookup"><span data-stu-id="052d3-209">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="052d3-210">Para fornecer dimensionamento personalizado, você deve substituir o <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="052d3-210">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span> 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="052d3-211">Para dimensionar um controle hospedado usando o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="052d3-211">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="052d3-212">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-212">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="052d3-213">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-213">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-214">O controle hospedado e seus elementos adjacentes são dimensionados por um fator de 0,5.</span><span class="sxs-lookup"><span data-stu-id="052d3-214">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="052d3-215">No entanto, a fonte do controle hospedada não é redimensionada.</span><span class="sxs-lookup"><span data-stu-id="052d3-215">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="052d3-216">Girando</span><span class="sxs-lookup"><span data-stu-id="052d3-216">Rotating</span></span>  
 <span data-ttu-id="052d3-217">Diferentemente dos elementos do WPF, controles de formulários do Windows não oferecem suporte a rotação.</span><span class="sxs-lookup"><span data-stu-id="052d3-217">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="052d3-218">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento não gira com outros elementos WPF quando uma transformação de rotação é aplicada.</span><span class="sxs-lookup"><span data-stu-id="052d3-218">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="052d3-219">Qualquer valor de rotação diferente de 180 graus gera o <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> evento.</span><span class="sxs-lookup"><span data-stu-id="052d3-219">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="052d3-220">Para ver o efeito de rotação em um aplicativo híbrido</span><span class="sxs-lookup"><span data-stu-id="052d3-220">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="052d3-221">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-221">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="052d3-222">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-222">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-223">O controle hospedado não é girado, mas seus elementos adjacentes são girados por um ângulo de 180 graus.</span><span class="sxs-lookup"><span data-stu-id="052d3-223">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="052d3-224">Você terá que redimensionar a janela para ver os elementos.</span><span class="sxs-lookup"><span data-stu-id="052d3-224">You may have to resize the window to see the elements.</span></span>  
 

## <a name="setting-padding-and-margins"></a><span data-ttu-id="052d3-225">Margens e preenchimento de configuração</span><span class="sxs-lookup"><span data-stu-id="052d3-225">Setting Padding and Margins</span></span>  
 <span data-ttu-id="052d3-226">Preenchimento e margens de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout são semelhantes a enchimento e margens em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="052d3-226">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="052d3-227">Basta definir o <xref:System.Windows.Controls.Control.Padding%2A> e <xref:System.Windows.FrameworkElement.Margin%2A> propriedades de <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-227">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="052d3-228">Para definir o preenchimento e margens de um controle hospedado</span><span class="sxs-lookup"><span data-stu-id="052d3-228">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="052d3-229">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-229">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="052d3-230">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-230">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-231">As configurações de preenchimento e margem são aplicadas para hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles da mesma maneira que seriam aplicadas em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="052d3-231">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="052d3-232">Usando contêineres de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="052d3-232">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="052d3-233"> fornece dois contêineres de layout dinâmico, <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="052d3-233"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="052d3-234">Você também pode usar esses contêineres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span><span class="sxs-lookup"><span data-stu-id="052d3-234">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="052d3-235">Para usar um contêiner de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="052d3-235">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="052d3-236">Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="052d3-236">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="052d3-237">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, copie o código a seguir para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="052d3-237">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="052d3-238">Adicionar uma chamada para o `InitializeFlowLayoutPanel` método no construtor.</span><span class="sxs-lookup"><span data-stu-id="052d3-238">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="052d3-239">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052d3-239">Press F5 to build and run the application.</span></span> <span data-ttu-id="052d3-240">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento preenche o <xref:System.Windows.Controls.DockPanel>, e <xref:System.Windows.Forms.FlowLayoutPanel> organiza seus controles filhos no padrão <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="052d3-240">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="052d3-241">Consulte também</span><span class="sxs-lookup"><span data-stu-id="052d3-241">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="052d3-242">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="052d3-242">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="052d3-243">Considerações sobre o layout do elemento WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="052d3-243">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="052d3-244">Organizar janelas controles de formulários no exemplo do WPF</span><span class="sxs-lookup"><span data-stu-id="052d3-244">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="052d3-245">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="052d3-245">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="052d3-246">Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="052d3-246">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
