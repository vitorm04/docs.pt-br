---
title: 'Passo a passo: mapear propriedades usando o elemento WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: edd9d6f698ba27cacb5e9a5eecab43f58d47b8e1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296518"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="de043-102">Passo a passo: mapear propriedades usando o elemento WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="de043-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="de043-103">Este passo a passo mostra como usar o <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> propriedade para mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades às propriedades correspondentes em um hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="de043-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="de043-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="de043-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="de043-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="de043-105">Creating the project.</span></span>

-   <span data-ttu-id="de043-106">Definir o layout do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de043-106">Defining the application layout.</span></span>

-   <span data-ttu-id="de043-107">Definir um novo mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-107">Defining a new property mapping.</span></span>

-   <span data-ttu-id="de043-108">Remover um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="de043-108">Removing a default property mapping.</span></span>

-   <span data-ttu-id="de043-109">Substituir um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="de043-109">Replacing a default property mapping.</span></span>

-   <span data-ttu-id="de043-110">Estender um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="de043-110">Extending a default property mapping.</span></span>

<span data-ttu-id="de043-111">Para obter uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [mapeando propriedades usando o exemplo de elemento WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="de043-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="de043-112">Quando tiver terminado, você será capaz de mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades às propriedades correspondentes em um hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="de043-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="de043-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="de043-113">Prerequisites</span></span>

<span data-ttu-id="de043-114">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="de043-114">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="de043-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="de043-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="de043-116">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="de043-116">Create and set up the project</span></span>

1. <span data-ttu-id="de043-117">Criar uma **aplicativo WPF** projeto chamado `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="de043-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="de043-118">Na **Gerenciador de soluções**, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.</span><span class="sxs-lookup"><span data-stu-id="de043-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="de043-119">Na **Gerenciador de soluções**, adicione referências aos assemblies System. Drawing e System.</span><span class="sxs-lookup"><span data-stu-id="de043-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="de043-120">Definindo o layout do aplicativo</span><span class="sxs-lookup"><span data-stu-id="de043-120">Defining the Application Layout</span></span>

<span data-ttu-id="de043-121">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-com base em aplicativo usa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento host um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="de043-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="de043-122">Definir o layout do aplicativo</span><span class="sxs-lookup"><span data-stu-id="de043-122">To define the application layout</span></span>

1. <span data-ttu-id="de043-123">Abra Window1.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de043-123">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2. <span data-ttu-id="de043-124">Substitua o código existente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="de043-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="de043-125">Abra Window1.xaml.cs no Editor de Código.</span><span class="sxs-lookup"><span data-stu-id="de043-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="de043-126">Na parte superior do arquivo, importe os seguintes namespaces.</span><span class="sxs-lookup"><span data-stu-id="de043-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="de043-127">Definindo um novo mapeamento de propriedade</span><span class="sxs-lookup"><span data-stu-id="de043-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="de043-128">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento fornece o padrão de vários mapeamentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="de043-129">Adicionar um novo mapeamento de propriedade chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método em de <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="de043-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="de043-130">Definir um novo mapeamento de propriedade</span><span class="sxs-lookup"><span data-stu-id="de043-130">To define a new property mapping</span></span>

-   <span data-ttu-id="de043-131">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="de043-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="de043-132">O `AddClipMapping` método adiciona um novo mapeamento para o <xref:System.Windows.UIElement.Clip%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="de043-133">O `OnClipChange` método traduz a <xref:System.Windows.UIElement.Clip%2A> propriedade para o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="de043-134">O `Window1_SizeChanged` método lida com a janela <xref:System.Windows.FrameworkElement.SizeChanged> eventos e dimensiona a região de recorte para caber na janela do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de043-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="de043-135">Removendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="de043-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="de043-136">Remover um mapeamento de propriedade padrão chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> método em de <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="de043-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="de043-137">Remover um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="de043-137">To remove a default property mapping</span></span>

-   <span data-ttu-id="de043-138">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="de043-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="de043-139">O `RemoveCursorMapping` método exclui o mapeamento padrão para o <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="de043-140">Substituindo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="de043-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="de043-141">Substituir um mapeamento de propriedade padrão removendo o mapeamento padrão e chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método em de <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="de043-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="de043-142">Substituir um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="de043-142">To replace a default property mapping</span></span>

-   <span data-ttu-id="de043-143">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="de043-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="de043-144">O `ReplaceFlowDirectionMapping` método substitui o mapeamento padrão para o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="de043-145">O `OnFlowDirectionChange` método traduz a <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade para o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="de043-146">O `cb_CheckedChanged` identificadores de método de <xref:System.Windows.Forms.CheckBox.CheckedChanged> evento no <xref:System.Windows.Forms.CheckBox> controle.</span><span class="sxs-lookup"><span data-stu-id="de043-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="de043-147">Ele atribui a <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade com base no valor da <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade</span><span class="sxs-lookup"><span data-stu-id="de043-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="de043-148">Estendendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="de043-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="de043-149">Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.</span><span class="sxs-lookup"><span data-stu-id="de043-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="de043-150">Estender um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="de043-150">To extend a default property mapping</span></span>

-   <span data-ttu-id="de043-151">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="de043-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="de043-152">O `ExtendBackgroundMapping` método adiciona um tradutor de propriedade personalizada para existente <xref:System.Windows.Controls.Control.Background%2A> mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="de043-153">O `OnBackgroundChange` método atribui uma imagem específica para o controle hospedado <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="de043-154">O método `OnBackgroundChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.</span><span class="sxs-lookup"><span data-stu-id="de043-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="de043-155">Inicializando seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="de043-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="de043-156">Configure seus mapeamentos de propriedades chamando os métodos descritos anteriormente no <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="de043-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="de043-157">Inicializar seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="de043-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="de043-158">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="de043-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="de043-159">O `WindowLoaded` identificadores de método a <xref:System.Windows.FrameworkElement.Loaded> eventos e realiza a seguinte inicialização.</span><span class="sxs-lookup"><span data-stu-id="de043-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    -   <span data-ttu-id="de043-160">Cria um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> controle.</span><span class="sxs-lookup"><span data-stu-id="de043-160">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>

    -   <span data-ttu-id="de043-161">Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="de043-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    -   <span data-ttu-id="de043-162">Atribui valores iniciais para as propriedades mapeadas.</span><span class="sxs-lookup"><span data-stu-id="de043-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="de043-163">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de043-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="de043-164">Clique na caixa de seleção para ver o efeito do <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapeamento.</span><span class="sxs-lookup"><span data-stu-id="de043-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="de043-165">Ao clicar na caixa de seleção, o layout inverte sua orientação esquerda-direita.</span><span class="sxs-lookup"><span data-stu-id="de043-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="de043-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de043-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="de043-167">Windows Forms e mapeamento de propriedade do WPF</span><span class="sxs-lookup"><span data-stu-id="de043-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="de043-168">Criar XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="de043-168">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="de043-169">Passo a passo: hospedar um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="de043-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)