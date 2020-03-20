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
# <a name="wpf-content-model"></a>Modelo de conteúdo do WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é uma plataforma de apresentação que fornece muitos controles e tipos de controle cujo objetivo principal é exibir diferentes tipos de conteúdo. Para determinar qual controle usar ou de qual controle derivar, você deve compreender os tipos de objetos que um controle específico pode exibir.  
  
 Este tópico resume o modelo de conteúdo para os controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o tipos semelhantes a controle. O modelo de conteúdo descreve qual conteúdo pode ser usado em um controle. Este tópico também lista as propriedades de conteúdo para cada modelo de conteúdo. Uma propriedade de conteúdo é uma propriedade que é usada para armazenar o conteúdo do objeto.  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a>Classes que Contêm Conteúdo Arbitrário  
 Alguns controles podem conter um objeto de qualquer <xref:System.DateTime> tipo, como <xref:System.Windows.UIElement> uma string, um objeto ou um que seja um recipiente para itens adicionais. Por exemplo, <xref:System.Windows.Controls.Button> uma pode conter uma imagem e algum texto; ou <xref:System.Windows.Controls.CheckBox> uma lata contenha o valor de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem quatro classes que podem conter conteúdo arbitrário. A tabela a seguir lista <xref:System.Windows.Controls.Control>as classes, que herdam de .  
  
