---
title: 'Instruções passo a passo: mapeando propriedades usando o controle ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 34119d889c8d6600fdda12cac33192c32d8e0fa6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467118"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="04492-102">Instruções passo a passo: mapeando propriedades usando o controle ElementHost</span><span class="sxs-lookup"><span data-stu-id="04492-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="04492-103">Este passo a passo mostra como usar o <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> propriedade para mapear [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriedades às propriedades correspondentes em um hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento.</span><span class="sxs-lookup"><span data-stu-id="04492-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="04492-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="04492-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="04492-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="04492-105">Creating the project.</span></span>

-   <span data-ttu-id="04492-106">Definir um novo mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-106">Defining a new property mapping.</span></span>

-   <span data-ttu-id="04492-107">Remover um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="04492-107">Removing a default property mapping.</span></span>

-   <span data-ttu-id="04492-108">Estender um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="04492-108">Extending a default property mapping.</span></span>

<span data-ttu-id="04492-109">Para ver uma listagem de código completa de todas tarefas ilustradas nesta instrução passo a passo, consulte [Mapeando propriedades usando o exemplo de controle ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="04492-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](https://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="04492-110">Quando você terminar, poderá mapear propriedades [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para as propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondentes em um elemento hospedado.</span><span class="sxs-lookup"><span data-stu-id="04492-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04492-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="04492-111">Prerequisites</span></span>

<span data-ttu-id="04492-112">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="04492-112">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="04492-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="04492-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="04492-114">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="04492-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="04492-115">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="04492-115">To create the project</span></span>

1.  <span data-ttu-id="04492-116">Criar uma **aplicativo do Windows Forms** projeto chamado `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="04492-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2.  <span data-ttu-id="04492-117">Na **Gerenciador de soluções**, adicione referências para os seguintes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span><span class="sxs-lookup"><span data-stu-id="04492-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    -   <span data-ttu-id="04492-118">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="04492-118">PresentationCore</span></span>

    -   <span data-ttu-id="04492-119">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="04492-119">PresentationFramework</span></span>

    -   <span data-ttu-id="04492-120">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="04492-120">WindowsBase</span></span>

    -   <span data-ttu-id="04492-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="04492-121">WindowsFormsIntegration</span></span>

3.  <span data-ttu-id="04492-122">Copie o seguinte código na parte superior do arquivo de código `Form1`.</span><span class="sxs-lookup"><span data-stu-id="04492-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4.  <span data-ttu-id="04492-123">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="04492-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="04492-124">Clique duas vezes no formulário para adicionar um manipulador de eventos para o <xref:System.Windows.Forms.Form.Load> eventos.</span><span class="sxs-lookup"><span data-stu-id="04492-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5.  <span data-ttu-id="04492-125">Retorne ao Designer de formulários do Windows e adicionar um manipulador de eventos para o formulário <xref:System.Windows.Forms.Control.Resize> eventos.</span><span class="sxs-lookup"><span data-stu-id="04492-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="04492-126">Para obter mais informações, consulte [Como criar manipuladores de eventos usando o Designer](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span><span class="sxs-lookup"><span data-stu-id="04492-126">For more information, see [How to: Create Event Handlers Using the Designer](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>

6.  <span data-ttu-id="04492-127">Declarar uma <xref:System.Windows.Forms.Integration.ElementHost> campo o `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="04492-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="04492-128">Definindo novos mapeamentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="04492-128">Defining New Property Mappings</span></span>

<span data-ttu-id="04492-129">O <xref:System.Windows.Forms.Integration.ElementHost> controle fornece vários padrão mapeamentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="04492-130">Adicionar um novo mapeamento de propriedade chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método em de <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="04492-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="04492-131">Definir novos mapeamentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="04492-131">To define new property mappings</span></span>

1.  <span data-ttu-id="04492-132">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="04492-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="04492-133">O `AddMarginMapping` método adiciona um novo mapeamento para o <xref:System.Windows.Forms.Control.Margin%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="04492-134">O `OnMarginChange` método traduz a <xref:System.Windows.Forms.Control.Margin%2A> propriedade para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2.  <span data-ttu-id="04492-135">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="04492-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="04492-136">O `AddRegionMapping` método adiciona um novo mapeamento para o <xref:System.Windows.Forms.Control.Region%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="04492-137">O `OnRegionChange` método traduz a <xref:System.Windows.Forms.Control.Region%2A> propriedade para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="04492-138">O `Form1_Resize` método lida com o formulário <xref:System.Windows.Forms.Control.Resize> eventos e dimensiona a região de recorte para caber no elemento hospedado.</span><span class="sxs-lookup"><span data-stu-id="04492-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="04492-139">Removendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="04492-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="04492-140">Remover um mapeamento de propriedade padrão chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> método em de <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="04492-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="04492-141">Remover um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="04492-141">To remove a default property mapping</span></span>

-   <span data-ttu-id="04492-142">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="04492-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="04492-143">O `RemoveCursorMapping` método exclui o mapeamento padrão para o <xref:System.Windows.Forms.Control.Cursor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="04492-144">Estendendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="04492-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="04492-145">Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.</span><span class="sxs-lookup"><span data-stu-id="04492-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="04492-146">Estender um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="04492-146">To extend a default property mapping</span></span>

-   <span data-ttu-id="04492-147">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="04492-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="04492-148">O `ExtendBackColorMapping` método adiciona um tradutor de propriedade personalizada para existente <xref:System.Windows.Forms.Control.BackColor%2A> mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="04492-149">O `OnBackColorChange` método atribui uma imagem específica para o controle hospedado <xref:System.Windows.Controls.Control.Background%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="04492-150">O método `OnBackColorChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.</span><span class="sxs-lookup"><span data-stu-id="04492-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="04492-151">Inicializar seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="04492-151">Initialize your property mappings</span></span>

1.  <span data-ttu-id="04492-152">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="04492-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="04492-153">O `Form1_Load` identificadores de método a <xref:System.Windows.Forms.Form.Load> eventos e realiza a seguinte inicialização.</span><span class="sxs-lookup"><span data-stu-id="04492-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    -   <span data-ttu-id="04492-154">Cria uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elemento.</span><span class="sxs-lookup"><span data-stu-id="04492-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    -   <span data-ttu-id="04492-155">Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04492-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    -   <span data-ttu-id="04492-156">Atribui valores iniciais para as propriedades mapeadas.</span><span class="sxs-lookup"><span data-stu-id="04492-156">Assigns initial values to the mapped properties.</span></span>

2.  <span data-ttu-id="04492-157">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04492-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="04492-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04492-158">See Also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="04492-159">Windows Forms e mapeamento de propriedade do WPF</span><span class="sxs-lookup"><span data-stu-id="04492-159">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="04492-160">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="04492-160">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="04492-161">Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04492-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)