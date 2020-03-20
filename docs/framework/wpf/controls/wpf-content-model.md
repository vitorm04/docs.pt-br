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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187401"
---
# <a name="wpf-content-model"></a><span data-ttu-id="31512-102">Modelo de conteúdo do WPF</span><span class="sxs-lookup"><span data-stu-id="31512-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="31512-103">é uma plataforma de apresentação que fornece muitos controles e tipos de controle cujo objetivo principal é exibir diferentes tipos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="31512-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="31512-104">Para determinar qual controle usar ou de qual controle derivar, você deve compreender os tipos de objetos que um controle específico pode exibir.</span><span class="sxs-lookup"><span data-stu-id="31512-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="31512-105">Este tópico resume o modelo de conteúdo para os controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o tipos semelhantes a controle.</span><span class="sxs-lookup"><span data-stu-id="31512-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="31512-106">O modelo de conteúdo descreve qual conteúdo pode ser usado em um controle.</span><span class="sxs-lookup"><span data-stu-id="31512-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="31512-107">Este tópico também lista as propriedades de conteúdo para cada modelo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="31512-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="31512-108">Uma propriedade de conteúdo é uma propriedade que é usada para armazenar o conteúdo do objeto.</span><span class="sxs-lookup"><span data-stu-id="31512-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="31512-109">Classes que Contêm Conteúdo Arbitrário</span><span class="sxs-lookup"><span data-stu-id="31512-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="31512-110">Alguns controles podem conter um objeto de qualquer <xref:System.DateTime> tipo, como <xref:System.Windows.UIElement> uma string, um objeto ou um que seja um recipiente para itens adicionais.</span><span class="sxs-lookup"><span data-stu-id="31512-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="31512-111">Por exemplo, <xref:System.Windows.Controls.Button> uma pode conter uma imagem e algum texto; ou <xref:System.Windows.Controls.CheckBox> uma lata contenha o valor de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31512-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="31512-112">tem quatro classes que podem conter conteúdo arbitrário.</span><span class="sxs-lookup"><span data-stu-id="31512-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="31512-113">A tabela a seguir lista <xref:System.Windows.Controls.Control>as classes, que herdam de .</span><span class="sxs-lookup"><span data-stu-id="31512-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="31512-114">Classes que contêm conteúdo arbitrário</span><span class="sxs-lookup"><span data-stu-id="31512-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="31512-115">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="31512-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="31512-116">Um único objeto arbitrário.</span><span class="sxs-lookup"><span data-stu-id="31512-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="31512-117">Um cabeçalho e um único item, que são objetos arbitrários.</span><span class="sxs-lookup"><span data-stu-id="31512-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="31512-118">Uma coleção de objetos arbitrários.</span><span class="sxs-lookup"><span data-stu-id="31512-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="31512-119">Um cabeçalho e uma coleção de itens, que são objetos arbitrários.</span><span class="sxs-lookup"><span data-stu-id="31512-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="31512-120">Os controles que herdam essas classes podem conter o mesmo tipo de conteúdo e tratar o conteúdo da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="31512-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="31512-121">A ilustração a seguir mostra um controle de cada modelo de conteúdo que contém uma imagem e algum texto:</span><span class="sxs-lookup"><span data-stu-id="31512-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Captura de tela que mostra quatro controles diferentes, um de cada modelo de conteúdo.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="31512-123">Controles que contêm um único objeto arbitrário</span><span class="sxs-lookup"><span data-stu-id="31512-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="31512-124">A <xref:System.Windows.Controls.ContentControl> classe contém uma única peça de conteúdo arbitrário.</span><span class="sxs-lookup"><span data-stu-id="31512-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="31512-125">Sua propriedade <xref:System.Windows.Controls.ContentControl.Content%2A>de conteúdo é .</span><span class="sxs-lookup"><span data-stu-id="31512-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="31512-126">Os seguintes controles <xref:System.Windows.Controls.ContentControl> herdam e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="31512-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="31512-127">A ilustração a seguir <xref:System.Windows.Controls.ContentControl.Content%2A> mostra quatro botões <xref:System.DateTime> cujo conjunto <xref:System.Windows.Shapes.Rectangle>é <xref:System.Windows.Controls.Panel> definido como <xref:System.Windows.Shapes.Ellipse> uma <xref:System.Windows.Controls.TextBlock>string, um objeto, um , e um que contém um e um :</span><span class="sxs-lookup"><span data-stu-id="31512-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Captura de tela que mostra quatro botões com diferentes tipos de conteúdo.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="31512-129">Para um exemplo de <xref:System.Windows.Controls.ContentControl.Content%2A> como definir <xref:System.Windows.Controls.ContentControl>a propriedade, veja .</span><span class="sxs-lookup"><span data-stu-id="31512-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="31512-130">Controles que contêm um único objeto arbitrário e um cabeçalho</span><span class="sxs-lookup"><span data-stu-id="31512-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="31512-131">A <xref:System.Windows.Controls.HeaderedContentControl> classe herda <xref:System.Windows.Controls.ContentControl> e exibe conteúdo com um cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="31512-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="31512-132">Herda a propriedade <xref:System.Windows.Controls.ContentControl.Content%2A>de <xref:System.Windows.Controls.ContentControl> conteúdo, e <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> define a <xref:System.Object>propriedade que é do tipo; portanto, ambos podem ser um objeto arbitrário.</span><span class="sxs-lookup"><span data-stu-id="31512-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="31512-133">Os seguintes controles <xref:System.Windows.Controls.HeaderedContentControl> herdam e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="31512-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="31512-134">A ilustração <xref:System.Windows.Controls.TabItem> a seguir mostra dois objetos.</span><span class="sxs-lookup"><span data-stu-id="31512-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="31512-135">O <xref:System.Windows.Controls.TabItem> primeiro <xref:System.Windows.UIElement> tem <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> objetos <xref:System.Windows.Controls.ContentControl.Content%2A>como o e o .</span><span class="sxs-lookup"><span data-stu-id="31512-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="31512-136">O <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> é definido <xref:System.Windows.Controls.StackPanel> para <xref:System.Windows.Shapes.Ellipse> um <xref:System.Windows.Controls.TextBlock>que contém um e um .</span><span class="sxs-lookup"><span data-stu-id="31512-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="31512-137">O <xref:System.Windows.Controls.ContentControl.Content%2A> é definido <xref:System.Windows.Controls.StackPanel> para <xref:System.Windows.Controls.TextBlock> um <xref:System.Windows.Controls.Label>que contém a e a .</span><span class="sxs-lookup"><span data-stu-id="31512-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="31512-138">O <xref:System.Windows.Controls.TabItem> segundo tem uma <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> corda <xref:System.Windows.Controls.TextBlock> no <xref:System.Windows.Controls.ContentControl.Content%2A>e um no .</span><span class="sxs-lookup"><span data-stu-id="31512-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl que usa diferentes tipos na propriedade Cabeçalho.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="31512-140">Para um exemplo de <xref:System.Windows.Controls.TabItem> como <xref:System.Windows.Controls.HeaderedContentControl>criar objetos, veja .</span><span class="sxs-lookup"><span data-stu-id="31512-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="31512-141">Controles que contêm uma coleção de objetos arbitrários</span><span class="sxs-lookup"><span data-stu-id="31512-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="31512-142">A <xref:System.Windows.Controls.ItemsControl> classe herda <xref:System.Windows.Controls.Control> e pode conter vários itens, como cordas, objetos ou outros elementos.</span><span class="sxs-lookup"><span data-stu-id="31512-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="31512-143">Suas propriedades <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de <xref:System.Windows.Controls.ItemsControl.Items%2A>conteúdo são e .</span><span class="sxs-lookup"><span data-stu-id="31512-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="31512-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>é normalmente usado <xref:System.Windows.Controls.ItemsControl> para preencher o com uma coleta de dados.</span><span class="sxs-lookup"><span data-stu-id="31512-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="31512-145">Se você não quiser usar uma <xref:System.Windows.Controls.ItemsControl>coleção para preencher o , <xref:System.Windows.Controls.ItemsControl.Items%2A> você pode adicionar itens usando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="31512-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="31512-146">Os seguintes controles <xref:System.Windows.Controls.ItemsControl> herdam e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="31512-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="31512-147">A ilustração <xref:System.Windows.Controls.ListBox> a seguir mostra um que contém esses tipos de itens:</span><span class="sxs-lookup"><span data-stu-id="31512-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="31512-148">Uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="31512-148">A string.</span></span>  
  
