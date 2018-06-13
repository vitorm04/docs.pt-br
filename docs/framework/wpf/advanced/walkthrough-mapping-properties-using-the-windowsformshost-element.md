---
title: 'Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: 771c0d972420b929ac757ced684de70d2dc7a58d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549296"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="5425e-102">Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="5425e-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>
<span data-ttu-id="5425e-103">Este passo a passo mostra como usar o <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> propriedade mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades às propriedades correspondentes em hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="5425e-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
 <span data-ttu-id="5425e-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="5425e-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="5425e-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="5425e-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="5425e-106">Definir o layout do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5425e-106">Defining the application layout.</span></span>  
  
-   <span data-ttu-id="5425e-107">Definir um novo mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-107">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="5425e-108">Remover um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="5425e-108">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="5425e-109">Substituir um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="5425e-109">Replacing a default property mapping.</span></span>  
  
-   <span data-ttu-id="5425e-110">Estender um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="5425e-110">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="5425e-111">Para uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [propriedades de mapeamento usando o exemplo de elemento WindowsFormsHost](http://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="5425e-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](http://go.microsoft.com/fwlink/?LinkID=160019).</span></span>  
  
 <span data-ttu-id="5425e-112">Quando você terminar, você poderá mapear [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades às propriedades correspondentes em hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="5425e-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5425e-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5425e-113">Prerequisites</span></span>  
 <span data-ttu-id="5425e-114">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="5425e-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="5425e-115">.</span><span class="sxs-lookup"><span data-stu-id="5425e-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="5425e-116">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="5425e-116">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="5425e-117">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="5425e-117">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="5425e-118">Crie um projeto de aplicativo WPF chamado `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="5425e-118">Create a WPF Application project named `PropertyMappingWithWfhSample`.</span></span>  
  
2.  <span data-ttu-id="5425e-119">No Gerenciador de Soluções, adicione uma referência ao assembly WindowsFormsIntegration, que é chamado de WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="5425e-119">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="5425e-120">No Gerenciador de soluções, adicione referências aos assemblies System. Drawing e System.</span><span class="sxs-lookup"><span data-stu-id="5425e-120">In Solution Explorer, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="defining-the-application-layout"></a><span data-ttu-id="5425e-121">Definindo o layout do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5425e-121">Defining the Application Layout</span></span>  
 <span data-ttu-id="5425e-122">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-com base em aplicativo usa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento host um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.</span><span class="sxs-lookup"><span data-stu-id="5425e-122">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-define-the-application-layout"></a><span data-ttu-id="5425e-123">Definir o layout do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5425e-123">To define the application layout</span></span>  
  
1.  <span data-ttu-id="5425e-124">Abra Window1 no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5425e-124">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="5425e-125">Substitua o código existente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5425e-125">Replace the existing code with the following code.</span></span>  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  <span data-ttu-id="5425e-126">Abra Window1.xaml.cs no Editor de Código.</span><span class="sxs-lookup"><span data-stu-id="5425e-126">Open Window1.xaml.cs in the Code Editor.</span></span>  
  
4.  <span data-ttu-id="5425e-127">Na parte superior do arquivo, importe os seguintes namespaces.</span><span class="sxs-lookup"><span data-stu-id="5425e-127">At the top of the file, import the following namespaces.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="5425e-128">Definindo um novo mapeamento de propriedade</span><span class="sxs-lookup"><span data-stu-id="5425e-128">Defining a New Property Mapping</span></span>  
 <span data-ttu-id="5425e-129">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento fornece vários propriedade mapeamentos padrão.</span><span class="sxs-lookup"><span data-stu-id="5425e-129">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="5425e-130">Você adiciona um novo mapeamento de propriedade chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método sobre o <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="5425e-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="5425e-131">Definir um novo mapeamento de propriedade</span><span class="sxs-lookup"><span data-stu-id="5425e-131">To define a new property mapping</span></span>  
  
-   <span data-ttu-id="5425e-132">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="5425e-132">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     <span data-ttu-id="5425e-133">O `AddClipMapping` método adiciona um novo mapeamento para o <xref:System.Windows.UIElement.Clip%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-133">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="5425e-134">O `OnClipChange` método converte o <xref:System.Windows.UIElement.Clip%2A> propriedade para o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-134">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="5425e-135">O `Window1_SizeChanged` método trata da janela <xref:System.Windows.FrameworkElement.SizeChanged> eventos e dimensiona a região de recorte para se ajustar à janela do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5425e-135">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="5425e-136">Removendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="5425e-136">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="5425e-137">Remover um mapeamento de propriedade padrão chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> método sobre o <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="5425e-137">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="5425e-138">Remover um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="5425e-138">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="5425e-139">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="5425e-139">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     <span data-ttu-id="5425e-140">O `RemoveCursorMapping` método exclui o mapeamento padrão para o <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-140">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>  
  
## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="5425e-141">Substituindo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="5425e-141">Replacing a Default Property Mapping</span></span>  
 <span data-ttu-id="5425e-142">Substituir um mapeamento de propriedade padrão, removendo o mapeamento padrão e chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método sobre o <xref:System.Windows.Forms.Integration.WindowsFormsHost> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="5425e-142">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="5425e-143">Substituir um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="5425e-143">To replace a default property mapping</span></span>  
  
-   <span data-ttu-id="5425e-144">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="5425e-144">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     <span data-ttu-id="5425e-145">O `ReplaceFlowDirectionMapping` método substitui o mapeamento padrão para o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-145">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>  
  
     <span data-ttu-id="5425e-146">O `OnFlowDirectionChange` método converte o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade para o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-146">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>  
  
     <span data-ttu-id="5425e-147">O `cb_CheckedChanged` método trata o <xref:System.Windows.Forms.CheckBox.CheckedChanged> evento no <xref:System.Windows.Forms.CheckBox> controle.</span><span class="sxs-lookup"><span data-stu-id="5425e-147">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="5425e-148">Ele atribui o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade com base no valor da <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade</span><span class="sxs-lookup"><span data-stu-id="5425e-148">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="5425e-149">Estendendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="5425e-149">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="5425e-150">Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.</span><span class="sxs-lookup"><span data-stu-id="5425e-150">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="5425e-151">Estender um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="5425e-151">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="5425e-152">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="5425e-152">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     <span data-ttu-id="5425e-153">O `ExtendBackgroundMapping` método adiciona um tradutor de propriedade personalizada para existente <xref:System.Windows.Controls.Control.Background%2A> mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-153">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>  
  
     <span data-ttu-id="5425e-154">O `OnBackgroundChange` método define uma imagem específica para o controle hospedado <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-154">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="5425e-155">O método `OnBackgroundChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.</span><span class="sxs-lookup"><span data-stu-id="5425e-155">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="5425e-156">Inicializando seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="5425e-156">Initializing Your Property Mappings</span></span>  
 <span data-ttu-id="5425e-157">Configurar seus mapeamentos de propriedades chamando os métodos descritos anteriormente no <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5425e-157">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="5425e-158">Inicializar seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="5425e-158">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="5425e-159">Copie o código a seguir para a definição da classe `Window1`.</span><span class="sxs-lookup"><span data-stu-id="5425e-159">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     <span data-ttu-id="5425e-160">O `WindowLoaded` método trata o <xref:System.Windows.FrameworkElement.Loaded> eventos e realiza a seguinte inicialização.</span><span class="sxs-lookup"><span data-stu-id="5425e-160">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="5425e-161">Cria um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> controle.</span><span class="sxs-lookup"><span data-stu-id="5425e-161">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>  
  
    -   <span data-ttu-id="5425e-162">Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="5425e-162">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="5425e-163">Atribui valores iniciais para as propriedades mapeadas.</span><span class="sxs-lookup"><span data-stu-id="5425e-163">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="5425e-164">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5425e-164">Press F5 to build and run the application.</span></span> <span data-ttu-id="5425e-165">Clique na caixa de seleção para ver o efeito do <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapeamento.</span><span class="sxs-lookup"><span data-stu-id="5425e-165">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="5425e-166">Ao clicar na caixa de seleção, o layout inverte sua orientação esquerda-direita.</span><span class="sxs-lookup"><span data-stu-id="5425e-166">When you click the check box, the layout reverses its left-right orientation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5425e-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5425e-167">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="5425e-168">Windows Forms e mapeamento de propriedade do WPF</span><span class="sxs-lookup"><span data-stu-id="5425e-168">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="5425e-169">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="5425e-169">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="5425e-170">Passo a passo: hospedando um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="5425e-170">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
