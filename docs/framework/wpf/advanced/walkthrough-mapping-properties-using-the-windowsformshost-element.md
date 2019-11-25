---
title: 'Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: 94d175ec58f35b7e807786c221437d05c605c0bc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974221"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="391af-102">Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="391af-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="391af-103">Este passo a passos mostra como usar a propriedade <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> para mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Propriedades para propriedades correspondentes em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado.</span><span class="sxs-lookup"><span data-stu-id="391af-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="391af-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="391af-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="391af-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="391af-105">Creating the project.</span></span>

- <span data-ttu-id="391af-106">Definir o layout do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="391af-106">Defining the application layout.</span></span>

- <span data-ttu-id="391af-107">Definir um novo mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="391af-107">Defining a new property mapping.</span></span>

- <span data-ttu-id="391af-108">Remover um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="391af-108">Removing a default property mapping.</span></span>

- <span data-ttu-id="391af-109">Substituir um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="391af-109">Replacing a default property mapping.</span></span>

- <span data-ttu-id="391af-110">Estender um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="391af-110">Extending a default property mapping.</span></span>

<span data-ttu-id="391af-111">Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [mapeando propriedades usando o exemplo do elemento WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="391af-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="391af-112">Quando tiver terminado, você poderá mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Propriedades para as propriedades correspondentes em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado.</span><span class="sxs-lookup"><span data-stu-id="391af-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="391af-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="391af-113">Prerequisites</span></span>

<span data-ttu-id="391af-114">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="391af-114">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="391af-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="391af-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="391af-116">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="391af-116">Create and set up the project</span></span>

1. <span data-ttu-id="391af-117">Crie um projeto de **aplicativo do WPF** chamado `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="391af-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="391af-118">Em **Gerenciador de soluções**, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado de WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="391af-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="391af-119">Em **Gerenciador de soluções**, adicione referências aos assemblies System. Drawing e System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="391af-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="391af-120">Definindo o layout do aplicativo</span><span class="sxs-lookup"><span data-stu-id="391af-120">Defining the Application Layout</span></span>

<span data-ttu-id="391af-121">O aplicativo baseado em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]usa o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> para hospedar um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="391af-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="391af-122">Definir o layout do aplicativo</span><span class="sxs-lookup"><span data-stu-id="391af-122">To define the application layout</span></span>

1. <span data-ttu-id="391af-123">Abra o Window1. XAML no designer do WPF.</span><span class="sxs-lookup"><span data-stu-id="391af-123">Open Window1.xaml in the WPF Designer.</span></span>

2. <span data-ttu-id="391af-124">Substitua o código existente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="391af-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="391af-125">Abra Window1.xaml.cs no Editor de Código.</span><span class="sxs-lookup"><span data-stu-id="391af-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="391af-126">Na parte superior do arquivo, importe os seguintes namespaces.</span><span class="sxs-lookup"><span data-stu-id="391af-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="391af-127">Definindo um novo mapeamento de propriedade</span><span class="sxs-lookup"><span data-stu-id="391af-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="391af-128">O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> fornece vários mapeamentos de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="391af-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="391af-129">Você adiciona um novo mapeamento de propriedade chamando o método <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="391af-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="391af-130">Definir um novo mapeamento de propriedade</span><span class="sxs-lookup"><span data-stu-id="391af-130">To define a new property mapping</span></span>

- <span data-ttu-id="391af-131">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="391af-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="391af-132">O método `AddClipMapping` adiciona um novo mapeamento para a propriedade <xref:System.Windows.UIElement.Clip%2A>.</span><span class="sxs-lookup"><span data-stu-id="391af-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="391af-133">O método `OnClipChange` converte a propriedade <xref:System.Windows.UIElement.Clip%2A> para a propriedade [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>.</span><span class="sxs-lookup"><span data-stu-id="391af-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="391af-134">O método `Window1_SizeChanged` manipula o evento de <xref:System.Windows.FrameworkElement.SizeChanged> da janela e dimensiona a região de recorte para ajustá-la à janela do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="391af-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="391af-135">Removendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="391af-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="391af-136">Remova um mapeamento de propriedade padrão chamando o método <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="391af-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="391af-137">Remover um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="391af-137">To remove a default property mapping</span></span>

- <span data-ttu-id="391af-138">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="391af-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="391af-139">O método `RemoveCursorMapping` exclui o mapeamento padrão para a propriedade <xref:System.Windows.FrameworkElement.Cursor%2A>.</span><span class="sxs-lookup"><span data-stu-id="391af-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="391af-140">Substituindo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="391af-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="391af-141">Substitua um mapeamento de propriedade padrão removendo o mapeamento padrão e chamando o método <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="391af-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="391af-142">Substituir um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="391af-142">To replace a default property mapping</span></span>

- <span data-ttu-id="391af-143">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="391af-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="391af-144">O método `ReplaceFlowDirectionMapping` substitui o mapeamento padrão para a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="391af-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="391af-145">O método `OnFlowDirectionChange` converte a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A> para a propriedade [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>.</span><span class="sxs-lookup"><span data-stu-id="391af-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="391af-146">O método `cb_CheckedChanged` manipula o evento <xref:System.Windows.Forms.CheckBox.CheckedChanged> no controle de <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="391af-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="391af-147">Ele atribui a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A> com base no valor da propriedade <xref:System.Windows.Forms.CheckBox.CheckState%2A></span><span class="sxs-lookup"><span data-stu-id="391af-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="391af-148">Estendendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="391af-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="391af-149">Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.</span><span class="sxs-lookup"><span data-stu-id="391af-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="391af-150">Estender um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="391af-150">To extend a default property mapping</span></span>

- <span data-ttu-id="391af-151">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="391af-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="391af-152">O método `ExtendBackgroundMapping` adiciona um tradutor de propriedade personalizada ao mapeamento de propriedade <xref:System.Windows.Controls.Control.Background%2A> existente.</span><span class="sxs-lookup"><span data-stu-id="391af-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="391af-153">O método `OnBackgroundChange` atribui uma imagem específica à propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> do controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="391af-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="391af-154">O método `OnBackgroundChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.</span><span class="sxs-lookup"><span data-stu-id="391af-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="391af-155">Inicializando seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="391af-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="391af-156">Configure os mapeamentos de propriedade chamando os métodos descritos anteriormente no manipulador de eventos <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="391af-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="391af-157">Inicializar seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="391af-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="391af-158">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="391af-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="391af-159">O método `WindowLoaded` manipula o evento <xref:System.Windows.FrameworkElement.Loaded> e executa a inicialização a seguir.</span><span class="sxs-lookup"><span data-stu-id="391af-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    - <span data-ttu-id="391af-160">Cria um controle de <xref:System.Windows.Forms.CheckBox> de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="391af-160">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>

    - <span data-ttu-id="391af-161">Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="391af-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="391af-162">Atribui valores iniciais para as propriedades mapeadas.</span><span class="sxs-lookup"><span data-stu-id="391af-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="391af-163">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="391af-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="391af-164">Clique na caixa de seleção para ver o efeito do mapeamento de <xref:System.Windows.FrameworkElement.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="391af-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="391af-165">Ao clicar na caixa de seleção, o layout inverte sua orientação esquerda-direita.</span><span class="sxs-lookup"><span data-stu-id="391af-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="391af-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="391af-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="391af-167">Windows Forms e mapeamento de propriedade do WPF</span><span class="sxs-lookup"><span data-stu-id="391af-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="391af-168">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="391af-168">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="391af-169">Passo a passo: hospedando um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="391af-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
