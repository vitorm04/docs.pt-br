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
ms.openlocfilehash: 484895db539b288bf388ff6c2ce3c29db55080b1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197848"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="26ffe-102">Instruções passo a passo: organizando controles dos Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="26ffe-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="26ffe-103">Este tutorial mostra como usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] recursos de layout para organizar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles em um aplicativo híbrido.</span><span class="sxs-lookup"><span data-stu-id="26ffe-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="26ffe-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="26ffe-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="26ffe-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="26ffe-105">Creating the project.</span></span>
- <span data-ttu-id="26ffe-106">Usando as configurações padrão de layout.</span><span class="sxs-lookup"><span data-stu-id="26ffe-106">Using default layout settings.</span></span>
- <span data-ttu-id="26ffe-107">Dimensionando o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-107">Sizing to content.</span></span>
- <span data-ttu-id="26ffe-108">Usando o posicionamento absoluto.</span><span class="sxs-lookup"><span data-stu-id="26ffe-108">Using absolute positioning.</span></span>
- <span data-ttu-id="26ffe-109">Especificando o tamanho explicitamente.</span><span class="sxs-lookup"><span data-stu-id="26ffe-109">Specifying size explicitly.</span></span>
- <span data-ttu-id="26ffe-110">Definindo propriedades de layout.</span><span class="sxs-lookup"><span data-stu-id="26ffe-110">Setting layout properties.</span></span>
- <span data-ttu-id="26ffe-111">Noções básicas sobre limitações da ordem z.</span><span class="sxs-lookup"><span data-stu-id="26ffe-111">Understanding z-order limitations.</span></span>
- <span data-ttu-id="26ffe-112">Encaixe.</span><span class="sxs-lookup"><span data-stu-id="26ffe-112">Docking.</span></span>
- <span data-ttu-id="26ffe-113">Definindo a visibilidade.</span><span class="sxs-lookup"><span data-stu-id="26ffe-113">Setting visibility.</span></span>
- <span data-ttu-id="26ffe-114">Hospedando um controle que não se alonga.</span><span class="sxs-lookup"><span data-stu-id="26ffe-114">Hosting a control that does not stretch.</span></span>
- <span data-ttu-id="26ffe-115">Dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="26ffe-115">Scaling.</span></span>
- <span data-ttu-id="26ffe-116">Girando.</span><span class="sxs-lookup"><span data-stu-id="26ffe-116">Rotating.</span></span>
- <span data-ttu-id="26ffe-117">Margens e preenchimento de configuração.</span><span class="sxs-lookup"><span data-stu-id="26ffe-117">Setting padding and margins.</span></span>
- <span data-ttu-id="26ffe-118">Usando contêineres de layout dinâmico.</span><span class="sxs-lookup"><span data-stu-id="26ffe-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="26ffe-119">Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [organizando Windows Forms controles no WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="26ffe-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="26ffe-120">Quando tiver terminado, você terá uma compreensão dos recursos de layout de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em aplicativos baseados em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26ffe-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26ffe-121">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="26ffe-121">Prerequisites</span></span>

<span data-ttu-id="26ffe-122">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="26ffe-123">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="26ffe-123">Creating the Project</span></span>

