---
title: Controles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 2ec8c0a99f4e2431aed0d8c24168b7329de669f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187527"
---
# <a name="controls"></a>Controles
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]navios com muitos dos componentes comuns de interface do <xref:System.Windows.Controls.Button>iu que são usados em quase todos os aplicativos do Windows, tais como, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>e <xref:System.Windows.Controls.ListBox>. Historicamente, esses objetos são chamados de controles. Enquanto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o SDK continua a usar o termo "controle" para significar vagamente qualquer classe que represente um objeto visível <xref:System.Windows.Controls.Control> em um aplicativo, é importante notar que uma classe não precisa herdar da classe para ter uma presença visível. As classes que <xref:System.Windows.Controls.Control> herdam da classe contêm um <xref:System.Windows.Controls.ControlTemplate>, que permite ao consumidor de um controle mudar radicalmente a aparência do controle sem ter que criar uma nova subclasse.  Este tópico discute como os controles (tanto <xref:System.Windows.Controls.Control> aqueles que herdam da classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]quanto os que não o fazem) são comumente usados em .  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>Criando uma instância de um controle  
 Você pode adicionar um controle a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] um aplicativo usando um ou código.  O exemplo a seguir mostra como criar um aplicativo simples que solicita a um usuário o nome e sobrenome.  Este exemplo cria seis controles: dois rótulos, duas caixas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]de texto e dois botões, em . Todos os controles podem ser criados da mesma forma.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 O exemplo a seguir cria o mesmo aplicativo no código. Para a brevidade, <xref:System.Windows.Controls.Grid>a `grid1`criação do , foi excluída da amostra. `grid1`tem as mesmas definições de coluna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e linha mostradas no exemplo anterior.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>Alterando a aparência de um controle  
 É comum alterar a aparência de um controle para ajustar a aparência do seu aplicativo. Você pode alterar a aparência de um controle seguindo um destes procedimentos, dependendo do que deseja realizar:  
  
- Altere o valor de uma propriedade do controle.  
  
- Crie <xref:System.Windows.Style> um para o controle.  
  
- Crie um <xref:System.Windows.Controls.ControlTemplate> novo para o controle.  
  