- <span data-ttu-id="31512-149">Um objeto <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="31512-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="31512-150">Um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="31512-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="31512-151">A <xref:System.Windows.Controls.Panel> que <xref:System.Windows.Shapes.Ellipse> contém <xref:System.Windows.Controls.TextBlock>um e um .</span><span class="sxs-lookup"><span data-stu-id="31512-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Captura de tela que mostra uma ListBox com quatro tipos de conteúdo.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="31512-153">Controles que contêm uma coleção de objetos arbitrários e um cabeçalho</span><span class="sxs-lookup"><span data-stu-id="31512-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="31512-154">A <xref:System.Windows.Controls.HeaderedItemsControl> classe herda <xref:System.Windows.Controls.ItemsControl> e pode conter vários itens, como cordas, objetos ou outros elementos, e um cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="31512-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="31512-155">Herda as <xref:System.Windows.Controls.ItemsControl> propriedades <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>de <xref:System.Windows.Controls.ItemsControl.Items%2A>conteúdo, e define <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> a propriedade que pode ser um objeto arbitrário.</span><span class="sxs-lookup"><span data-stu-id="31512-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="31512-156">Os seguintes controles <xref:System.Windows.Controls.HeaderedItemsControl> herdam e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="31512-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="31512-157">Classes que contêm uma coleção de objetos de UIElement</span><span class="sxs-lookup"><span data-stu-id="31512-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="31512-158">A <xref:System.Windows.Controls.Panel> classe posiciona <xref:System.Windows.UIElement> e organiza objetos infantis.</span><span class="sxs-lookup"><span data-stu-id="31512-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="31512-159">Sua propriedade <xref:System.Windows.Controls.Panel.Children%2A>de conteúdo é .</span><span class="sxs-lookup"><span data-stu-id="31512-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="31512-160">As seguintes classes <xref:System.Windows.Controls.Panel> herdam da classe e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="31512-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="31512-161">Para obter mais informações, consulte [Visão geral dos painéis](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="31512-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="31512-162">Classes que afetam a aparência de um UIElement</span><span class="sxs-lookup"><span data-stu-id="31512-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="31512-163">A <xref:System.Windows.Controls.Decorator> classe aplica efeitos visuais em ou <xref:System.Windows.UIElement>em torno de uma única criança .</span><span class="sxs-lookup"><span data-stu-id="31512-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="31512-164">Sua propriedade <xref:System.Windows.Controls.Decorator.Child%2A>de conteúdo é .</span><span class="sxs-lookup"><span data-stu-id="31512-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="31512-165">As seguintes <xref:System.Windows.Controls.Decorator> classes herdam e usam seu modelo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="31512-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="31512-166">A ilustração <xref:System.Windows.Controls.TextBox> a seguir mostra um que <xref:System.Windows.Controls.Border> tem (é decorado com) um ao seu redor.</span><span class="sxs-lookup"><span data-stu-id="31512-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="31512-167">![TextBox com borda preta](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="31512-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="31512-168">TextBlock que tem uma borda</span><span class="sxs-lookup"><span data-stu-id="31512-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="31512-169">Classes que fornecem comentários visuais sobre um UIElement</span><span class="sxs-lookup"><span data-stu-id="31512-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="31512-170">A <xref:System.Windows.Documents.Adorner> classe fornece pistas visuais para um usuário.</span><span class="sxs-lookup"><span data-stu-id="31512-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="31512-171">Por exemplo, <xref:System.Windows.Documents.Adorner> use um para adicionar alças funcionais a elementos ou fornecer informações de estado sobre um controle.</span><span class="sxs-lookup"><span data-stu-id="31512-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="31512-172">A <xref:System.Windows.Documents.Adorner> classe fornece uma estrutura para que você possa criar seus próprios adornos.</span><span class="sxs-lookup"><span data-stu-id="31512-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="31512-173">não fornece adornos implementados.</span><span class="sxs-lookup"><span data-stu-id="31512-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="31512-174">Para mais informações, consulte [Visão geral dos adornos](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="31512-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="31512-175">Classes que habilitam os usuários a inserir texto</span><span class="sxs-lookup"><span data-stu-id="31512-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="31512-176">O WPF fornece três principais controles que habilitam os usuários a inserir texto.</span><span class="sxs-lookup"><span data-stu-id="31512-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="31512-177">Cada controle exibe o texto de forma diferente.</span><span class="sxs-lookup"><span data-stu-id="31512-177">Each control displays the text differently.</span></span> <span data-ttu-id="31512-178">A tabela a seguir lista esses três controles relacionados ao texto, seus recursos quando eles exibem texto e suas propriedades que contêm o texto do controle.</span><span class="sxs-lookup"><span data-stu-id="31512-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="31512-179">Control</span><span class="sxs-lookup"><span data-stu-id="31512-179">Control</span></span>|<span data-ttu-id="31512-180">O texto é exibido como</span><span class="sxs-lookup"><span data-stu-id="31512-180">Text is displayed as</span></span>|<span data-ttu-id="31512-181">Propriedade de conteúdo</span><span class="sxs-lookup"><span data-stu-id="31512-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="31512-182">Texto sem formatação</span><span class="sxs-lookup"><span data-stu-id="31512-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="31512-183">Texto formatado</span><span class="sxs-lookup"><span data-stu-id="31512-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="31512-184">Texto oculto (os caracteres são mascarados)</span><span class="sxs-lookup"><span data-stu-id="31512-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a><span data-ttu-id="31512-185">Classes que exibem seu texto</span><span class="sxs-lookup"><span data-stu-id="31512-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="31512-186">Várias classes podem ser usadas para exibir texto simples ou formatado.</span><span class="sxs-lookup"><span data-stu-id="31512-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="31512-187">Você pode <xref:System.Windows.Controls.TextBlock> usar para exibir pequenas quantidades de texto.</span><span class="sxs-lookup"><span data-stu-id="31512-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="31512-188">Se você quiser exibir grandes quantidades <xref:System.Windows.Controls.FlowDocumentReader>de <xref:System.Windows.Controls.FlowDocumentPageViewer>texto, use os controles ou <xref:System.Windows.Controls.FlowDocumentScrollViewer> controles.</span><span class="sxs-lookup"><span data-stu-id="31512-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="31512-189">O <xref:System.Windows.Controls.TextBlock> tem duas <xref:System.Windows.Controls.TextBlock.Text%2A> propriedades <xref:System.Windows.Controls.TextBlock.Inlines%2A>de conteúdo: e .</span><span class="sxs-lookup"><span data-stu-id="31512-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="31512-190">Quando você deseja exibir texto que usa <xref:System.Windows.Controls.TextBlock.Text%2A> formatação consistente, a propriedade é muitas vezes a sua melhor escolha.</span><span class="sxs-lookup"><span data-stu-id="31512-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="31512-191">Se você planeja usar formatação diferente ao <xref:System.Windows.Controls.TextBlock.Inlines%2A> longo do texto, use a propriedade.</span><span class="sxs-lookup"><span data-stu-id="31512-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="31512-192">A <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriedade é <xref:System.Windows.Documents.Inline> uma coleção de objetos, que especificam como formatar texto.</span><span class="sxs-lookup"><span data-stu-id="31512-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="31512-193">A tabela a seguir <xref:System.Windows.Controls.FlowDocumentReader>lista <xref:System.Windows.Controls.FlowDocumentPageViewer>a <xref:System.Windows.Controls.FlowDocumentScrollViewer> propriedade de conteúdo para , e classes.</span><span class="sxs-lookup"><span data-stu-id="31512-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="31512-194">Control</span><span class="sxs-lookup"><span data-stu-id="31512-194">Control</span></span>|<span data-ttu-id="31512-195">Propriedade de conteúdo</span><span class="sxs-lookup"><span data-stu-id="31512-195">Content property</span></span>|<span data-ttu-id="31512-196">Tipo de propriedade de conteúdo</span><span class="sxs-lookup"><span data-stu-id="31512-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="31512-197">Document</span><span class="sxs-lookup"><span data-stu-id="31512-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="31512-198">Document</span><span class="sxs-lookup"><span data-stu-id="31512-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="31512-199">Document</span><span class="sxs-lookup"><span data-stu-id="31512-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="31512-200">O <xref:System.Windows.Documents.FlowDocument> implementa <xref:System.Windows.Documents.IDocumentPaginatorSource> a interface; portanto, todas as três <xref:System.Windows.Documents.FlowDocument> classes podem ter um como conteúdo.</span><span class="sxs-lookup"><span data-stu-id="31512-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a><span data-ttu-id="31512-201">Classes que formatam seu texto</span><span class="sxs-lookup"><span data-stu-id="31512-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="31512-202"><xref:System.Windows.Documents.TextElement>e suas classes relacionadas permitem que você forme texto.</span><span class="sxs-lookup"><span data-stu-id="31512-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="31512-203"><xref:System.Windows.Documents.TextElement>objetos contêm <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument> formatam texto em e objetos.</span><span class="sxs-lookup"><span data-stu-id="31512-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="31512-204">Os dois tipos <xref:System.Windows.Documents.TextElement> principais de objetos são <xref:System.Windows.Documents.Block> elementos e <xref:System.Windows.Documents.Inline> elementos.</span><span class="sxs-lookup"><span data-stu-id="31512-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="31512-205">Um <xref:System.Windows.Documents.Block> elemento representa um bloco de texto, como um parágrafo ou uma lista.</span><span class="sxs-lookup"><span data-stu-id="31512-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="31512-206">Um <xref:System.Windows.Documents.Inline> elemento representa uma parte do texto em um bloco.</span><span class="sxs-lookup"><span data-stu-id="31512-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="31512-207">Muitas <xref:System.Windows.Documents.Inline> classes especificam a formatação para o texto ao qual são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="31512-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="31512-208">Cada <xref:System.Windows.Documents.TextElement> um tem seu próprio modelo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="31512-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="31512-209">Para obter mais informações, consulte [Visão geral do modelo de conteúdo TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="31512-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31512-210">Confira também</span><span class="sxs-lookup"><span data-stu-id="31512-210">See also</span></span>

- [<span data-ttu-id="31512-211">Avançado</span><span class="sxs-lookup"><span data-stu-id="31512-211">Advanced</span></span>](../advanced/index.md)