<span data-ttu-id="26ffe-124">Para criar e configurar o projeto, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-124">To create and set up the project, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-125">Crie um projeto de aplicativo WPF chamado `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="26ffe-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="26ffe-126">Em Gerenciador de Soluções, adicione referências aos seguintes assemblies:</span><span class="sxs-lookup"><span data-stu-id="26ffe-126">In Solution Explorer, add references to the following assemblies:</span></span>

    - <span data-ttu-id="26ffe-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="26ffe-127">WindowsFormsIntegration</span></span>
    - <span data-ttu-id="26ffe-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="26ffe-128">System.Windows.Forms</span></span>
    - <span data-ttu-id="26ffe-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="26ffe-129">System.Drawing</span></span>

3. <span data-ttu-id="26ffe-130">Clique duas vezes em *MainWindow. XAML* para abri-lo no modo de exibição XAML.</span><span class="sxs-lookup"><span data-stu-id="26ffe-130">Double-click *MainWindow.xaml* to open it in XAML view.</span></span>

4. <span data-ttu-id="26ffe-131">No elemento <xref:System.Windows.Window>, adicione o seguinte mapeamento de namespace de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26ffe-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="26ffe-132">No elemento <xref:System.Windows.Controls.Grid>, defina a propriedade <xref:System.Windows.Controls.Grid.ShowGridLines%2A> como `true` e defina cinco linhas e três colunas.</span><span class="sxs-lookup"><span data-stu-id="26ffe-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="26ffe-133">Usando as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="26ffe-133">Using Default Layout Settings</span></span>

<span data-ttu-id="26ffe-134">Por padrão, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> manipula o layout do controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado.</span><span class="sxs-lookup"><span data-stu-id="26ffe-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="26ffe-135">Para usar as configurações de layout padrão, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-135">To use default layout settings, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-136">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="26ffe-137">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-137">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-138">O controle de <xref:System.Windows.Forms.Button?displayProperty=nameWithType> de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aparece na <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="26ffe-139">O controle hospedado é dimensionado com base em seu conteúdo e o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é dimensionado para acomodar o controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="26ffe-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="26ffe-140">Dimensionando para o conteúdo</span><span class="sxs-lookup"><span data-stu-id="26ffe-140">Sizing to Content</span></span>

<span data-ttu-id="26ffe-141">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> garante que o controle hospedado seja dimensionado para exibir seu conteúdo corretamente.</span><span class="sxs-lookup"><span data-stu-id="26ffe-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

<span data-ttu-id="26ffe-142">Para dimensionar para o conteúdo, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-142">To size to content, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-143">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="26ffe-144">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-144">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-145">Os dois novos controles de botão são dimensionados para exibir a cadeia de caracteres de texto mais longa e o tamanho de fonte maior corretamente, e os elementos de <xref:System.Windows.Forms.Integration.WindowsFormsHost> são redimensionados para acomodar os controles hospedados.</span><span class="sxs-lookup"><span data-stu-id="26ffe-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="26ffe-146">Usando o posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="26ffe-146">Using Absolute Positioning</span></span>

<span data-ttu-id="26ffe-147">Você pode usar o posicionamento absoluto para posicionar o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> em qualquer lugar na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="26ffe-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

<span data-ttu-id="26ffe-148">Para usar o posicionamento absoluto, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-148">To use absolute positioning, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-149">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="26ffe-150">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-150">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-151">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é colocado em 20 pixels do lado superior da célula de grade e 20 pixels à esquerda.</span><span class="sxs-lookup"><span data-stu-id="26ffe-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="26ffe-152">Especificando o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="26ffe-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="26ffe-153">Você pode especificar o tamanho do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> usando as propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

<span data-ttu-id="26ffe-154">Para especificar o tamanho explicitamente, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-154">To specify size explicitly, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-155">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="26ffe-156">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-156">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-157">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é definido com um tamanho de 50 pixels de largura por 70 pixels de altura, o que é menor do que as configurações de layout padrão.</span><span class="sxs-lookup"><span data-stu-id="26ffe-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="26ffe-158">O conteúdo do controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é reorganizado de acordo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="26ffe-159">Definindo propriedades de layout</span><span class="sxs-lookup"><span data-stu-id="26ffe-159">Setting Layout Properties</span></span>

<span data-ttu-id="26ffe-160">Sempre defina propriedades relacionadas ao layout no controle hospedado usando as propriedades do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="26ffe-161">Definindo propriedades de layout diretamente no controle hospedado produzirá resultados indesejados.</span><span class="sxs-lookup"><span data-stu-id="26ffe-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="26ffe-162">Definir propriedades relacionadas a layout no controle hospedado no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="26ffe-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

<span data-ttu-id="26ffe-163">Para ver os efeitos das propriedades de configuração no controle hospedado, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-163">To see the effects of setting properties on the hosted control, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-164">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="26ffe-165">Em **Gerenciador de soluções**, clique duas vezes em *MainWindow. XAML. vb* ou *MainWindow.XAML.cs* para abri-lo no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="26ffe-165">In **Solution Explorer**, double-click *MainWindow.xaml.vb* or *MainWindow.xaml.cs* to open it in the Code Editor.</span></span>

3. <span data-ttu-id="26ffe-166">Copie o seguinte código para a definição de classe de `MainWindow`:</span><span class="sxs-lookup"><span data-stu-id="26ffe-166">Copy the following code into the `MainWindow` class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="26ffe-167">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-167">Press <kbd>F5</kbd> to build and run the application.</span></span>

5. <span data-ttu-id="26ffe-168">Clique no botão **clicar em mim** .</span><span class="sxs-lookup"><span data-stu-id="26ffe-168">Click the **Click me** button.</span></span> <span data-ttu-id="26ffe-169">O manipulador de eventos `button1_Click` define as propriedades <xref:System.Windows.Forms.Control.Top%2A> e <xref:System.Windows.Forms.Control.Left%2A> no controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="26ffe-169">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="26ffe-170">Isso faz com que o controle hospedado seja reposicionado dentro do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-170">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="26ffe-171">O host mantém a mesma área da tela, mas o controle hospedado é cortado.</span><span class="sxs-lookup"><span data-stu-id="26ffe-171">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="26ffe-172">Em vez disso, o controle hospedado sempre deve preencher o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-172">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="26ffe-173">Noções básicas sobre limitações da ordem z</span><span class="sxs-lookup"><span data-stu-id="26ffe-173">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="26ffe-174">Elementos de <xref:System.Windows.Forms.Integration.WindowsFormsHost> visíveis sempre são desenhados sobre outros elementos do WPF e não são afetados pela ordem z.</span><span class="sxs-lookup"><span data-stu-id="26ffe-174">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="26ffe-175">Para ver esse comportamento de ordem z, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="26ffe-175">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="26ffe-176">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-176">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="26ffe-177">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-177">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-178">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é pintado sobre o elemento Label.</span><span class="sxs-lookup"><span data-stu-id="26ffe-178">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="26ffe-179">Encaixe</span><span class="sxs-lookup"><span data-stu-id="26ffe-179">Docking</span></span>

<span data-ttu-id="26ffe-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento dá suporte ao encaixe de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26ffe-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="26ffe-181">Defina a propriedade <xref:System.Windows.Controls.DockPanel.Dock%2A> anexada para encaixar o controle hospedado em um elemento <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-181">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

<span data-ttu-id="26ffe-182">Para encaixar um controle hospedado, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-182">To dock a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-183">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-183">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="26ffe-184">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-184">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-185">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é encaixado no lado direito do elemento <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-185">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="26ffe-186">Definindo a visibilidade</span><span class="sxs-lookup"><span data-stu-id="26ffe-186">Setting Visibility</span></span>

<span data-ttu-id="26ffe-187">Você pode tornar seu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle invisível ou recolhê-lo definindo a propriedade <xref:System.Windows.UIElement.Visibility%2A> no elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-187">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="26ffe-188">Quando um controle estiver invisível, ele não será exibido, mas ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="26ffe-188">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="26ffe-189">Quando um controle estiver recolhido, ele não será exibido, mas também não ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="26ffe-189">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

<span data-ttu-id="26ffe-190">Para definir a visibilidade de um controle hospedado, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-190">To set the visibility of a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-191">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-191">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="26ffe-192">Em *MainWindow. XAML. vb* ou *MainWindow.XAML.cs*, copie o seguinte código para a definição de classe:</span><span class="sxs-lookup"><span data-stu-id="26ffe-192">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="26ffe-193">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-193">Press <kbd>F5</kbd> to build and run the application.</span></span>

4. <span data-ttu-id="26ffe-194">Clique no botão **clique para tornar invisível** para tornar o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> invisível.</span><span class="sxs-lookup"><span data-stu-id="26ffe-194">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="26ffe-195">Clique no botão **clique para recolher** para ocultar totalmente o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> do layout.</span><span class="sxs-lookup"><span data-stu-id="26ffe-195">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="26ffe-196">Quando o controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é recolhido, os elementos circundantes são reorganizados para ocupar seu espaço.</span><span class="sxs-lookup"><span data-stu-id="26ffe-196">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="26ffe-197">Hospedando um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="26ffe-197">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="26ffe-198">Alguns controles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm um tamanho fixo e não se alongam para preencher o espaço disponível no layout.</span><span class="sxs-lookup"><span data-stu-id="26ffe-198">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="26ffe-199">Por exemplo, o controle de <xref:System.Windows.Forms.MonthCalendar> exibe um mês em um espaço fixo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-199">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

<span data-ttu-id="26ffe-200">Para hospedar um controle que não se estende, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-200">To host a control that does not stretch, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-201">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-201">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="26ffe-202">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-202">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-203">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é centralizado na linha de grade, mas não é ampliado para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="26ffe-203">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="26ffe-204">Se a janela for grande o suficiente, você poderá ver dois ou mais meses exibidos pelo controle de <xref:System.Windows.Forms.MonthCalendar> hospedado, mas eles são centralizados na linha.</span><span class="sxs-lookup"><span data-stu-id="26ffe-204">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="26ffe-205">O mecanismo de layout de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] centraliza os elementos que não podem ser dimensionados para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="26ffe-205">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="26ffe-206">Dimensionamento</span><span class="sxs-lookup"><span data-stu-id="26ffe-206">Scaling</span></span>

<span data-ttu-id="26ffe-207">Ao contrário dos elementos do WPF, a maioria dos controles de Windows Forms não são continuamente escalonáveis.</span><span class="sxs-lookup"><span data-stu-id="26ffe-207">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="26ffe-208">Para fornecer o dimensionamento personalizado, você substitui o método <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-208">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="26ffe-209">Para dimensionar um controle hospedado usando o comportamento padrão, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-209">To scale a hosted control by using the default behavior, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-210">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-210">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="26ffe-211">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-211">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-212">O controle hospedado e seus elementos adjacentes são dimensionados por um fator de 0,5.</span><span class="sxs-lookup"><span data-stu-id="26ffe-212">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="26ffe-213">No entanto, a fonte do controle hospedada não é redimensionada.</span><span class="sxs-lookup"><span data-stu-id="26ffe-213">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="26ffe-214">Girando</span><span class="sxs-lookup"><span data-stu-id="26ffe-214">Rotating</span></span>

<span data-ttu-id="26ffe-215">Ao contrário dos elementos do WPF, os controles de Windows Forms não dão suporte à rotação.</span><span class="sxs-lookup"><span data-stu-id="26ffe-215">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="26ffe-216">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> não gira com outros elementos do WPF quando uma transformação de rotação é aplicada.</span><span class="sxs-lookup"><span data-stu-id="26ffe-216">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="26ffe-217">Qualquer valor de rotação diferente de 180 graus gera o evento <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-217">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

<span data-ttu-id="26ffe-218">Para ver o efeito de rotação em um aplicativo híbrido, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-218">To see the effect of rotation in a hybrid application, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-219">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-219">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="26ffe-220">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-220">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-221">O controle hospedado não é girado, mas seus elementos adjacentes são girados por um ângulo de 180 graus.</span><span class="sxs-lookup"><span data-stu-id="26ffe-221">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="26ffe-222">Você terá que redimensionar a janela para ver os elementos.</span><span class="sxs-lookup"><span data-stu-id="26ffe-222">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="26ffe-223">Margens e preenchimento de configuração</span><span class="sxs-lookup"><span data-stu-id="26ffe-223">Setting Padding and Margins</span></span>

<span data-ttu-id="26ffe-224">O preenchimento e as margens no layout de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são semelhantes ao preenchimento e às margens em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26ffe-224">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="26ffe-225">Basta definir as propriedades <xref:System.Windows.Controls.Control.Padding%2A> e <xref:System.Windows.FrameworkElement.Margin%2A> no elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-225">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

<span data-ttu-id="26ffe-226">Para definir o preenchimento e as margens de um controle hospedado, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-226">To set padding and margins for a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-227">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-227">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="26ffe-228">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-228">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-229">As configurações de preenchimento e margem são aplicadas aos controles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedados da mesma maneira que eles seriam aplicados em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26ffe-229">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="26ffe-230">Usando contêineres de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="26ffe-230">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="26ffe-231">fornece dois contêineres de layout dinâmico, <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="26ffe-231">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="26ffe-232">Você também pode usar esses contêineres em layouts de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26ffe-232">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

<span data-ttu-id="26ffe-233">Para usar um contêiner de layout dinâmico, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="26ffe-233">To use a dynamic layout container, follow these steps:</span></span>

1. <span data-ttu-id="26ffe-234">Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="26ffe-234">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="26ffe-235">Em *MainWindow. XAML. vb* ou *MainWindow.XAML.cs*, copie o seguinte código para a definição de classe:</span><span class="sxs-lookup"><span data-stu-id="26ffe-235">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="26ffe-236">Adicione uma chamada para o método `InitializeFlowLayoutPanel` no construtor:</span><span class="sxs-lookup"><span data-stu-id="26ffe-236">Add a call to the `InitializeFlowLayoutPanel` method in the constructor:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="26ffe-237">Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26ffe-237">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="26ffe-238">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> preenche a <xref:System.Windows.Controls.DockPanel>e <xref:System.Windows.Forms.FlowLayoutPanel> organiza seus controles filho no <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>padrão.</span><span class="sxs-lookup"><span data-stu-id="26ffe-238">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="26ffe-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26ffe-239">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="26ffe-240">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26ffe-240">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="26ffe-241">Considerações sobre o layout do elemento WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="26ffe-241">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="26ffe-242">Organizando Windows Forms controles no WPF de exemplo</span><span class="sxs-lookup"><span data-stu-id="26ffe-242">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="26ffe-243">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="26ffe-243">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="26ffe-244">Passo a passo: hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ffe-244">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
