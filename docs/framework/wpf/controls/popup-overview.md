---
title: Visão geral do pop-up
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 53283619d1bd2727bdca1df6a3a408ec0ce873a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625702"
---
# <a name="popup-overview"></a>Visão geral do pop-up
O <xref:System.Windows.Controls.Primitives.Popup> controle fornece uma maneira de exibir o conteúdo em uma janela separada que flutua sobre a janela do aplicativo atual em relação a um elemento designado ou tela coordenada. Este tópico apresenta o <xref:System.Windows.Controls.Primitives.Popup> controlar e fornece informações sobre seu uso.  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>O que é um pop-up?  
 Um <xref:System.Windows.Controls.Primitives.Popup> controle exibe conteúdo em uma janela separada em relação a um elemento ou ponto na tela. Quando o <xref:System.Windows.Controls.Primitives.Popup> estiver visível, o <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> estiver definida como `true`.  
  
> [!NOTE]
>  Um <xref:System.Windows.Controls.Primitives.Popup> não abre automaticamente quando o ponteiro do mouse se move sobre seu objeto pai. Se você quiser que um <xref:System.Windows.Controls.Primitives.Popup> para abrir automaticamente, use o <xref:System.Windows.Controls.ToolTip> ou <xref:System.Windows.Controls.ToolTipService> classe. Para obter mais informações, consulte [Visão geral de ToolTip](tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Criar um pop-up  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.Primitives.Popup> controle que é o elemento filho de um <xref:System.Windows.Controls.Button> controle. Porque uma <xref:System.Windows.Controls.Button> pode ter apenas um elemento filho, este exemplo coloca o texto para o <xref:System.Windows.Controls.Button> e o <xref:System.Windows.Controls.Primitives.Popup> controles em um <xref:System.Windows.Controls.StackPanel>. O conteúdo do <xref:System.Windows.Controls.Primitives.Popup> aparece em uma <xref:System.Windows.Controls.TextBlock> controle, que exibe seu texto em uma janela separada que flutua sobre a janela do aplicativo próximo relacionado <xref:System.Windows.Controls.Button> controle.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Controles que implementam um pop-up  
 Você pode criar <xref:System.Windows.Controls.Primitives.Popup> controles em outros controles. Os seguintes controles implementam o <xref:System.Windows.Controls.Primitives.Popup> controle para usos específicos:  
  
- <xref:System.Windows.Controls.ToolTip>. Se você quiser criar uma dica de ferramenta para um elemento, use o <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ToolTipService> classes. Para obter mais informações, consulte [Visão geral de ToolTip](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Se você quiser criar um menu de contexto para um elemento, use o <xref:System.Windows.Controls.ContextMenu> controle. Para mais informações, consulte [Visão geral do ContextMenu](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Se você quiser criar um controle de seleção que tenha uma caixa de lista suspensa que pode ser mostrado ou oculto, use o <xref:System.Windows.Controls.ComboBox> controle.  
  
- <xref:System.Windows.Controls.Expander>. Se você quiser criar um controle que exibe um cabeçalho com uma área recolhível que exibe conteúdo, use o <xref:System.Windows.Controls.Expander> controle. Para mais informações, consulte [Visão geral do expansor](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Aparência e comportamento de pop-up  
 O <xref:System.Windows.Controls.Primitives.Popup> controle fornece a funcionalidade que permite que você personalize sua aparência e comportamento. Por exemplo, você pode definir o comportamento de aberto e fechamento, animação, efeitos de opacidade e bitmap, e <xref:System.Windows.Controls.Primitives.Popup> tamanho e posição.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Comportamento de abertura e fechamento  
 Um <xref:System.Windows.Controls.Primitives.Popup> controle exibe seu conteúdo quando o <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> estiver definida como `true`. Por padrão, <xref:System.Windows.Controls.Primitives.Popup> permanece aberta até que o <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> estiver definida como `false`. No entanto, você pode alterar o comportamento padrão definindo a <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> propriedade para `false`. Quando você define essa propriedade como `false`, o <xref:System.Windows.Controls.Primitives.Popup> janela de conteúdo tem captura do mouse. O <xref:System.Windows.Controls.Primitives.Popup> perde mouse captura e a janela fecha quando ocorre um evento de mouse fora o <xref:System.Windows.Controls.Primitives.Popup> janela.  
  
 O <xref:System.Windows.Controls.Primitives.Popup.Opened> e <xref:System.Windows.Controls.Primitives.Popup.Closed> eventos são gerados quando o <xref:System.Windows.Controls.Primitives.Popup> janela de conteúdo é aberto ou fechado.  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animação  
 O <xref:System.Windows.Controls.Primitives.Popup> controle tem suporte interno para as animações que são normalmente associadas a comportamentos como deslizamento e no slide. Você pode ativar essas animações definindo a <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> propriedade para um <xref:System.Windows.Controls.Primitives.PopupAnimation> valor de enumeração. Para <xref:System.Windows.Controls.Primitives.Popup> animações funcione corretamente, você deve definir o <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> propriedade `true`.  
  
 Você também pode aplicar animações, como <xref:System.Windows.Media.Animation.Storyboard> para o <xref:System.Windows.Controls.Primitives.Popup> controle.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Efeitos de bitmap e opacidade  
 O <xref:System.Windows.UIElement.Opacity%2A> propriedade para um <xref:System.Windows.Controls.Primitives.Popup> controle não tem nenhum efeito em seu conteúdo. Por padrão, o <xref:System.Windows.Controls.Primitives.Popup> janela de conteúdo é opaca. Para criar um transparente <xref:System.Windows.Controls.Primitives.Popup>, defina a <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> propriedade `true`.  
  
 O conteúdo de um <xref:System.Windows.Controls.Primitives.Popup> não herda efeitos de bitmap, como <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, que você defina diretamente no <xref:System.Windows.Controls.Primitives.Popup> controle ou em qualquer outro elemento na janela pai. Para efeitos de bitmap serem exibidos no conteúdo de um <xref:System.Windows.Controls.Primitives.Popup>, você deve definir o efeito de bitmap diretamente em seu conteúdo. Por exemplo, se o filho de um <xref:System.Windows.Controls.Primitives.Popup> é um <xref:System.Windows.Controls.StackPanel>, defina o efeito de bitmap no <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Tamanho de pop-up  
 Por padrão, um <xref:System.Windows.Controls.Primitives.Popup> é dimensionado automaticamente ao seu conteúdo. Quando o dimensionamento automático ocorre, alguns efeitos de bitmap podem estar ocultos porque o tamanho padrão da área da tela que está definido para o <xref:System.Windows.Controls.Primitives.Popup> conteúdo não fornece espaço suficiente para os efeitos de bitmap serem exibidos.  
  
 <xref:System.Windows.Controls.Primitives.Popup> conteúdo também podem ficar obscuros quando você define um <xref:System.Windows.UIElement.RenderTransform%2A> no conteúdo. Nesse cenário, alguns conteúdos podem estar ocultos se o conteúdo transformado <xref:System.Windows.Controls.Primitives.Popup> ultrapassa a área do original <xref:System.Windows.Controls.Primitives.Popup>. Se um efeito de bitmap ou transformação requer mais espaço, você pode definir uma margem ao redor de <xref:System.Windows.Controls.Primitives.Popup> conteúdo para fornecer mais área para o controle.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Definindo a posição de pop-up  
 Você pode posicionar um pop-up, definindo o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> propriedades. Para mais informações, consulte [Comportamento de posicionamento de pop-up](popup-placement-behavior.md). Quando <xref:System.Windows.Controls.Primitives.Popup> é exibido na tela, ele não se reposicionará o pai estiver reposicionado.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Personalizando o posicionamento do pop-up  
 Você pode personalizar o posicionamento de um <xref:System.Windows.Controls.Primitives.Popup> controle especificando um conjunto de coordenadas que são relativas a <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> onde você deseja que o <xref:System.Windows.Controls.Primitives.Popup> seja exibido.  
  
 Para personalizar o posicionamento, defina as <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade para <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Em seguida, defina uma <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegado que retorna um conjunto de pontos possíveis para posicionamento e eixos principais (em ordem de preferência) para o <xref:System.Windows.Controls.Primitives.Popup>. O ponto que mostra a maior parte do <xref:System.Windows.Controls.Primitives.Popup> é selecionado automaticamente. Para ver um exemplo, consulte [Especificar uma posição de pop-up personalizada](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Pop-up e árvore visual  
 Um <xref:System.Windows.Controls.Primitives.Popup> controle não tem sua própria árvore visual; em vez disso, ele retorna um tamanho de 0 (zero) quando o <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> método para <xref:System.Windows.Controls.Primitives.Popup> é chamado. No entanto, quando você define o <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> propriedade de <xref:System.Windows.Controls.Primitives.Popup> para `true`, uma nova janela com sua própria árvore visual é criada. A nova janela contém o <xref:System.Windows.Controls.Primitives.Popup.Child%2A> conteúdo do <xref:System.Windows.Controls.Primitives.Popup>. A largura e altura da nova janela não podem ser maiores do que 75 por cento da largura ou altura da tela.  
  
 O <xref:System.Windows.Controls.Primitives.Popup> controle mantém uma referência ao seu <xref:System.Windows.Controls.Primitives.Popup.Child%2A> conteúdo como um filho lógico. Quando a nova janela é criado, o conteúdo do <xref:System.Windows.Controls.Primitives.Popup> se torna um filho visual da janela e mantém o filho lógico de <xref:System.Windows.Controls.Primitives.Popup>. Por outro lado, <xref:System.Windows.Controls.Primitives.Popup> mantém o pai lógico do seu <xref:System.Windows.Controls.Primitives.Popup.Child%2A> conteúdo.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tópicos de instruções](popup-how-to-topics.md)
- [Tópicos de instruções](tooltip-how-to-topics.md)
