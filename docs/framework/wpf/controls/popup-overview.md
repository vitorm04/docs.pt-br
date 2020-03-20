---
title: Visão geral do pop-up
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 911130d52744c5ba54750f214829a5d1900e083c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185947"
---
# <a name="popup-overview"></a>Visão geral do pop-up
O <xref:System.Windows.Controls.Primitives.Popup> controle fornece uma maneira de exibir conteúdo em uma janela separada que flutua sobre a janela de aplicativo atual em relação a um elemento designado ou coordenada de tela. Este tópico introduz <xref:System.Windows.Controls.Primitives.Popup> o controle e fornece informações sobre seu uso.  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>O que é um pop-up?  
 Um <xref:System.Windows.Controls.Primitives.Popup> controle exibe conteúdo em uma janela separada em relação a um elemento ou ponto na tela. Quando <xref:System.Windows.Controls.Primitives.Popup> o é <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> visível, a `true`propriedade é definida como .  
  
> [!NOTE]
> A <xref:System.Windows.Controls.Primitives.Popup> não abre automaticamente quando o ponteiro do mouse se move sobre seu objeto pai. Se você <xref:System.Windows.Controls.Primitives.Popup> quiser abrir automaticamente, <xref:System.Windows.Controls.ToolTip> use <xref:System.Windows.Controls.ToolTipService> a ou classe. Para obter mais informações, consulte [Visão geral de ToolTip](tooltip-overview.md).  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>Criar um pop-up  
 O exemplo a seguir <xref:System.Windows.Controls.Primitives.Popup> mostra como definir um <xref:System.Windows.Controls.Button> controle que é o elemento filho de um controle. Como <xref:System.Windows.Controls.Button> a pode ter apenas um elemento filho, <xref:System.Windows.Controls.Button> este <xref:System.Windows.Controls.Primitives.Popup> exemplo coloca <xref:System.Windows.Controls.StackPanel>o texto para o e os controles em um . O conteúdo <xref:System.Windows.Controls.Primitives.Popup> do aparece <xref:System.Windows.Controls.TextBlock> em um controle, que exibe seu texto em uma <xref:System.Windows.Controls.Button> janela separada que flutua sobre a janela do aplicativo perto do controle relacionado.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>Controles que implementam um pop-up  
 Você pode <xref:System.Windows.Controls.Primitives.Popup> construir controles em outros controles. Os seguintes controles <xref:System.Windows.Controls.Primitives.Popup> implementam o controle para usos específicos:  
  
