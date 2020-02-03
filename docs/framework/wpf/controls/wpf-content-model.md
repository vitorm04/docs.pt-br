---
title: Modelo de conteúdo
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738275"
---
# <a name="wpf-content-model"></a><span data-ttu-id="25d03-102">Modelo de conteúdo do WPF</span><span class="sxs-lookup"><span data-stu-id="25d03-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="25d03-103">é uma plataforma de apresentação que fornece muitos controles e tipos de controle cujo objetivo principal é exibir diferentes tipos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="25d03-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="25d03-104">Para determinar qual controle usar ou de qual controle derivar, você deve compreender os tipos de objetos que um controle específico pode exibir.</span><span class="sxs-lookup"><span data-stu-id="25d03-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="25d03-105">Este tópico resume o modelo de conteúdo para os controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o tipos semelhantes a controle.</span><span class="sxs-lookup"><span data-stu-id="25d03-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="25d03-106">O modelo de conteúdo descreve qual conteúdo pode ser usado em um controle.</span><span class="sxs-lookup"><span data-stu-id="25d03-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="25d03-107">Este tópico também lista as propriedades de conteúdo para cada modelo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="25d03-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="25d03-108">Uma propriedade de conteúdo é uma propriedade que é usada para armazenar o conteúdo do objeto.</span><span class="sxs-lookup"><span data-stu-id="25d03-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="25d03-109">Classes que Contêm Conteúdo Arbitrário</span><span class="sxs-lookup"><span data-stu-id="25d03-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="25d03-110">Alguns controles podem conter um objeto de qualquer tipo, como uma cadeia de caracteres, um objeto <xref:System.DateTime> ou um <xref:System.Windows.UIElement> que seja um contêiner para itens adicionais.</span><span class="sxs-lookup"><span data-stu-id="25d03-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="25d03-111">Por exemplo, um <xref:System.Windows.Controls.Button> pode conter uma imagem e algum texto; ou um <xref:System.Windows.Controls.CheckBox> pode conter o valor de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25d03-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="25d03-112">tem quatro classes que podem conter conteúdo arbitrário.</span><span class="sxs-lookup"><span data-stu-id="25d03-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="25d03-113">A tabela a seguir lista as classes, que herdam de <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="25d03-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="25d03-114">Classes que contêm conteúdo arbitrário</span><span class="sxs-lookup"><span data-stu-id="25d03-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="25d03-115">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="25d03-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="25d03-116">Um único objeto arbitrário.</span><span class="sxs-lookup"><span data-stu-id="25d03-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="25d03-117">Um cabeçalho e um único item, que são objetos arbitrários.</span><span class="sxs-lookup"><span data-stu-id="25d03-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="25d03-118">Uma coleção de objetos arbitrários.</span><span class="sxs-lookup"><span data-stu-id="25d03-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="25d03-119">Um cabeçalho e uma coleção de itens, que são objetos arbitrários.</span><span class="sxs-lookup"><span data-stu-id="25d03-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="25d03-120">Os controles que herdam essas classes podem conter o mesmo tipo de conteúdo e tratar o conteúdo da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="25d03-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="25d03-121">A ilustração a seguir mostra um controle de cada modelo de conteúdo que contém uma imagem e algum texto:</span><span class="sxs-lookup"><span data-stu-id="25d03-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Captura de tela que mostra quatro controles diferentes, um de cada modelo de conteúdo.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="25d03-123">Controles que contêm um único objeto arbitrário</span><span class="sxs-lookup"><span data-stu-id="25d03-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="25d03-124">A classe <xref:System.Windows.Controls.ContentControl> contém uma única parte do conteúdo arbitrário.</span><span class="sxs-lookup"><span data-stu-id="25d03-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="25d03-125">Sua propriedade de conteúdo é <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="25d03-126">Os seguintes controles herdam de <xref:System.Windows.Controls.ContentControl> e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="25d03-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 <span data-ttu-id="25d03-127">A ilustração a seguir mostra quatro botões cujo <xref:System.Windows.Controls.ContentControl.Content%2A> está definido como uma cadeia de caracteres, um objeto <xref:System.DateTime>, um <xref:System.Windows.Shapes.Rectangle>e um <xref:System.Windows.Controls.Panel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>:</span><span class="sxs-lookup"><span data-stu-id="25d03-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Captura de tela que mostra quatro botões com tipos de conteúdo diferentes.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="25d03-129">Para obter um exemplo de como definir a propriedade <xref:System.Windows.Controls.ContentControl.Content%2A>, consulte <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="25d03-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="25d03-130">Controles que contêm um único objeto arbitrário e um cabeçalho</span><span class="sxs-lookup"><span data-stu-id="25d03-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="25d03-131">A classe <xref:System.Windows.Controls.HeaderedContentControl> herda de <xref:System.Windows.Controls.ContentControl> e exibe o conteúdo com um cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="25d03-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="25d03-132">Ele herda a propriedade Content, <xref:System.Windows.Controls.ContentControl.Content%2A>, de <xref:System.Windows.Controls.ContentControl> e define a propriedade <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> que é do tipo <xref:System.Object>; Portanto, ambos podem ser um objeto arbitrário.</span><span class="sxs-lookup"><span data-stu-id="25d03-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="25d03-133">Os seguintes controles herdam de <xref:System.Windows.Controls.HeaderedContentControl> e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="25d03-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="25d03-134">A ilustração a seguir mostra dois objetos <xref:System.Windows.Controls.TabItem>.</span><span class="sxs-lookup"><span data-stu-id="25d03-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="25d03-135">A primeira <xref:System.Windows.Controls.TabItem> tem <xref:System.Windows.UIElement> objetos que o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e o <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="25d03-136">O <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> é definido como um <xref:System.Windows.Controls.StackPanel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="25d03-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="25d03-137">O <xref:System.Windows.Controls.ContentControl.Content%2A> é definido como um <xref:System.Windows.Controls.StackPanel> que contém uma <xref:System.Windows.Controls.TextBlock> e uma <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="25d03-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="25d03-138">A segunda <xref:System.Windows.Controls.TabItem> tem uma cadeia de caracteres na <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e uma <xref:System.Windows.Controls.TextBlock> no <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl que usa tipos diferentes na propriedade Header.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="25d03-140">Para obter um exemplo de como criar <xref:System.Windows.Controls.TabItem> objetos, consulte <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="25d03-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="25d03-141">Controles que contêm uma coleção de objetos arbitrários</span><span class="sxs-lookup"><span data-stu-id="25d03-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="25d03-142">A classe <xref:System.Windows.Controls.ItemsControl> herda de <xref:System.Windows.Controls.Control> e pode conter vários itens, como cadeias de caracteres, objetos ou outros elementos.</span><span class="sxs-lookup"><span data-stu-id="25d03-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="25d03-143">Suas propriedades de conteúdo são <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> e <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="25d03-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> normalmente é usado para preencher o <xref:System.Windows.Controls.ItemsControl> com uma coleção de dados.</span><span class="sxs-lookup"><span data-stu-id="25d03-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="25d03-145">Se você não quiser usar uma coleção para popular a <xref:System.Windows.Controls.ItemsControl>, poderá adicionar itens usando a propriedade <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="25d03-146">Os seguintes controles herdam de <xref:System.Windows.Controls.ItemsControl> e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="25d03-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="25d03-147">A ilustração a seguir mostra um <xref:System.Windows.Controls.ListBox> que contém estes tipos de itens:</span><span class="sxs-lookup"><span data-stu-id="25d03-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="25d03-148">Uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="25d03-148">A string.</span></span>  
  
