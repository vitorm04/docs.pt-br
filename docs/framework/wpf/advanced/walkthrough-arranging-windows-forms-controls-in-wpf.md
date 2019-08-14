---
title: 'Passo a passo: organizar controles do Windows Forms no WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972302"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="74426-102">Passo a passo: organizar controles do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="74426-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="74426-103">Este tutorial mostra como usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os recursos de layout para organizar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles em um aplicativo híbrido.</span><span class="sxs-lookup"><span data-stu-id="74426-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="74426-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="74426-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="74426-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="74426-105">Creating the project.</span></span>

- <span data-ttu-id="74426-106">Usando as configurações padrão de layout.</span><span class="sxs-lookup"><span data-stu-id="74426-106">Using default layout settings.</span></span>

- <span data-ttu-id="74426-107">Dimensionando o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="74426-107">Sizing to content.</span></span>

- <span data-ttu-id="74426-108">Usando o posicionamento absoluto.</span><span class="sxs-lookup"><span data-stu-id="74426-108">Using absolute positioning.</span></span>

- <span data-ttu-id="74426-109">Especificando o tamanho explicitamente.</span><span class="sxs-lookup"><span data-stu-id="74426-109">Specifying size explicitly.</span></span>

- <span data-ttu-id="74426-110">Definindo propriedades de layout.</span><span class="sxs-lookup"><span data-stu-id="74426-110">Setting layout properties.</span></span>

- <span data-ttu-id="74426-111">Noções básicas sobre limitações da ordem z.</span><span class="sxs-lookup"><span data-stu-id="74426-111">Understanding z-order limitations.</span></span>

- <span data-ttu-id="74426-112">Encaixe.</span><span class="sxs-lookup"><span data-stu-id="74426-112">Docking.</span></span>

- <span data-ttu-id="74426-113">Definindo a visibilidade.</span><span class="sxs-lookup"><span data-stu-id="74426-113">Setting visibility.</span></span>

- <span data-ttu-id="74426-114">Hospedando um controle que não se alonga.</span><span class="sxs-lookup"><span data-stu-id="74426-114">Hosting a control that does not stretch.</span></span>

- <span data-ttu-id="74426-115">Dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="74426-115">Scaling.</span></span>

- <span data-ttu-id="74426-116">Girando.</span><span class="sxs-lookup"><span data-stu-id="74426-116">Rotating.</span></span>

- <span data-ttu-id="74426-117">Margens e preenchimento de configuração.</span><span class="sxs-lookup"><span data-stu-id="74426-117">Setting padding and margins.</span></span>

- <span data-ttu-id="74426-118">Usando contêineres de layout dinâmico.</span><span class="sxs-lookup"><span data-stu-id="74426-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="74426-119">Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [organizando Windows Forms controles no WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="74426-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="74426-120">Quando terminar, você terá uma compreensão dos recursos de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout em aplicativos baseados na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]base.</span><span class="sxs-lookup"><span data-stu-id="74426-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74426-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="74426-121">Prerequisites</span></span>

<span data-ttu-id="74426-122">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="74426-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="74426-123">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="74426-123">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="74426-124">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="74426-124">To create and set up the project</span></span>

