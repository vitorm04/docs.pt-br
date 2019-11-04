---
title: Estilos para foco em controles e FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 988b084144532df6f7a6073184fcf035b0813bfd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458685"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Estilos para foco em controles e FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece dois mecanismos paralelos para alterar a aparência visual de um controle quando ele recebe o foco do teclado. O primeiro mecanismo é usar setters de propriedade para propriedades como <xref:System.Windows.UIElement.IsKeyboardFocused%2A> dentro do estilo ou modelo que é aplicado ao controle. O segundo mecanismo é fornecer um estilo separado como o valor da propriedade <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>; o "estilo visual de foco" cria uma árvore visual separada para um adorno que se baseia no controle, em vez de alterar a árvore visual do controle ou outro elemento de interface do usuário, substituindo-o. Este tópico aborda os cenários em que cada um desses mecanismos é apropriado.  

<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>O objetivo do estilo visual de foco  
 O recurso de estilo visual de foco fornece um "modelo de objeto" comum para introduzir comentários visuais do usuário com base em navegação de teclado para qualquer elemento de interface do usuário. Isso é possível sem a aplicação de um novo modelo para o controle ou conhecendo a composição do modelo específico.  
  
 No entanto, como o recurso de estilo visual de foco funciona sem conhecer os modelos de controle, os comentários visuais que pode ser exibido para um controle usando um estilo visual de foco é necessariamente limitado. O que o recurso realmente faz é sobrepor uma árvore visual diferente (um adorno) na parte superior da árvore visual conforme criado por uma renderização de controle pelo modelo. Você define essa árvore visual separada usando um estilo que preenche a propriedade <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Comportamento de estilo visual de foco padrão  
 Os estilos visuais de foco funcionam apenas quando a ação do foco foi iniciada pelo teclado. Qualquer ação do mouse ou alteração de foco por programação desabilita o modo de estilos visuais de foco. Para obter mais informações sobre as distinções entre os modos de foco, consulte [Visão geral do foco](focus-overview.md).  
  
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
  
 A definição de <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> em estilos de controle individuais que não fazem parte de um tema não é o uso pretendido de estilos visuais de foco. Isso ocorre porque um comportamento visual inconsistente entre controles pode levar a uma experiência confusa do usuário em relação ao foco do teclado. Se você estiver pretendendo comportamentos específicos de controle para o foco do teclado que são deliberadamente não coerentes em um tema, uma abordagem muito melhor é usar gatilhos em estilos para propriedades de estado de entrada individuais, como <xref:System.Windows.UIElement.IsFocused%2A> ou <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Estilos visuais de foco agem exclusivamente para foco do teclado. Dessa forma, estilos visuais de foco são um tipo de recurso de acessibilidade. Se quiser alterações de interface do usuário para qualquer tipo de foco, seja por meio de mouse, teclado ou programaticamente, então você não deverá usar estilos visuais de foco e, em vez disso, deverá usar setters e disparadores nos estilos ou modelos que estão funcionando do valor das propriedades de foco gerais, como <xref:System.Windows.UIElement.IsFocused%2A> ou <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Como criar um estilo visual de foco  
 O estilo que você cria para um estilo visual de foco sempre deve ter a <xref:System.Windows.Style.TargetType%2A> de <xref:System.Windows.Controls.Control>. O estilo deve consistir principalmente em um <xref:System.Windows.Controls.ControlTemplate>. Você não especifica o tipo de destino para ser o tipo em que o estilo visual de foco é atribuído à <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Como o tipo de destino é sempre <xref:System.Windows.Controls.Control>, você deve estilizar usando propriedades que são comuns a todos os controles (usando as propriedades da classe <xref:System.Windows.Controls.Control> e suas classes base). Você deve criar um modelo que funcionará corretamente como uma sobreposição para um elemento de interface do usuário e que não ocultará áreas funcionais do controle. Em geral, isso significa que os comentários visuais devem aparecer fora das margens do controle ou como efeitos temporários ou discretos que não bloquearão o teste de clique no controle no qual o estilo visual de foco é aplicado. As propriedades que você pode usar na associação de modelo que são úteis para determinar o dimensionamento e o posicionamento do seu modelo de sobreposição incluem <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>e <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternativas ao uso de um estilo visual de foco  
 Para situações em que usar um estilo visual de foco não é apropriado, porque você está estilizando apenas controles únicos ou porque deseja maior controle em relação ao modelo de controle, há muitas outras propriedades acessíveis e técnicas que podem criar comportamento visual em resposta às alterações no foco.  
  
 Os gatilhos, os setters e os setters de evento são discutidos em detalhes em [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md). A manipulação de eventos roteados é discutida em [Visão geral de eventos roteados](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Se você estiver interessado especificamente no foco do teclado, a propriedade de dependência <xref:System.Windows.UIElement.IsKeyboardFocused%2A> poderá ser usada para uma propriedade <xref:System.Windows.Trigger>. Um gatilho de propriedade em um estilo ou modelo é uma técnica mais apropriada para definir um comportamento de foco do teclado que é especificamente para um único controle e que pode não corresponder visualmente ao comportamento de foco do teclado para outros controles.  
  
 Outra propriedade de dependência semelhante é <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, que pode ser apropriada para ser usada se você quiser destacar visualmente que o foco do teclado está em algum lugar dentro da composição ou dentro da área funcional do controle. Por exemplo, você pode posicionar um gatilho <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> de modo que um painel que agrupa vários controles apareça de forma diferente, mesmo que o foco do teclado possa estar mais precisamente em um elemento individual dentro desse painel.  
  
 Você também pode usar os eventos <xref:System.Windows.UIElement.GotKeyboardFocus> e <xref:System.Windows.UIElement.LostKeyboardFocus> (bem como seus equivalentes de visualização). Você pode usar esses eventos como base para um <xref:System.Windows.EventSetter>, ou você pode escrever manipuladores para os eventos no code-behind.  
  
### <a name="other-focus-properties"></a>Outras propriedades de foco  
 Se você quiser todas as possíveis causas da alteração do foco para produzir um comportamento visual, deverá basear um Setter ou gatilho na propriedade de dependência <xref:System.Windows.UIElement.IsFocused%2A> ou, como alternativa, nos eventos <xref:System.Windows.UIElement.GotFocus> ou <xref:System.Windows.UIElement.LostFocus> usados para um <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Visão geral do foco](focus-overview.md)
- [Visão geral da entrada](input-overview.md)
