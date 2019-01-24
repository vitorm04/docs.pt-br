---
title: 'Passo a passo: Organizar o Windows Forms a controles no WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 5947168fabfe8ec22203029d9ec89b9719728413
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697615"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="7eb97-102">Passo a passo: Organizar o Windows Forms a controles no WPF</span><span class="sxs-lookup"><span data-stu-id="7eb97-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="7eb97-103">Este passo a passo mostra como usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] recursos de layout para organizar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles em um aplicativo híbrido.</span><span class="sxs-lookup"><span data-stu-id="7eb97-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="7eb97-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="7eb97-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="7eb97-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="7eb97-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="7eb97-106">Usando as configurações padrão de layout.</span><span class="sxs-lookup"><span data-stu-id="7eb97-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="7eb97-107">Dimensionando o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="7eb97-108">Usando o posicionamento absoluto.</span><span class="sxs-lookup"><span data-stu-id="7eb97-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="7eb97-109">Especificando o tamanho explicitamente.</span><span class="sxs-lookup"><span data-stu-id="7eb97-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="7eb97-110">Definindo propriedades de layout.</span><span class="sxs-lookup"><span data-stu-id="7eb97-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="7eb97-111">Noções básicas sobre limitações da ordem z.</span><span class="sxs-lookup"><span data-stu-id="7eb97-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="7eb97-112">Encaixe.</span><span class="sxs-lookup"><span data-stu-id="7eb97-112">Docking.</span></span>  
  
-   <span data-ttu-id="7eb97-113">Definindo a visibilidade.</span><span class="sxs-lookup"><span data-stu-id="7eb97-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="7eb97-114">Hospedando um controle que não se alonga.</span><span class="sxs-lookup"><span data-stu-id="7eb97-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="7eb97-115">Dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-115">Scaling.</span></span>  
  
-   <span data-ttu-id="7eb97-116">Girando.</span><span class="sxs-lookup"><span data-stu-id="7eb97-116">Rotating.</span></span>  
  
