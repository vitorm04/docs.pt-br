---
title: Controles
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66c6cc58423a2af8d0fd6de93b8884918888fb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="controls"></a>Controles
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]é fornecido com muitos dos componentes comuns de interface do usuário que são usados em quase todos os aplicativos do Windows, como <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>, e <xref:System.Windows.Controls.ListBox>. Historicamente, esses objetos são chamados de controles. Enquanto o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK continua a usar o termo "control" significando livremente qualquer classe que representa um objeto visível em um aplicativo, é importante observar que uma classe não precisa herdar o <xref:System.Windows.Controls.Control> classe para ter uma presença visível. Classes que herdam o <xref:System.Windows.Controls.Control> classe contém um <xref:System.Windows.Controls.ControlTemplate>, que permite que o consumidor de um controle alterar radicalmente a aparência do controle sem a necessidade de criar uma nova subclasse.  Este tópico discute como controles (tanto aqueles que herdam o <xref:System.Windows.Controls.Control> classe e os que não) são normalmente usados no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Criando uma instância de um controle  
 Você pode adicionar um controle a um aplicativo usando o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou código.  O exemplo a seguir mostra como criar um aplicativo simples que solicita a um usuário o nome e sobrenome.  Este exemplo cria seis controles: dois rótulos, duas caixas de texto e dois botões, em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Todos os controles podem ser criados da mesma forma.  
  
 [!code-xaml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 O exemplo a seguir cria o mesmo aplicativo no código. Para resumir, a criação do <xref:System.Windows.Controls.Grid>, `grid1`, foi excluída do exemplo. `grid1`tem as mesmas definições de coluna e linha, conforme mostrado na anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo.  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Alterando a aparência de um controle  
 É comum alterar a aparência de um controle para ajustar a aparência do seu aplicativo. Você pode alterar a aparência de um controle seguindo um destes procedimentos, dependendo do que deseja realizar:  
  
-   Altere o valor de uma propriedade do controle.  
  
-   Criar um <xref:System.Windows.Style> para o controle.  
  
-   Criar um novo <xref:System.Windows.Controls.ControlTemplate> para o controle.  
  
### <a name="changing-a-controls-property-value"></a>Alterando o valor da propriedade do controle  
 Muitos controles têm propriedades que permitem que você altere a aparência do controle, como o <xref:System.Windows.Controls.Control.Background%2A> de um <xref:System.Windows.Controls.Button>. Você pode definir as propriedades de valor em ambos os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e código. O exemplo a seguir define o <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, e <xref:System.Windows.Controls.Control.FontWeight%2A> propriedades em um <xref:System.Windows.Controls.Button> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 O exemplo a seguir define as mesmas propriedades no código.  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Criando um estilo para um controle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece a capacidade de especificar a aparência dos controles de atacado, em vez de definir propriedades em cada instância no aplicativo, criando um <xref:System.Windows.Style>. O exemplo a seguir cria um <xref:System.Windows.Style> que é aplicada a cada <xref:System.Windows.Controls.Button> no aplicativo. <xref:System.Windows.Style>definições geralmente são definidas em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em uma <xref:System.Windows.ResourceDictionary>, como o <xref:System.Windows.FrameworkElement.Resources%2A> propriedade o <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Você também pode aplicar um estilo somente a certos controles de um tipo específico ao atribuir uma chave para o estilo e especificando essa chave no `Style` propriedade do controle.  Para obter mais informações sobre estilos, consulte [estilos e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Criando um ControlTemplate  
 Um <xref:System.Windows.Style> permite que você defina propriedades em vários controles em um momento, mas, às vezes, convém personalizar a aparência de um <xref:System.Windows.Controls.Control> além do que você pode fazer, criando um <xref:System.Windows.Style>. Classes que herdam o <xref:System.Windows.Controls.Control> classe tiver um <xref:System.Windows.Controls.ControlTemplate>, que define a estrutura e a aparência de um <xref:System.Windows.Controls.Control>. O <xref:System.Windows.Controls.Control.Template%2A> propriedade de um <xref:System.Windows.Controls.Control> é público, então você pode dar uma <xref:System.Windows.Controls.Control> um <xref:System.Windows.Controls.ControlTemplate> que é diferente do padrão. Geralmente você pode especificar um novo <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.Control> em vez de herdar de um controle para personalizar a aparência de um <xref:System.Windows.Controls.Control>.  
  
 Considere o controle muito comum, <xref:System.Windows.Controls.Button>.  O comportamento primário de um <xref:System.Windows.Controls.Button> é permitir que um aplicativo para executar alguma ação quando o usuário clica neles.  Por padrão, o <xref:System.Windows.Controls.Button> na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparece como um retângulo elevado.  Ao desenvolver um aplicativo, talvez você queira aproveitar o comportamento de um <xref:System.Windows.Controls.Button>– manipulando o clique no botão evento – ou seja, mas você pode alterar a aparência do botão além do que você pode fazer alterando propriedades do botão.  Nesse caso, você pode criar um novo <xref:System.Windows.Controls.ControlTemplate>.  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.Button>.  O <xref:System.Windows.Controls.ControlTemplate> cria um <xref:System.Windows.Controls.Button> com cantos arredondados e um plano de fundo do gradiente.  O <xref:System.Windows.Controls.ControlTemplate> contém um <xref:System.Windows.Controls.Border> cujo <xref:System.Windows.Controls.Border.Background%2A> é um <xref:System.Windows.Media.LinearGradientBrush> com dois <xref:System.Windows.Media.GradientStop> objetos.  A primeira <xref:System.Windows.Media.GradientStop> usa associação de dados para associar o <xref:System.Windows.Media.GradientStop.Color%2A> propriedade o <xref:System.Windows.Media.GradientStop> para a cor do plano de fundo do botão.  Quando você define o <xref:System.Windows.Controls.Control.Background%2A> propriedade o <xref:System.Windows.Controls.Button>, a cor desse valor será usada como o primeiro <xref:System.Windows.Media.GradientStop>. Para obter mais informações sobre vinculação de dados, veja [Noções básicas de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md). O exemplo também cria um <xref:System.Windows.Trigger> que altera a aparência do <xref:System.Windows.Controls.Button> quando <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> é `true`.  
  
 [!code-xaml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  O <xref:System.Windows.Controls.Control.Background%2A> propriedade o <xref:System.Windows.Controls.Button> deve ser definido como um <xref:System.Windows.Media.SolidColorBrush> para que o exemplo funcione corretamente.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Assinando eventos  
 Você pode assinar um evento de controle usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou código, mas você pode manipular apenas um evento no código.  O exemplo a seguir mostra como assinar o `Click` eventos de um <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 A exemplo a seguir trata o `Click` eventos de um <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Conteúdo avançado em controles  
 A maioria das classes que herdam o <xref:System.Windows.Controls.Control> classe tem a capacidade para conter conteúdo rico. Por exemplo, um <xref:System.Windows.Controls.Label> pode conter qualquer objeto, como uma cadeia de caracteres, um <xref:System.Windows.Controls.Image>, ou um <xref:System.Windows.Controls.Panel>.  As classes a seguir oferecem suporte a conteúdo rico e atuam como classes base para a maioria dos controles no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl>-- Alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, e <xref:System.Windows.Controls.ToolTip>.  
  
-   <xref:System.Windows.Controls.ItemsControl>-- Alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>, e <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>-- Alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>, e <xref:System.Windows.Controls.Expander>.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>-- Alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>, e <xref:System.Windows.Controls.ToolBar>.  
  
-  
  
 Para obter mais informações sobre essas classes base, consulte [modelo de conteúdo do WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Controles por categoria](../../../../docs/framework/wpf/controls/controls-by-category.md)  
 [Biblioteca de controles](../../../../docs/framework/wpf/controls/control-library.md)  
 [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Entrada](../../../../docs/framework/wpf/advanced/input-wpf.md)  
 [Habilitar um comando](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)  
 [Instruções passo a passo: criar um botão animado personalizado](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)  
 [Personalização do controle](../../../../docs/framework/wpf/controls/control-customization.md)