- <xref:System.Windows.Controls.ToolTip>. Se você quiser criar uma dica de <xref:System.Windows.Controls.ToolTip> ferramenta <xref:System.Windows.Controls.ToolTipService> para um elemento, use o e classes. Para obter mais informações, consulte [Visão geral de ToolTip](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Se você quiser criar um menu de <xref:System.Windows.Controls.ContextMenu> contexto para um elemento, use o controle. Para mais informações, consulte [Visão geral do ContextMenu](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Se você quiser criar um controle de seleção que tenha uma caixa <xref:System.Windows.Controls.ComboBox> de lista parada que possa ser mostrada ou oculta, use o controle.  
  
- <xref:System.Windows.Controls.Expander>. Se você quiser criar um controle que exiba um cabeçalho <xref:System.Windows.Controls.Expander> com uma área dobrável que exibe conteúdo, use o controle. Para mais informações, consulte [Visão geral do expansor](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Aparência e comportamento de pop-up  
 O <xref:System.Windows.Controls.Primitives.Popup> controle fornece funcionalidade que permite personalizar seu comportamento e aparência. Por exemplo, você pode definir efeitos de comportamento aberto e próximo, animação, opacidade e bitmap, e <xref:System.Windows.Controls.Primitives.Popup> tamanho e posição.  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>Comportamento de abertura e fechamento  
 Um <xref:System.Windows.Controls.Primitives.Popup> controle exibe seu <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> conteúdo quando `true`a propriedade é definida como . Por padrão, <xref:System.Windows.Controls.Primitives.Popup> permanece <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> aberto até `false`que a propriedade seja definida como . No entanto, você pode alterar <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> o `false`comportamento padrão definindo a propriedade para . Quando você define `false`esta <xref:System.Windows.Controls.Primitives.Popup> propriedade para , a janela de conteúdo tem captura de mouse. O <xref:System.Windows.Controls.Primitives.Popup> perde a captura do mouse e a <xref:System.Windows.Controls.Primitives.Popup> janela fecha quando um evento do mouse ocorre fora da janela.  
  
 Os <xref:System.Windows.Controls.Primitives.Popup.Opened> <xref:System.Windows.Controls.Primitives.Popup.Closed> eventos são levantados <xref:System.Windows.Controls.Primitives.Popup> quando a janela de conteúdo está aberta ou fechada.  
  
<a name="Animation"></a>
### <a name="animation"></a>Animação  
 O <xref:System.Windows.Controls.Primitives.Popup> controle tem suporte integrado para as animações que são tipicamente associadas a comportamentos como desbotamento e slide-in. Você pode ativar essas animações <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> definindo <xref:System.Windows.Controls.Primitives.PopupAnimation> a propriedade como um valor de enumeração. Para <xref:System.Windows.Controls.Primitives.Popup> que as animações funcionem <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> corretamente, você deve definir a propriedade para `true`.  
  
 Você também pode aplicar <xref:System.Windows.Media.Animation.Storyboard> animações como no <xref:System.Windows.Controls.Primitives.Popup> controle.  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>Efeitos de bitmap e opacidade  
 A <xref:System.Windows.UIElement.Opacity%2A> propriedade <xref:System.Windows.Controls.Primitives.Popup> para um controle não tem efeito sobre seu conteúdo. Por padrão, <xref:System.Windows.Controls.Primitives.Popup> a janela de conteúdo é opaca. Para criar <xref:System.Windows.Controls.Primitives.Popup>uma transparente, defina a <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> propriedade como `true`.  
  
 O conteúdo <xref:System.Windows.Controls.Primitives.Popup> de um não herda <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>efeitos de bitmap, <xref:System.Windows.Controls.Primitives.Popup> tais como, que você defina diretamente no controle ou em qualquer outro elemento na janela pai. Para que os efeitos do bitmap apareçam no conteúdo de a, <xref:System.Windows.Controls.Primitives.Popup>você deve definir o efeito bitmap diretamente em seu conteúdo. Por exemplo, se o <xref:System.Windows.Controls.Primitives.Popup> filho <xref:System.Windows.Controls.StackPanel>de a for um <xref:System.Windows.Controls.StackPanel>, defina o efeito bitmap no .  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Tamanho de pop-up  
 Por padrão, <xref:System.Windows.Controls.Primitives.Popup> a é automaticamente dimensionada para o seu conteúdo. Quando ocorre o dimensionamento automático, alguns efeitos de bitmap podem ser ocultos porque o tamanho padrão da área de tela definida para o <xref:System.Windows.Controls.Primitives.Popup> conteúdo não fornece espaço suficiente para os efeitos do bitmap serem exibidos.  
  
 <xref:System.Windows.Controls.Primitives.Popup>o conteúdo também pode ser <xref:System.Windows.UIElement.RenderTransform%2A> obscurecido quando você define um no conteúdo. Nesse cenário, alguns conteúdos podem ser ocultos se o conteúdo do transformado <xref:System.Windows.Controls.Primitives.Popup> se estender além da área do original. <xref:System.Windows.Controls.Primitives.Popup> Se um efeito ou transformação do bitmap requer <xref:System.Windows.Controls.Primitives.Popup> mais espaço, você pode definir uma margem em torno do conteúdo, a fim de fornecer mais área para o controle.  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>Definindo a posição de pop-up  
 Você pode posicionar um pop-up <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>definindo <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> as <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>propriedades e propriedades. Para mais informações, consulte [Comportamento de posicionamento de pop-up](popup-placement-behavior.md). Quando <xref:System.Windows.Controls.Primitives.Popup> é exibido na tela, ele não se reposiciona se seu pai for reposicionado.  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>Personalizando o posicionamento do pop-up  
 Você pode personalizar a <xref:System.Windows.Controls.Primitives.Popup> colocação de um controle especificando um <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> conjunto de <xref:System.Windows.Controls.Primitives.Popup> coordenadas relativas ao local onde você deseja que ele apareça.  
  
 Para personalizar a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> colocação, defina a propriedade como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Em seguida, defina um <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegado que devolva um conjunto de <xref:System.Windows.Controls.Primitives.Popup>possíveis pontos de colocação e eixos primários (por ordem de preferência) para o . O ponto que mostra a <xref:System.Windows.Controls.Primitives.Popup> maior parte do é automaticamente selecionado. Para ver um exemplo, consulte [Especificar uma posição de pop-up personalizada](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Pop-up e árvore visual  
 Um <xref:System.Windows.Controls.Primitives.Popup> controle não tem sua própria árvore visual; em vez disso, retorna um tamanho <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> de <xref:System.Windows.Controls.Primitives.Popup> 0 (zero) quando o método para é chamado. No entanto, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> quando <xref:System.Windows.Controls.Primitives.Popup> você `true`define a propriedade de , uma nova janela com sua própria árvore visual é criada. A nova janela <xref:System.Windows.Controls.Primitives.Popup.Child%2A> contém <xref:System.Windows.Controls.Primitives.Popup>o conteúdo de . A largura e altura da nova janela não podem ser maiores do que 75 por cento da largura ou altura da tela.  
  
 O <xref:System.Windows.Controls.Primitives.Popup> controle mantém <xref:System.Windows.Controls.Primitives.Popup.Child%2A> uma referência ao seu conteúdo como uma criança lógica. Quando a nova janela é criada, o conteúdo torna-se <xref:System.Windows.Controls.Primitives.Popup> uma criança <xref:System.Windows.Controls.Primitives.Popup>visual da janela e continua a ser a criança lógica de . Por outro <xref:System.Windows.Controls.Primitives.Popup> lado, continua <xref:System.Windows.Controls.Primitives.Popup.Child%2A> sendo o pai lógico de seu conteúdo.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tópicos de como fazer](popup-how-to-topics.md)
- [Tópicos de como fazer](tooltip-how-to-topics.md)