|Classes que contêm conteúdo arbitrário|Conteúdo|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Um único objeto arbitrário.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Um cabeçalho e um único item, que são objetos arbitrários.|  
|<xref:System.Windows.Controls.ItemsControl>|Uma coleção de objetos arbitrários.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Um cabeçalho e uma coleção de itens, que são objetos arbitrários.|  
  
 Os controles que herdam essas classes podem conter o mesmo tipo de conteúdo e tratar o conteúdo da mesma forma. A ilustração a seguir mostra um controle de cada modelo de conteúdo que contém uma imagem e algum texto:  
  
 ![Captura de tela que mostra quatro controles diferentes, um de cada modelo de conteúdo.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Controles que contêm um único objeto arbitrário  
 A <xref:System.Windows.Controls.ContentControl> classe contém uma única peça de conteúdo arbitrário. Sua propriedade <xref:System.Windows.Controls.ContentControl.Content%2A>de conteúdo é . Os seguintes controles <xref:System.Windows.Controls.ContentControl> herdam e usam seu modelo de conteúdo:  
  
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
  
 A ilustração a seguir <xref:System.Windows.Controls.ContentControl.Content%2A> mostra quatro botões <xref:System.DateTime> cujo conjunto <xref:System.Windows.Shapes.Rectangle>é <xref:System.Windows.Controls.Panel> definido como <xref:System.Windows.Shapes.Ellipse> uma <xref:System.Windows.Controls.TextBlock>string, um objeto, um , e um que contém um e um :  
  
 ![Captura de tela que mostra quatro botões com diferentes tipos de conteúdo.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Para um exemplo de <xref:System.Windows.Controls.ContentControl.Content%2A> como definir <xref:System.Windows.Controls.ContentControl>a propriedade, veja .  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Controles que contêm um único objeto arbitrário e um cabeçalho  
 A <xref:System.Windows.Controls.HeaderedContentControl> classe herda <xref:System.Windows.Controls.ContentControl> e exibe conteúdo com um cabeçalho. Herda a propriedade <xref:System.Windows.Controls.ContentControl.Content%2A>de <xref:System.Windows.Controls.ContentControl> conteúdo, e <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> define a <xref:System.Object>propriedade que é do tipo; portanto, ambos podem ser um objeto arbitrário.  
  
 Os seguintes controles <xref:System.Windows.Controls.HeaderedContentControl> herdam e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 A ilustração <xref:System.Windows.Controls.TabItem> a seguir mostra dois objetos. O <xref:System.Windows.Controls.TabItem> primeiro <xref:System.Windows.UIElement> tem <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> objetos <xref:System.Windows.Controls.ContentControl.Content%2A>como o e o . O <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> é definido <xref:System.Windows.Controls.StackPanel> para <xref:System.Windows.Shapes.Ellipse> um <xref:System.Windows.Controls.TextBlock>que contém um e um . O <xref:System.Windows.Controls.ContentControl.Content%2A> é definido <xref:System.Windows.Controls.StackPanel> para <xref:System.Windows.Controls.TextBlock> um <xref:System.Windows.Controls.Label>que contém a e a . O <xref:System.Windows.Controls.TabItem> segundo tem uma <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> corda <xref:System.Windows.Controls.TextBlock> no <xref:System.Windows.Controls.ContentControl.Content%2A>e um no .  
  
 ![TabControl que usa diferentes tipos na propriedade Cabeçalho.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Para um exemplo de <xref:System.Windows.Controls.TabItem> como <xref:System.Windows.Controls.HeaderedContentControl>criar objetos, veja .  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Controles que contêm uma coleção de objetos arbitrários  
 A <xref:System.Windows.Controls.ItemsControl> classe herda <xref:System.Windows.Controls.Control> e pode conter vários itens, como cordas, objetos ou outros elementos. Suas propriedades <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de <xref:System.Windows.Controls.ItemsControl.Items%2A>conteúdo são e . <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>é normalmente usado <xref:System.Windows.Controls.ItemsControl> para preencher o com uma coleta de dados. Se você não quiser usar uma <xref:System.Windows.Controls.ItemsControl>coleção para preencher o , <xref:System.Windows.Controls.ItemsControl.Items%2A> você pode adicionar itens usando a propriedade.  
  
 Os seguintes controles <xref:System.Windows.Controls.ItemsControl> herdam e usam seu modelo de conteúdo:  
  
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
  
 A ilustração <xref:System.Windows.Controls.ListBox> a seguir mostra um que contém esses tipos de itens:  
  
- Uma cadeia de caracteres.  
  
- Um objeto <xref:System.DateTime> .  
  
- Um <xref:System.Windows.UIElement>.  
  
- A <xref:System.Windows.Controls.Panel> que <xref:System.Windows.Shapes.Ellipse> contém <xref:System.Windows.Controls.TextBlock>um e um .  
  
 ![Captura de tela que mostra uma ListBox com quatro tipos de conteúdo.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Controles que contêm uma coleção de objetos arbitrários e um cabeçalho  
 A <xref:System.Windows.Controls.HeaderedItemsControl> classe herda <xref:System.Windows.Controls.ItemsControl> e pode conter vários itens, como cordas, objetos ou outros elementos, e um cabeçalho. Herda as <xref:System.Windows.Controls.ItemsControl> propriedades <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>de <xref:System.Windows.Controls.ItemsControl.Items%2A>conteúdo, e define <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> a propriedade que pode ser um objeto arbitrário.  
  
 Os seguintes controles <xref:System.Windows.Controls.HeaderedItemsControl> herdam e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Classes que contêm uma coleção de objetos de UIElement  
 A <xref:System.Windows.Controls.Panel> classe posiciona <xref:System.Windows.UIElement> e organiza objetos infantis. Sua propriedade <xref:System.Windows.Controls.Panel.Children%2A>de conteúdo é .  
  
 As seguintes classes <xref:System.Windows.Controls.Panel> herdam da classe e usam seu modelo de conteúdo:  
  
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
  
 Para obter mais informações, consulte [Visão geral dos painéis](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Classes que afetam a aparência de um UIElement  
 A <xref:System.Windows.Controls.Decorator> classe aplica efeitos visuais em ou <xref:System.Windows.UIElement>em torno de uma única criança . Sua propriedade <xref:System.Windows.Controls.Decorator.Child%2A>de conteúdo é . As seguintes <xref:System.Windows.Controls.Decorator> classes herdam e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 A ilustração <xref:System.Windows.Controls.TextBox> a seguir mostra um que <xref:System.Windows.Controls.Border> tem (é decorado com) um ao seu redor.  
  
 ![TextBox com borda preta](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock que tem uma borda  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Classes que fornecem comentários visuais sobre um UIElement  
 A <xref:System.Windows.Documents.Adorner> classe fornece pistas visuais para um usuário. Por exemplo, <xref:System.Windows.Documents.Adorner> use um para adicionar alças funcionais a elementos ou fornecer informações de estado sobre um controle. A <xref:System.Windows.Documents.Adorner> classe fornece uma estrutura para que você possa criar seus próprios adornos. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não fornece adornos implementados. Para mais informações, consulte [Visão geral dos adornos](adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a>Classes que habilitam os usuários a inserir texto  
 O WPF fornece três principais controles que habilitam os usuários a inserir texto. Cada controle exibe o texto de forma diferente. A tabela a seguir lista esses três controles relacionados ao texto, seus recursos quando eles exibem texto e suas propriedades que contêm o texto do controle.  
  
|Control|O texto é exibido como|Propriedade de conteúdo|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Texto sem formatação|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Texto formatado|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Texto oculto (os caracteres são mascarados)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a>Classes que exibem seu texto  
 Várias classes podem ser usadas para exibir texto simples ou formatado. Você pode <xref:System.Windows.Controls.TextBlock> usar para exibir pequenas quantidades de texto. Se você quiser exibir grandes quantidades <xref:System.Windows.Controls.FlowDocumentReader>de <xref:System.Windows.Controls.FlowDocumentPageViewer>texto, use os controles ou <xref:System.Windows.Controls.FlowDocumentScrollViewer> controles.  
  
 O <xref:System.Windows.Controls.TextBlock> tem duas <xref:System.Windows.Controls.TextBlock.Text%2A> propriedades <xref:System.Windows.Controls.TextBlock.Inlines%2A>de conteúdo: e . Quando você deseja exibir texto que usa <xref:System.Windows.Controls.TextBlock.Text%2A> formatação consistente, a propriedade é muitas vezes a sua melhor escolha. Se você planeja usar formatação diferente ao <xref:System.Windows.Controls.TextBlock.Inlines%2A> longo do texto, use a propriedade. A <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriedade é <xref:System.Windows.Documents.Inline> uma coleção de objetos, que especificam como formatar texto.  
  
 A tabela a seguir <xref:System.Windows.Controls.FlowDocumentReader>lista <xref:System.Windows.Controls.FlowDocumentPageViewer>a <xref:System.Windows.Controls.FlowDocumentScrollViewer> propriedade de conteúdo para , e classes.  
  
|Control|Propriedade de conteúdo|Tipo de propriedade de conteúdo|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Document|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Document|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Document|<xref:System.Windows.Documents.FlowDocument>|  
  
 O <xref:System.Windows.Documents.FlowDocument> implementa <xref:System.Windows.Documents.IDocumentPaginatorSource> a interface; portanto, todas as três <xref:System.Windows.Documents.FlowDocument> classes podem ter um como conteúdo.  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a>Classes que formatam seu texto  
 <xref:System.Windows.Documents.TextElement>e suas classes relacionadas permitem que você forme texto. <xref:System.Windows.Documents.TextElement>objetos contêm <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument> formatam texto em e objetos. Os dois tipos <xref:System.Windows.Documents.TextElement> principais de objetos são <xref:System.Windows.Documents.Block> elementos e <xref:System.Windows.Documents.Inline> elementos. Um <xref:System.Windows.Documents.Block> elemento representa um bloco de texto, como um parágrafo ou uma lista. Um <xref:System.Windows.Documents.Inline> elemento representa uma parte do texto em um bloco. Muitas <xref:System.Windows.Documents.Inline> classes especificam a formatação para o texto ao qual são aplicadas. Cada <xref:System.Windows.Documents.TextElement> um tem seu próprio modelo de conteúdo. Para obter mais informações, consulte [Visão geral do modelo de conteúdo TextElement](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Confira também

- [Avançado](../advanced/index.md)