### <a name="changing-a-controls-property-value"></a>Alterando o valor da propriedade do controle  
 Muitos controles têm propriedades que permitem alterar a forma <xref:System.Windows.Controls.Control.Background%2A> como <xref:System.Windows.Controls.Button>o controle aparece, como o de um . Você pode definir as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] propriedades de valor em ambos e código. O exemplo a <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.FontSize%2A>seguir <xref:System.Windows.Controls.Control.FontWeight%2A> define as <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]propriedades e propriedades em uma in .  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 O exemplo a seguir define as mesmas propriedades no código.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Criando um estilo para um controle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]lhe dá a capacidade de especificar a aparência dos controles por atacado, em <xref:System.Windows.Style>vez de definir propriedades em cada instância no aplicativo, criando um . O exemplo a <xref:System.Windows.Style> seguir cria um <xref:System.Windows.Controls.Button> que é aplicado a cada um no aplicativo. <xref:System.Windows.Style>definições são tipicamente [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] definidas em <xref:System.Windows.ResourceDictionary> <xref:System.Windows.FrameworkElement.Resources%2A> um , <xref:System.Windows.FrameworkElement>como a propriedade do .  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Você também pode aplicar um estilo a apenas certos controles de um tipo específico, atribuindo uma chave ao estilo e especificando essa chave na propriedade do `Style` seu controle.  Para obter mais informações sobre estilos, consulte [Styling e Templating](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Criando um ControlTemplate  
 A <xref:System.Windows.Style> permite definir propriedades em vários controles de cada vez, mas às <xref:System.Windows.Controls.Control> vezes você pode querer <xref:System.Windows.Style>personalizar a aparência de um além do que você pode fazer criando um . As classes que <xref:System.Windows.Controls.Control> herdam da classe têm um <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Control>, que define a estrutura e aparência de um . A <xref:System.Windows.Controls.Control.Template%2A> propriedade <xref:System.Windows.Controls.Control> de um é pública, <xref:System.Windows.Controls.Control> então <xref:System.Windows.Controls.ControlTemplate> você pode dar um que é diferente do seu padrão. Muitas vezes você <xref:System.Windows.Controls.ControlTemplate> pode <xref:System.Windows.Controls.Control> especificar um novo para um em <xref:System.Windows.Controls.Control>vez de herdar de um controle para personalizar a aparência de um .  
  
 Considere o controle <xref:System.Windows.Controls.Button>muito comum, .  O principal comportamento <xref:System.Windows.Controls.Button> de a é permitir que um aplicativo tome alguma ação quando o usuário clica nele.  Por padrão, <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o in aparece como um retângulo elevado.  Ao desenvolver um aplicativo, você pode querer tirar <xref:System.Windows.Controls.Button>proveito do comportamento de um --ou seja, ao manusear o evento de clique do botão --, mas você pode alterar a aparência do botão além do que você pode fazer alterando as propriedades do botão.  Neste caso, você pode <xref:System.Windows.Controls.ControlTemplate>criar um novo .  
  
 O exemplo a <xref:System.Windows.Controls.ControlTemplate> seguir <xref:System.Windows.Controls.Button>cria um para a .  O <xref:System.Windows.Controls.ControlTemplate> cria <xref:System.Windows.Controls.Button> um com cantos arredondados e um fundo gradiente.  O <xref:System.Windows.Controls.ControlTemplate> contém <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Border.Background%2A> um <xref:System.Windows.Media.LinearGradientBrush> cujo <xref:System.Windows.Media.GradientStop> é um com dois objetos.  O <xref:System.Windows.Media.GradientStop> primeiro usa vinculação <xref:System.Windows.Media.GradientStop.Color%2A> de <xref:System.Windows.Media.GradientStop> dados para vincular a propriedade do à cor do fundo do botão.  Quando você <xref:System.Windows.Controls.Control.Background%2A> definir a <xref:System.Windows.Controls.Button>propriedade do , a cor desse <xref:System.Windows.Media.GradientStop>valor será usada como a primeira . Para obter mais informações sobre vinculação de dados, consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md). O exemplo também <xref:System.Windows.Trigger> cria um que <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> altera `true`a aparência do quando é .  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> A <xref:System.Windows.Controls.Control.Background%2A> propriedade <xref:System.Windows.Controls.Button> do deve ser <xref:System.Windows.Media.SolidColorBrush> definida como um para que o exemplo funcione corretamente.  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>Assinando eventos  
 Você pode assinar um evento de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] controle usando um ou código, mas você só pode lidar com um evento em código.  O exemplo a seguir mostra `Click` como <xref:System.Windows.Controls.Button>se inscrever no evento de a .  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 O exemplo a `Click` seguir lida <xref:System.Windows.Controls.Button>com o evento de um .  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>Conteúdo avançado em controles  
 A maioria das <xref:System.Windows.Controls.Control> classes que herdam da classe têm a capacidade de conter conteúdo rico. Por exemplo, <xref:System.Windows.Controls.Label> uma lata pode conter qualquer <xref:System.Windows.Controls.Image>objeto, <xref:System.Windows.Controls.Panel>como uma seqüência, um , ou um .  As classes a seguir fornecem suporte para conteúdo rico e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]atuam como classes base para a maioria dos controles em .  
  
- <xref:System.Windows.Controls.ContentControl>-- Alguns exemplos de classes que <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Button>herdam dessa classe são, e <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>-- Alguns exemplos de classes que <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.Menu>herdam dessa classe são, e <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>-- Alguns exemplos de classes que <xref:System.Windows.Controls.TabItem> <xref:System.Windows.Controls.GroupBox>herdam dessa classe são, e <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>-Alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>e <xref:System.Windows.Controls.ToolBar>.  

 Para obter mais informações sobre essas classes base, consulte [WPF Content Model](wpf-content-model.md).  
  
## <a name="see-also"></a>Confira também

- [Estilo e modelagem](styling-and-templating.md)
- [Controles por categoria](controls-by-category.md)
- [Biblioteca de controles](control-library.md)
- [Visão geral de modelagem dos dados](../data/data-templating-overview.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Entrada](../advanced/input-wpf.md)
- [Habilitar um comando](../advanced/how-to-enable-a-command.md)
- [Instruções passo a passo: criar um botão animado personalizado](walkthroughs-create-a-custom-animated-button.md)
- [Personalização do controle](control-customization.md)