- <span data-ttu-id="25d03-149">Um objeto <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="25d03-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="25d03-150">Um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="25d03-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="25d03-151">Um <xref:System.Windows.Controls.Panel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="25d03-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Captura de tela que mostra uma caixa de listagem com quatro tipos de conteúdo.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="25d03-153">Controles que contêm uma coleção de objetos arbitrários e um cabeçalho</span><span class="sxs-lookup"><span data-stu-id="25d03-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="25d03-154">A classe <xref:System.Windows.Controls.HeaderedItemsControl> herda de <xref:System.Windows.Controls.ItemsControl> e pode conter vários itens, como cadeias de caracteres, objetos ou outros elementos, e um cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="25d03-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="25d03-155">Ele herda as propriedades de conteúdo <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>e <xref:System.Windows.Controls.ItemsControl.Items%2A>, e define a propriedade <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> que pode ser um objeto arbitrário.</span><span class="sxs-lookup"><span data-stu-id="25d03-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="25d03-156">Os seguintes controles herdam de <xref:System.Windows.Controls.HeaderedItemsControl> e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="25d03-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="25d03-157">Classes que contêm uma coleção de objetos de UIElement</span><span class="sxs-lookup"><span data-stu-id="25d03-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="25d03-158">A classe <xref:System.Windows.Controls.Panel> posiciona e organiza objetos <xref:System.Windows.UIElement> filhos.</span><span class="sxs-lookup"><span data-stu-id="25d03-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="25d03-159">Sua propriedade de conteúdo é <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="25d03-160">As classes a seguir herdam da classe <xref:System.Windows.Controls.Panel> e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="25d03-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="25d03-161">Para obter mais informações, consulte [Visão geral dos painéis](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="25d03-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="25d03-162">Classes que afetam a aparência de um UIElement</span><span class="sxs-lookup"><span data-stu-id="25d03-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="25d03-163">A classe <xref:System.Windows.Controls.Decorator> aplica efeitos visuais em ou em um único <xref:System.Windows.UIElement>filho.</span><span class="sxs-lookup"><span data-stu-id="25d03-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="25d03-164">Sua propriedade de conteúdo é <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="25d03-165">As classes a seguir herdam de <xref:System.Windows.Controls.Decorator> e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="25d03-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="25d03-166">A ilustração a seguir mostra um <xref:System.Windows.Controls.TextBox> que tem (decorado com) um <xref:System.Windows.Controls.Border> em volta dele.</span><span class="sxs-lookup"><span data-stu-id="25d03-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="25d03-167">![TextBox com borda preta](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="25d03-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="25d03-168">TextBlock que tem uma borda</span><span class="sxs-lookup"><span data-stu-id="25d03-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="25d03-169">Classes que fornecem comentários visuais sobre um UIElement</span><span class="sxs-lookup"><span data-stu-id="25d03-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="25d03-170">A classe <xref:System.Windows.Documents.Adorner> fornece indicações visuais para um usuário.</span><span class="sxs-lookup"><span data-stu-id="25d03-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="25d03-171">Por exemplo, use um <xref:System.Windows.Documents.Adorner> para adicionar identificadores funcionais a elementos ou fornecer informações de estado sobre um controle.</span><span class="sxs-lookup"><span data-stu-id="25d03-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="25d03-172">A classe <xref:System.Windows.Documents.Adorner> fornece uma estrutura para que você possa criar seus próprios adornos.</span><span class="sxs-lookup"><span data-stu-id="25d03-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="25d03-173">não fornece adornos implementados.</span><span class="sxs-lookup"><span data-stu-id="25d03-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="25d03-174">Para mais informações, consulte [Visão geral dos adornos](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="25d03-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="25d03-175">Classes que habilitam os usuários a inserir texto</span><span class="sxs-lookup"><span data-stu-id="25d03-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="25d03-176">O WPF fornece três principais controles que habilitam os usuários a inserir texto.</span><span class="sxs-lookup"><span data-stu-id="25d03-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="25d03-177">Cada controle exibe o texto de forma diferente.</span><span class="sxs-lookup"><span data-stu-id="25d03-177">Each control displays the text differently.</span></span> <span data-ttu-id="25d03-178">A tabela a seguir lista esses três controles relacionados ao texto, seus recursos quando eles exibem texto e suas propriedades que contêm o texto do controle.</span><span class="sxs-lookup"><span data-stu-id="25d03-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="25d03-179">Controle</span><span class="sxs-lookup"><span data-stu-id="25d03-179">Control</span></span>|<span data-ttu-id="25d03-180">O texto é exibido como</span><span class="sxs-lookup"><span data-stu-id="25d03-180">Text is displayed as</span></span>|<span data-ttu-id="25d03-181">Propriedade de conteúdo</span><span class="sxs-lookup"><span data-stu-id="25d03-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="25d03-182">Texto sem formatação</span><span class="sxs-lookup"><span data-stu-id="25d03-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="25d03-183">Texto formatado</span><span class="sxs-lookup"><span data-stu-id="25d03-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="25d03-184">Texto oculto (os caracteres são mascarados)</span><span class="sxs-lookup"><span data-stu-id="25d03-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="25d03-185">Classes que exibem seu texto</span><span class="sxs-lookup"><span data-stu-id="25d03-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="25d03-186">Várias classes podem ser usadas para exibir texto simples ou formatado.</span><span class="sxs-lookup"><span data-stu-id="25d03-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="25d03-187">Você pode usar <xref:System.Windows.Controls.TextBlock> para exibir pequenas quantidades de texto.</span><span class="sxs-lookup"><span data-stu-id="25d03-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="25d03-188">Se você quiser exibir grandes quantidades de texto, use os controles <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="25d03-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="25d03-189">O <xref:System.Windows.Controls.TextBlock> tem duas propriedades de conteúdo: <xref:System.Windows.Controls.TextBlock.Text%2A> e <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="25d03-190">Quando você deseja exibir o texto que usa formatação consistente, a propriedade <xref:System.Windows.Controls.TextBlock.Text%2A> geralmente é a melhor opção.</span><span class="sxs-lookup"><span data-stu-id="25d03-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="25d03-191">Se você planeja usar formatação diferente em todo o texto, use a propriedade <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d03-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="25d03-192">A propriedade <xref:System.Windows.Controls.TextBlock.Inlines%2A> é uma coleção de objetos <xref:System.Windows.Documents.Inline>, que especificam como formatar o texto.</span><span class="sxs-lookup"><span data-stu-id="25d03-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="25d03-193">A tabela a seguir lista a propriedade de conteúdo para as classes <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>e <xref:System.Windows.Controls.FlowDocumentScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="25d03-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="25d03-194">Controle</span><span class="sxs-lookup"><span data-stu-id="25d03-194">Control</span></span>|<span data-ttu-id="25d03-195">Propriedade de conteúdo</span><span class="sxs-lookup"><span data-stu-id="25d03-195">Content property</span></span>|<span data-ttu-id="25d03-196">Tipo de propriedade de conteúdo</span><span class="sxs-lookup"><span data-stu-id="25d03-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="25d03-197">Documento</span><span class="sxs-lookup"><span data-stu-id="25d03-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="25d03-198">Documento</span><span class="sxs-lookup"><span data-stu-id="25d03-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="25d03-199">Documento</span><span class="sxs-lookup"><span data-stu-id="25d03-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="25d03-200">O <xref:System.Windows.Documents.FlowDocument> implementa a interface <xref:System.Windows.Documents.IDocumentPaginatorSource>; Portanto, todas as três classes podem pegar um <xref:System.Windows.Documents.FlowDocument> como conteúdo.</span><span class="sxs-lookup"><span data-stu-id="25d03-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="25d03-201">Classes que formatam seu texto</span><span class="sxs-lookup"><span data-stu-id="25d03-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="25d03-202"><xref:System.Windows.Documents.TextElement> e suas classes relacionadas permitem que você formate o texto.</span><span class="sxs-lookup"><span data-stu-id="25d03-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="25d03-203"><xref:System.Windows.Documents.TextElement> objetos contêm e formatam texto em objetos <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="25d03-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="25d03-204">Os dois tipos principais de objetos <xref:System.Windows.Documents.TextElement> são elementos de <xref:System.Windows.Documents.Block> e elementos de <xref:System.Windows.Documents.Inline>.</span><span class="sxs-lookup"><span data-stu-id="25d03-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="25d03-205">Um elemento <xref:System.Windows.Documents.Block> representa um bloco de texto, como um parágrafo ou uma lista.</span><span class="sxs-lookup"><span data-stu-id="25d03-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="25d03-206">Um elemento <xref:System.Windows.Documents.Inline> representa uma parte do texto em um bloco.</span><span class="sxs-lookup"><span data-stu-id="25d03-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="25d03-207">Muitas classes de <xref:System.Windows.Documents.Inline> especificam a formatação para o texto ao qual elas são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="25d03-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="25d03-208">Cada <xref:System.Windows.Documents.TextElement> tem seu próprio modelo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="25d03-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="25d03-209">Para obter mais informações, consulte [Visão geral do modelo de conteúdo TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="25d03-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d03-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25d03-210">See also</span></span>

- [<span data-ttu-id="25d03-211">Avançado</span><span class="sxs-lookup"><span data-stu-id="25d03-211">Advanced</span></span>](../advanced/index.md)