1. <span data-ttu-id="74426-125">Crie um projeto de aplicativo WPF chamado `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="74426-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="74426-126">No Gerenciador de Soluções, adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="74426-126">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="74426-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="74426-127">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="74426-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="74426-128">System.Windows.Forms</span></span>

    - <span data-ttu-id="74426-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="74426-129">System.Drawing</span></span>

3. <span data-ttu-id="74426-130">Clique duas vezes em MainWindow.xaml para abri-lo no modo de exibição XAML.</span><span class="sxs-lookup"><span data-stu-id="74426-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>

4. <span data-ttu-id="74426-131">No elemento, adicione o mapeamento de namespace a seguir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. <xref:System.Windows.Window></span><span class="sxs-lookup"><span data-stu-id="74426-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="74426-132">No elemento, defina a <xref:System.Windows.Controls.Grid.ShowGridLines%2A> Propriedade como `true` e defina cinco linhas e três colunas. <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="74426-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="74426-133">Usando as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="74426-133">Using Default Layout Settings</span></span>

<span data-ttu-id="74426-134">Por padrão, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento manipula o layout para o controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado.</span><span class="sxs-lookup"><span data-stu-id="74426-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-use-default-layout-settings"></a><span data-ttu-id="74426-135">Para usar as configurações padrão de layout</span><span class="sxs-lookup"><span data-stu-id="74426-135">To use default layout settings</span></span>

1. <span data-ttu-id="74426-136">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="74426-137">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-138">O [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Controls.Canvas>controle apareceno.<xref:System.Windows.Forms.Button?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="74426-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="74426-139">O controle hospedado é dimensionado com base em seu conteúdo e o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é dimensionado para acomodar o controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="74426-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="74426-140">Dimensionando para o conteúdo</span><span class="sxs-lookup"><span data-stu-id="74426-140">Sizing to Content</span></span>

<span data-ttu-id="74426-141">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento garante que o controle hospedado seja dimensionado para exibir seu conteúdo corretamente.</span><span class="sxs-lookup"><span data-stu-id="74426-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

### <a name="to-size-to-content"></a><span data-ttu-id="74426-142">Para dimensionar para o Conteúdo</span><span class="sxs-lookup"><span data-stu-id="74426-142">To size to content</span></span>

1. <span data-ttu-id="74426-143">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="74426-144">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-145">Os dois novos controles de botão são dimensionados para exibir a cadeia de caracteres de texto mais longa e o <xref:System.Windows.Forms.Integration.WindowsFormsHost> tamanho de fonte maior corretamente, e os elementos são redimensionados para acomodar os controles hospedados.</span><span class="sxs-lookup"><span data-stu-id="74426-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="74426-146">Usando o posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="74426-146">Using Absolute Positioning</span></span>

<span data-ttu-id="74426-147">Você pode usar o posicionamento absoluto para posicionar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento em qualquer lugar na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="74426-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

### <a name="to-use-absolute-positioning"></a><span data-ttu-id="74426-148">Para usar posicionamento absoluto</span><span class="sxs-lookup"><span data-stu-id="74426-148">To use absolute positioning</span></span>

1. <span data-ttu-id="74426-149">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="74426-150">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-151">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é colocado em 20 pixels do lado superior da célula de grade e 20 pixels à esquerda.</span><span class="sxs-lookup"><span data-stu-id="74426-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="74426-152">Especificando o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="74426-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="74426-153">Você pode especificar o tamanho do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento usando as <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="74426-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

### <a name="to-specify-size-explicitly"></a><span data-ttu-id="74426-154">Para especificar o tamanho explicitamente</span><span class="sxs-lookup"><span data-stu-id="74426-154">To specify size explicitly</span></span>

1. <span data-ttu-id="74426-155">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="74426-156">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-157">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é definido com um tamanho de 50 pixels de largura por 70 pixels de altura, que é menor do que as configurações de layout padrão.</span><span class="sxs-lookup"><span data-stu-id="74426-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="74426-158">O conteúdo do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é reorganizado de acordo.</span><span class="sxs-lookup"><span data-stu-id="74426-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="74426-159">Definindo propriedades de layout</span><span class="sxs-lookup"><span data-stu-id="74426-159">Setting Layout Properties</span></span>

<span data-ttu-id="74426-160">Sempre defina propriedades relacionadas ao layout no controle hospedado usando as propriedades do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="74426-161">Definindo propriedades de layout diretamente no controle hospedado produzirá resultados indesejados.</span><span class="sxs-lookup"><span data-stu-id="74426-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="74426-162">Definir propriedades relacionadas a layout no controle hospedado no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="74426-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="74426-163">Para ver os efeitos da definição das propriedades no controle hospedado</span><span class="sxs-lookup"><span data-stu-id="74426-163">To see the effects of setting properties on the hosted control</span></span>

1. <span data-ttu-id="74426-164">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="74426-165">No Gerenciador de Soluções, clique duas vezes em MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="74426-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="74426-166">Abrir vb ou MainWindow.xaml.cs no Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="74426-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>

3. <span data-ttu-id="74426-167">Copie o código a seguir na `MainWindow` definição de classe.</span><span class="sxs-lookup"><span data-stu-id="74426-167">Copy the following code into the `MainWindow` class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="74426-168">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-168">Press F5 to build and run the application.</span></span>

5. <span data-ttu-id="74426-169">Clique no botão **clicar em mim** .</span><span class="sxs-lookup"><span data-stu-id="74426-169">Click the **Click me** button.</span></span> <span data-ttu-id="74426-170">O `button1_Click` manipulador de eventos define <xref:System.Windows.Forms.Control.Top%2A> as <xref:System.Windows.Forms.Control.Left%2A> Propriedades e no controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="74426-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="74426-171">Isso faz com que o controle hospedado seja reposicionado dentro <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="74426-172">O host mantém a mesma área da tela, mas o controle hospedado é cortado.</span><span class="sxs-lookup"><span data-stu-id="74426-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="74426-173">Em vez disso, o controle hospedado sempre deve <xref:System.Windows.Forms.Integration.WindowsFormsHost> preencher o elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="74426-174">Noções básicas sobre limitações da ordem z</span><span class="sxs-lookup"><span data-stu-id="74426-174">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="74426-175">Os <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos visíveis sempre são desenhados sobre outros elementos do WPF e não são afetados pela ordem z.</span><span class="sxs-lookup"><span data-stu-id="74426-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="74426-176">Para ver esse comportamento de ordem z, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="74426-176">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="74426-177">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="74426-178">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-179">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é pintado sobre o elemento Label.</span><span class="sxs-lookup"><span data-stu-id="74426-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="74426-180">Encaixe</span><span class="sxs-lookup"><span data-stu-id="74426-180">Docking</span></span>

<span data-ttu-id="74426-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost>o elemento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece suporte a encaixe.</span><span class="sxs-lookup"><span data-stu-id="74426-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="74426-182">Defina a <xref:System.Windows.Controls.DockPanel.Dock%2A> Propriedade anexada para encaixar o controle <xref:System.Windows.Controls.DockPanel> hospedado em um elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="74426-183">Para encaixar o controle hospedado</span><span class="sxs-lookup"><span data-stu-id="74426-183">To dock a hosted control</span></span>

1. <span data-ttu-id="74426-184">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="74426-185">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-186">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é encaixado no lado direito <xref:System.Windows.Controls.DockPanel> do elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="74426-187">Definindo a visibilidade</span><span class="sxs-lookup"><span data-stu-id="74426-187">Setting Visibility</span></span>

<span data-ttu-id="74426-188">Você pode tornar seu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle invisível ou recolhê-lo definindo <xref:System.Windows.UIElement.Visibility%2A> a propriedade no <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="74426-189">Quando um controle estiver invisível, ele não será exibido, mas ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="74426-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="74426-190">Quando um controle estiver recolhido, ele não será exibido, mas também não ocupa espaço de layout.</span><span class="sxs-lookup"><span data-stu-id="74426-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="74426-191">Para definir a visibilidade de um controle hospedado</span><span class="sxs-lookup"><span data-stu-id="74426-191">To set the visibility of a hosted control</span></span>

1. <span data-ttu-id="74426-192">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="74426-193">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, copie o código a seguir para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="74426-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="74426-194">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-194">Press F5 to build and run the application.</span></span>

4. <span data-ttu-id="74426-195">Clique no botão **clique para tornar invisível** para tornar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento invisível.</span><span class="sxs-lookup"><span data-stu-id="74426-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="74426-196">Clique no botão **clique para recolher** para ocultar totalmente <xref:System.Windows.Forms.Integration.WindowsFormsHost> o elemento do layout.</span><span class="sxs-lookup"><span data-stu-id="74426-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="74426-197">Quando o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle é recolhido, os elementos circundantes são reorganizados para ocupar seu espaço.</span><span class="sxs-lookup"><span data-stu-id="74426-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="74426-198">Hospedando um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="74426-198">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="74426-199">Alguns [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles têm um tamanho fixo e não se alongam para preencher o espaço disponível no layout.</span><span class="sxs-lookup"><span data-stu-id="74426-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="74426-200">Por exemplo, o <xref:System.Windows.Forms.MonthCalendar> controle exibe um mês em um espaço fixo.</span><span class="sxs-lookup"><span data-stu-id="74426-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="74426-201">Para hospedar um controle que não se alonga</span><span class="sxs-lookup"><span data-stu-id="74426-201">To host a control that does not stretch</span></span>

1. <span data-ttu-id="74426-202">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="74426-203">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-204">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento é centralizado na linha de grade, mas não é ampliado para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="74426-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="74426-205">Se a janela for grande o suficiente, você poderá ver dois ou mais meses exibidos pelo controle <xref:System.Windows.Forms.MonthCalendar> hospedado, mas eles são centralizados na linha.</span><span class="sxs-lookup"><span data-stu-id="74426-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="74426-206">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de layout centraliza os elementos que não podem ser dimensionados para preencher o espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="74426-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="74426-207">Dimensionamento</span><span class="sxs-lookup"><span data-stu-id="74426-207">Scaling</span></span>

<span data-ttu-id="74426-208">Ao contrário dos elementos do WPF, a maioria dos controles de Windows Forms não são continuamente escalonáveis.</span><span class="sxs-lookup"><span data-stu-id="74426-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="74426-209">Para fornecer o dimensionamento personalizado, você <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> substitui o método.</span><span class="sxs-lookup"><span data-stu-id="74426-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="74426-210">Para dimensionar um controle hospedado usando o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="74426-210">To scale a hosted control by using the default behavior</span></span>

1. <span data-ttu-id="74426-211">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="74426-212">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-213">O controle hospedado e seus elementos adjacentes são dimensionados por um fator de 0,5.</span><span class="sxs-lookup"><span data-stu-id="74426-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="74426-214">No entanto, a fonte do controle hospedada não é redimensionada.</span><span class="sxs-lookup"><span data-stu-id="74426-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="74426-215">Girando</span><span class="sxs-lookup"><span data-stu-id="74426-215">Rotating</span></span>

<span data-ttu-id="74426-216">Ao contrário dos elementos do WPF, os controles de Windows Forms não dão suporte à rotação.</span><span class="sxs-lookup"><span data-stu-id="74426-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="74426-217">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento não gira com outros elementos do WPF quando uma transformação de rotação é aplicada.</span><span class="sxs-lookup"><span data-stu-id="74426-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="74426-218">Qualquer valor de rotação diferente de 180 graus gera <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> o evento.</span><span class="sxs-lookup"><span data-stu-id="74426-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="74426-219">Para ver o efeito de rotação em um aplicativo híbrido</span><span class="sxs-lookup"><span data-stu-id="74426-219">To see the effect of rotation in a hybrid application</span></span>

1. <span data-ttu-id="74426-220">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="74426-221">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-222">O controle hospedado não é girado, mas seus elementos adjacentes são girados por um ângulo de 180 graus.</span><span class="sxs-lookup"><span data-stu-id="74426-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="74426-223">Você terá que redimensionar a janela para ver os elementos.</span><span class="sxs-lookup"><span data-stu-id="74426-223">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="74426-224">Margens e preenchimento de configuração</span><span class="sxs-lookup"><span data-stu-id="74426-224">Setting Padding and Margins</span></span>

<span data-ttu-id="74426-225">O preenchimento e as margens [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no layout são semelhantes ao preenchimento e às margens [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]no.</span><span class="sxs-lookup"><span data-stu-id="74426-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="74426-226">Basta definir as <xref:System.Windows.Controls.Control.Padding%2A> propriedades <xref:System.Windows.FrameworkElement.Margin%2A> e no <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="74426-227">Para definir o preenchimento e margens de um controle hospedado</span><span class="sxs-lookup"><span data-stu-id="74426-227">To set padding and margins for a hosted control</span></span>

1. <span data-ttu-id="74426-228">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="74426-229">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-230">As configurações de preenchimento e margem são aplicadas aos controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedados da mesma maneira como eles seriam [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]aplicados.</span><span class="sxs-lookup"><span data-stu-id="74426-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="74426-231">Usando contêineres de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="74426-231">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="74426-232">fornece dois contêineres de <xref:System.Windows.Forms.FlowLayoutPanel> layout dinâmico e. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="74426-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="74426-233">Você também pode usar esses contêineres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em layouts.</span><span class="sxs-lookup"><span data-stu-id="74426-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="74426-234">Para usar um contêiner de layout dinâmico</span><span class="sxs-lookup"><span data-stu-id="74426-234">To use a dynamic layout container</span></span>

1. <span data-ttu-id="74426-235">Copie o XAML a seguir no <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="74426-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="74426-236">Em MainWindow.xaml.vb ou MainWindow.xaml.cs, copie o código a seguir para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="74426-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="74426-237">Adicione uma chamada para o `InitializeFlowLayoutPanel` método no construtor.</span><span class="sxs-lookup"><span data-stu-id="74426-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="74426-238">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74426-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="74426-239">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento preenche o <xref:System.Windows.Controls.DockPanel>e <xref:System.Windows.Forms.FlowLayoutPanel> organiza seus controles filho no padrão <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="74426-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="74426-240">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74426-240">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="74426-241">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="74426-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="74426-242">Considerações sobre o layout do elemento WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="74426-242">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="74426-243">Organizando Windows Forms controles no WPF de exemplo</span><span class="sxs-lookup"><span data-stu-id="74426-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="74426-244">Passo a passo: Hospedando um controle composto Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="74426-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="74426-245">Passo a passo: Hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74426-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