-   <span data-ttu-id="7eb97-117">Margens e preenchimento de configuração.</span><span class="sxs-lookup"><span data-stu-id="7eb97-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="7eb97-118">Usando contêineres de layout dinâmico.</span><span class="sxs-lookup"><span data-stu-id="7eb97-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="7eb97-119">Para obter uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [Organizando controles do Windows Forms no WPF de exemplo](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="7eb97-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="7eb97-120">Quando tiver terminado, você terá um entendimento dos [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] recursos de layout no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-com base em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7eb97-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7eb97-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7eb97-121">Prerequisites</span></span>  

<span data-ttu-id="7eb97-122">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="creating-the-project"></a><span data-ttu-id="7eb97-123">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="7eb97-123">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="7eb97-124">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="7eb97-124">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="7eb97-125">Crie um projeto de aplicativo WPF chamado `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="7eb97-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="7eb97-126">No Gerenciador de Soluções, adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="7eb97-126">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="7eb97-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="7eb97-127">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="7eb97-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="7eb97-128">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="7eb97-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="7eb97-129">System.Drawing</span></span>  
  
3.  <span data-ttu-id="7eb97-130">Clique duas vezes em MainWindow.xaml para abri-lo no modo de exibição XAML.</span><span class="sxs-lookup"><span data-stu-id="7eb97-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="7eb97-131">No <xref:System.Windows.Window> elemento, adicione o seguinte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapeamento de namespace.</span><span class="sxs-lookup"><span data-stu-id="7eb97-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="7eb97-132">No <xref:System.Windows.Controls.Grid> conjunto de elementos a <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriedade `true` e defina cinco linhas e três colunas.</span><span class="sxs-lookup"><span data-stu-id="7eb97-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="7eb97-133">Usando as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="7eb97-133">Using Default Layout Settings</span></span>  
 <span data-ttu-id="7eb97-134">Por padrão, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento manipula o layout para hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="7eb97-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="7eb97-135">Para usar as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="7eb97-135">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="7eb97-136">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="7eb97-137">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-138">O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> controle aparece no <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="7eb97-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="7eb97-139">O controle hospedado é dimensionado com base em seu conteúdo e o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é dimensionado para acomodar o controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="7eb97-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="7eb97-140">Dimensionando para o conteúdo</span><span class="sxs-lookup"><span data-stu-id="7eb97-140">Sizing to Content</span></span>  
 <span data-ttu-id="7eb97-141">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento garante que o controle hospedado é dimensionado para exibir seu conteúdo corretamente.</span><span class="sxs-lookup"><span data-stu-id="7eb97-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="7eb97-142">Para dimensionar para o Conteúdo</span><span class="sxs-lookup"><span data-stu-id="7eb97-142">To size to content</span></span>  
  
1.  <span data-ttu-id="7eb97-143">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="7eb97-144">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-145">Os dois novos controles de botão são dimensionados para exibir a sequência de texto mais longa e maior tamanho de fonte corretamente e o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos são redimensionados para acomodar os controles hospedados.</span><span class="sxs-lookup"><span data-stu-id="7eb97-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="7eb97-146">Usando o posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="7eb97-146">Using Absolute Positioning</span></span>  
 <span data-ttu-id="7eb97-147">Você pode usar posicionamento absoluto para colocar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento em qualquer lugar na interface do usuário (IU).</span><span class="sxs-lookup"><span data-stu-id="7eb97-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="7eb97-148">Para usar posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="7eb97-148">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="7eb97-149">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="7eb97-150">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-151">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é colocado a 20 pixels do lado superior da célula da grade e 20 pixels da esquerda.</span><span class="sxs-lookup"><span data-stu-id="7eb97-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="7eb97-152">Especificando o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="7eb97-152">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="7eb97-153">Você pode especificar o tamanho do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento usando o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="7eb97-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="7eb97-154">Para especificar o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="7eb97-154">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="7eb97-155">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="7eb97-156">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-157">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> é definido como um tamanho de 50 pixels de largura por 70 pixels de altura, que é menor do que as configurações de layout padrão.</span><span class="sxs-lookup"><span data-stu-id="7eb97-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="7eb97-158">O conteúdo a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é reorganizado adequadamente.</span><span class="sxs-lookup"><span data-stu-id="7eb97-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="7eb97-159">Definindo propriedades de layout</span><span class="sxs-lookup"><span data-stu-id="7eb97-159">Setting Layout Properties</span></span>  
 <span data-ttu-id="7eb97-160">Sempre defina propriedades relacionadas ao layout no controle hospedado usando as propriedades do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="7eb97-161">Definindo propriedades de layout diretamente no controle hospedado produzirá resultados indesejados.</span><span class="sxs-lookup"><span data-stu-id="7eb97-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="7eb97-162">Definição de propriedades relacionadas ao layout no controle hospedado em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="7eb97-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="7eb97-163">Para ver os efeitos da definição das propriedades no controle hospedado</span><span class="sxs-lookup"><span data-stu-id="7eb97-163">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="7eb97-164">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="7eb97-165">No Gerenciador de Soluções, clique duas vezes em MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="7eb97-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="7eb97-166">Abrir vb ou MainWindow.xaml.cs no Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7eb97-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="7eb97-167">Copie o seguinte código para o `MainWindow` definição de classe.</span><span class="sxs-lookup"><span data-stu-id="7eb97-167">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4.  <span data-ttu-id="7eb97-168">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-168">Press F5 to build and run the application.</span></span>

5.  <span data-ttu-id="7eb97-169">Clique o **Click me** botão.</span><span class="sxs-lookup"><span data-stu-id="7eb97-169">Click the **Click me** button.</span></span> <span data-ttu-id="7eb97-170">O `button1_Click` conjuntos de manipulador de eventos do <xref:System.Windows.Forms.Control.Top%2A> e <xref:System.Windows.Forms.Control.Left%2A> propriedades no controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="7eb97-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="7eb97-171">Isso faz com que o controle hospedado seja reposicionado dentro do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="7eb97-172">O host mantém a mesma área da tela, mas o controle hospedado é cortado.</span><span class="sxs-lookup"><span data-stu-id="7eb97-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="7eb97-173">Em vez disso, o controle hospedado sempre deve preencher o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="7eb97-174">Noções básicas sobre limitações da ordem z</span><span class="sxs-lookup"><span data-stu-id="7eb97-174">Understanding Z-Order Limitations</span></span>
 <span data-ttu-id="7eb97-175">Visível <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos sempre são desenhados sobre outros elementos do WPF, e eles não são afetados pela ordem z.</span><span class="sxs-lookup"><span data-stu-id="7eb97-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="7eb97-176">Para ver esse comportamento da ordem z, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7eb97-176">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="7eb97-177">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2.  <span data-ttu-id="7eb97-178">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-179">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é pintado sobre o elemento de rótulo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>


## <a name="docking"></a><span data-ttu-id="7eb97-180">Encaixe</span><span class="sxs-lookup"><span data-stu-id="7eb97-180">Docking</span></span>
 <span data-ttu-id="7eb97-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> dá suporte ao elemento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] encaixe.</span><span class="sxs-lookup"><span data-stu-id="7eb97-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="7eb97-182">Defina as <xref:System.Windows.Controls.DockPanel.Dock%2A> propriedade anexada para encaixar o controle hospedado em um <xref:System.Windows.Controls.DockPanel> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="7eb97-183">Para encaixar o controle hospedado</span><span class="sxs-lookup"><span data-stu-id="7eb97-183">To dock a hosted control</span></span>

1.  <span data-ttu-id="7eb97-184">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2.  <span data-ttu-id="7eb97-185">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-186">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> é encaixado à direita do elemento a <xref:System.Windows.Controls.DockPanel> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="7eb97-187">Definindo a visibilidade</span><span class="sxs-lookup"><span data-stu-id="7eb97-187">Setting Visibility</span></span>
 <span data-ttu-id="7eb97-188">Você pode fazer sua [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle invisível ou recolhê-lo definindo o <xref:System.Windows.UIElement.Visibility%2A> propriedade no <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="7eb97-189">Quando um controle estiver invisível, ele não será exibido, mas ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="7eb97-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="7eb97-190">Quando um controle estiver recolhido, ele não será exibido, mas também não ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="7eb97-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="7eb97-191">Para definir a visibilidade de um controle hospedado</span><span class="sxs-lookup"><span data-stu-id="7eb97-191">To set the visibility of a hosted control</span></span>

1.  <span data-ttu-id="7eb97-192">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2.  <span data-ttu-id="7eb97-193">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, copie o código a seguir para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="7eb97-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3.  <span data-ttu-id="7eb97-194">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-194">Press F5 to build and run the application.</span></span>

4.  <span data-ttu-id="7eb97-195">Clique o **clique para tornar invisíveis** botão para fazer o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento invisível.</span><span class="sxs-lookup"><span data-stu-id="7eb97-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5.  <span data-ttu-id="7eb97-196">Clique o **clique para recolher** botão para ocultar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento do layout completamente.</span><span class="sxs-lookup"><span data-stu-id="7eb97-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="7eb97-197">Quando o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle estiver recolhido, os elementos adjacentes serão reorganizados para ocupar o seu espaço.</span><span class="sxs-lookup"><span data-stu-id="7eb97-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="7eb97-198">Hospedando um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="7eb97-198">Hosting a Control That Does Not Stretch</span></span>
 <span data-ttu-id="7eb97-199">Alguns [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles têm um tamanho fixo e não se esticam para preencher o espaço disponível no layout.</span><span class="sxs-lookup"><span data-stu-id="7eb97-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="7eb97-200">Por exemplo, o <xref:System.Windows.Forms.MonthCalendar> controle exibe um mês em um espaço fixo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="7eb97-201">Para hospedar um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="7eb97-201">To host a control that does not stretch</span></span>

1.  <span data-ttu-id="7eb97-202">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2.  <span data-ttu-id="7eb97-203">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-204">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é centralizado na linha de grade, mas ele não é alongado para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="7eb97-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="7eb97-205">Se a janela é grande o suficiente, você poderá ver duas ou mais meses exibidos pelo hospedado <xref:System.Windows.Forms.MonthCalendar> controle, mas eles são centralizados na linha.</span><span class="sxs-lookup"><span data-stu-id="7eb97-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="7eb97-206">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de layout centraliza os elementos que não podem ser dimensionados para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="7eb97-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="7eb97-207">Dimensionamento</span><span class="sxs-lookup"><span data-stu-id="7eb97-207">Scaling</span></span>
 <span data-ttu-id="7eb97-208">Diferentemente dos elementos do WPF, a maioria dos controles de formulários do Windows não são escalonáveis continuamente.</span><span class="sxs-lookup"><span data-stu-id="7eb97-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="7eb97-209">Para fornecer dimensionamento personalizado, você deve substituir o <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="7eb97-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="7eb97-210">Para dimensionar um controle hospedado usando o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="7eb97-210">To scale a hosted control by using the default behavior</span></span>

1.  <span data-ttu-id="7eb97-211">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2.  <span data-ttu-id="7eb97-212">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-213">O controle hospedado e seus elementos adjacentes são dimensionados por um fator de 0,5.</span><span class="sxs-lookup"><span data-stu-id="7eb97-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="7eb97-214">No entanto, a fonte do controle hospedada não é redimensionada.</span><span class="sxs-lookup"><span data-stu-id="7eb97-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="7eb97-215">Girando</span><span class="sxs-lookup"><span data-stu-id="7eb97-215">Rotating</span></span>
 <span data-ttu-id="7eb97-216">Diferentemente dos elementos do WPF, controles dos Windows Forms não oferecem suporte a rotação.</span><span class="sxs-lookup"><span data-stu-id="7eb97-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="7eb97-217">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento não gira com outros elementos do WPF quando uma transformação de rotação é aplicada.</span><span class="sxs-lookup"><span data-stu-id="7eb97-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="7eb97-218">Qualquer valor de rotação diferente de 180 graus gera o <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> eventos.</span><span class="sxs-lookup"><span data-stu-id="7eb97-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="7eb97-219">Para ver o efeito de rotação em um aplicativo híbrido</span><span class="sxs-lookup"><span data-stu-id="7eb97-219">To see the effect of rotation in a hybrid application</span></span>

1.  <span data-ttu-id="7eb97-220">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2.  <span data-ttu-id="7eb97-221">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-222">O controle hospedado não é girado, mas seus elementos adjacentes são girados por um ângulo de 180 graus.</span><span class="sxs-lookup"><span data-stu-id="7eb97-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="7eb97-223">Você terá que redimensionar a janela para ver os elementos.</span><span class="sxs-lookup"><span data-stu-id="7eb97-223">You may have to resize the window to see the elements.</span></span>


## <a name="setting-padding-and-margins"></a><span data-ttu-id="7eb97-224">Margens e preenchimento de configuração</span><span class="sxs-lookup"><span data-stu-id="7eb97-224">Setting Padding and Margins</span></span>
 <span data-ttu-id="7eb97-225">Preenchimento e margens em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout são semelhantes a preenchimento e margens em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7eb97-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="7eb97-226">Basta definir a <xref:System.Windows.Controls.Control.Padding%2A> e <xref:System.Windows.FrameworkElement.Margin%2A> propriedades sobre o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="7eb97-227">Para definir o preenchimento e margens de um controle hospedado</span><span class="sxs-lookup"><span data-stu-id="7eb97-227">To set padding and margins for a hosted control</span></span>

1.  <span data-ttu-id="7eb97-228">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2.  <span data-ttu-id="7eb97-229">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-230">As configurações de preenchimento e margem são aplicadas para hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles da mesma maneira que seriam aplicadas em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7eb97-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="7eb97-231">Usando contêineres de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="7eb97-231">Using Dynamic Layout Containers</span></span>
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="7eb97-232">fornece dois contêineres de layout dinâmico <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="7eb97-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="7eb97-233">Você também pode usar esses contêineres em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span><span class="sxs-lookup"><span data-stu-id="7eb97-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="7eb97-234">Para usar um contêiner de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="7eb97-234">To use a dynamic layout container</span></span>

1.  <span data-ttu-id="7eb97-235">Copie o seguinte XAML para o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="7eb97-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2.  <span data-ttu-id="7eb97-236">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, copie o código a seguir para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="7eb97-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3.  <span data-ttu-id="7eb97-237">Adicione uma chamada para o `InitializeFlowLayoutPanel` método no construtor.</span><span class="sxs-lookup"><span data-stu-id="7eb97-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="7eb97-238">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7eb97-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="7eb97-239">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento preenche os <xref:System.Windows.Controls.DockPanel>, e <xref:System.Windows.Forms.FlowLayoutPanel> organiza seus controles filho no padrão <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="7eb97-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb97-240">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7eb97-240">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7eb97-241">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7eb97-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="7eb97-242">Considerações sobre o layout do elemento WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="7eb97-242">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="7eb97-243">Organizar o Windows Forms a controles no WPF de exemplo</span><span class="sxs-lookup"><span data-stu-id="7eb97-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="7eb97-244">Passo a passo: Hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="7eb97-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="7eb97-245">Passo a passo: Hospedando um controle composto do WPF nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7eb97-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
