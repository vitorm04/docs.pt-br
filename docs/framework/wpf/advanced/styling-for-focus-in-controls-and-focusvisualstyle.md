---
title: Estilos para foco em controles e FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 07dd5f015624e934ceb4fd38f23f7e780d185dfc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672625"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Estilos para foco em controles e FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece dois mecanismos paralelos para alterar a aparência visual de um controle quando ele recebe o foco do teclado. O primeiro mecanismo é usar setters de propriedade para propriedades como <xref:System.Windows.UIElement.IsKeyboardFocused%2A> dentro do estilo ou modelo que é aplicado ao controle. O segundo mecanismo é fornecer um estilo separado como o valor do <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> propriedade; o "estilo visual de foco" cria uma árvore visual separada para um adorno que é desenhado na parte superior do controle, em vez de alterar a árvore visual do controle ou outra interface de usuário elemento ao substituí-la. Este tópico aborda os cenários em que cada um desses mecanismos é apropriado.  
   
  
<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>O objetivo do estilo visual de foco  
 O recurso de estilo visual de foco fornece um "modelo de objeto" comum para introduzir comentários visuais do usuário com base em navegação de teclado para qualquer elemento de interface do usuário. Isso é possível sem a aplicação de um novo modelo para o controle ou conhecendo a composição do modelo específico.  
  
 No entanto, como o recurso de estilo visual de foco funciona sem conhecer os modelos de controle, os comentários visuais que pode ser exibido para um controle usando um estilo visual de foco é necessariamente limitado. O que o recurso realmente faz é sobrepor uma árvore visual diferente (um adorno) na parte superior da árvore visual conforme criado por uma renderização de controle pelo modelo. Você define esta árvore visual separado usando um estilo que preenche o <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> propriedade.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Comportamento de estilo visual de foco padrão  
 Os estilos visuais de foco funcionam apenas quando a ação do foco foi iniciada pelo teclado. Qualquer ação do mouse ou alteração de foco por programação desabilita o modo de estilos visuais de foco. Para obter mais informações sobre as distinções entre os modos de foco, consulte [Visão geral do foco](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
 Os temas dos controles incluem um comportamento de estilo visual de foco padrão que se torna o estilo visual de foco para todos os controles no tema. Esse estilo de tema é identificado pelo valor da chave estática <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Ao declarar seu próprio estilo visual de foco no nível do aplicativo, você pode substituir esse comportamento de estilo padrão dos temas. Como alternativa, se você definir o tema inteiro, deverá usar essa mesma chave para definir o estilo para o comportamento padrão para o tema inteiro.  
  
 Nos temas, o estilo visual de foco padrão é geralmente muito simples. A seguir está uma aproximação grosseira:  
  
```xaml  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>   
## <a name="when-to-use-focus-visual-styles"></a>Quando usar estilos visuais de foco  
 Conceitualmente, a aparência dos estilos visuais de foco aplicados aos controles deve ser coerente de controle para controle. Uma maneira de garantir coerência é alterar o estilo visual de foto somente se você estiver compondo um tema inteiro, em que cada controle que está definido no tema obtém o mesmo estilo visual de foco ou alguma variação de um estilo que está relacionado visualmente de controle para controle. Como alternativa, você pode usar o mesmo estilo (ou estilos semelhantes) para estilizar cada elemento com foco no teclado em uma página ou em uma interface do usuário.  
  
 Definindo <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> nos estilos de controle individuais que não fazem parte de um tema é não o uso pretendido do foco estilos visuais. Isso ocorre porque um comportamento visual inconsistente entre controles pode levar a uma experiência confusa do usuário em relação ao foco do teclado. Se você estiver pretendendo comportamentos de controle específicos para o foco do teclado que são deliberadamente não coerentes em um tema, uma abordagem muito melhor é usar gatilhos em estilos para propriedades de estado de entrada individual, como <xref:System.Windows.UIElement.IsFocused%2A> ou <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Estilos visuais de foco agem exclusivamente para foco do teclado. Dessa forma, estilos visuais de foco são um tipo de recurso de acessibilidade. Se quiser alterações de interface do usuário para qualquer tipo de foco, seja por meio de mouse, teclado ou programaticamente, então você não deverá usar estilos visuais de foco e, em vez disso, deverá usar setters e disparadores nos estilos ou modelos que estão funcionando do valor das propriedades de foco gerais, como <xref:System.Windows.UIElement.IsFocused%2A> ou <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Como criar um estilo visual de foco  
 O estilo que você criar para um estilo visual de foco sempre deve ter o <xref:System.Windows.Style.TargetType%2A> de <xref:System.Windows.Controls.Control>. O estilo deve consistir principalmente de uma <xref:System.Windows.Controls.ControlTemplate>. Você não especificar o tipo de destino para ser do tipo onde o estilo visual de foco é atribuído ao <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Como o tipo de destino é sempre <xref:System.Windows.Controls.Control>, você deverá estilizar usando as propriedades que são comuns a todos os controles (usando propriedades do objeto a <xref:System.Windows.Controls.Control> classe e suas classes base). Você deve criar um modelo que funcionará corretamente como uma sobreposição para um elemento de interface do usuário e que não ocultará áreas funcionais do controle. Em geral, isso significa que os comentários visuais devem aparecer fora das margens do controle ou como efeitos temporários ou discretos que não bloquearão o teste de clique no controle no qual o estilo visual de foco é aplicado. As propriedades que você pode usar na associação de modelo que são úteis para determinar dimensionamento e posicionamento do seu modelo de sobreposição incluem <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, e <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternativas ao uso de um estilo visual de foco  
 Para situações em que usar um estilo visual de foco não é apropriado, porque você está estilizando apenas controles únicos ou porque deseja maior controle em relação ao modelo de controle, há muitas outras propriedades acessíveis e técnicas que podem criar comportamento visual em resposta às alterações no foco.  
  
 Os gatilhos, os setters e os setters de evento são discutidos em detalhes em [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md). A manipulação de eventos roteados é discutida em [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Se você estiver interessado especificamente em foco do teclado, o <xref:System.Windows.UIElement.IsKeyboardFocused%2A> propriedade de dependência pode ser usada para uma propriedade <xref:System.Windows.Trigger>. Um gatilho de propriedade em um estilo ou modelo é uma técnica mais apropriada para definir um comportamento de foco do teclado que é especificamente para um único controle e que pode não corresponder visualmente ao comportamento de foco do teclado para outros controles.  
  
 Outra propriedade de dependência semelhante é <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, que pode ser apropriada a ser usada se você deseja chamar visualmente o foco do teclado está em algum lugar dentro de composição ou dentro da área funcional do controle. Por exemplo, você pode colocar um <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> gatilho, de modo que um painel que agrupa vários controles apareça de maneira diferente, mesmo que o foco do teclado possa com mais precisão estar em um elemento individual dentro desse painel.  
  
 Você também pode usar os eventos <xref:System.Windows.UIElement.GotKeyboardFocus> e <xref:System.Windows.UIElement.LostKeyboardFocus> (bem como seus equivalentes de visualização). Você pode usar esses eventos como base para um <xref:System.Windows.EventSetter>, ou você pode escrever manipuladores para os eventos no code-behind.  
  
### <a name="other-focus-properties"></a>Outras propriedades de foco  
 Se desejar que todas as possíveis causas de alteração de foco para produzir um comportamento visual, você deve basear um setter ou gatilho a <xref:System.Windows.UIElement.IsFocused%2A> propriedade de dependência, ou como alternativa na <xref:System.Windows.UIElement.GotFocus> ou <xref:System.Windows.UIElement.LostFocus> eventos utilizados para um <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Visão geral do foco](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)
