---
title: O modelo de threading da tinta
ms.date: 03/30/2017
helpviewer_keywords:
- application user interface thread [WPF]
- stylus plug-in
- ink threading model [WPF]
- ink [WPF], rendering
- pen thread [WPF]
- threading model [WPF]
- rendering ink [WPF]
- dynamic rendering thread [WPF]
- ink collection plug-in
- plug-ins [WPF], for ink
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
ms.openlocfilehash: cc0ff8a2345bd945dd2fffdfda80f00e1ab99c67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="the-ink-threading-model"></a>O modelo de threading da tinta
Um dos benefícios da tinta em um Tablet PC é que ela se parece muito com escrever com uma caneta comum e papel.  Para fazer isso, a caneta eletrônica coleta dados de entrada a uma taxa muito maior do que um mouse e renderiza a tinta enquanto o usuário escreve.  O thread da interface do usuário do aplicativo não é suficiente para coletar dados da caneta e renderizar a tinta, porque ele pode ser bloqueado.  Para resolver isso, um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa dois threads adicionais quando um usuário escreve com tinta.  
  
 A lista a seguir descreve os threads que fazem parte da coleta e renderização da tinta digital:  
  
-   Thread de caneta – o thread que coleta dados da caneta.  (Na realidade, trata-se de um pool de threads, mas este tópico refere-se a ele como um thread de caneta.)  
  
-   Thread da interface do usuário do aplicativo – o thread que controla a interface do usuário do aplicativo.  
  
-   Thread de renderização dinâmica – o thread que renderiza a tinta enquanto o usuário desenha um traço. O thread de renderização dinâmica é diferente do thread que renderiza outros elementos da interface do usuário para o aplicativo, conforme mencionado no [Modelo de threading](../../../../docs/framework/wpf/advanced/threading-model.md) da Windows Presentation Foundation.  
  
 O modelo de tinta é o mesmo se o aplicativo usa o <xref:System.Windows.Controls.InkCanvas> ou um controle personalizado semelhante àquele [criando um controle de entrada de tinta](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  Embora este tópico discute threading em termos do <xref:System.Windows.Controls.InkCanvas>, os mesmos conceitos se aplicam quando você cria um controle personalizado.  
  
## <a name="threading-overview"></a>Visão geral do threading  
 O diagrama a seguir ilustra o modelo de threading quando um usuário desenha um traço:  
  
 ![Modelo de threading ao desenhar um traço. ] (../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1.  Ações que ocorrem enquanto o usuário desenha o traço  
  
    1.  Quando o usuário desenha um traço, os pontos da caneta entram no thread da caneta.  Plug-ins de caneta, incluindo o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, aceite os pontos de caneta no thread de caneta e terá a chance de modificá-las antes do <xref:System.Windows.Controls.InkCanvas> recebe.  
  
    2.  O <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderiza os pontos de caneta no thread de processamento dinâmico. Isso acontece ao mesmo tempo em que a etapa anterior.  
  
    3.  O <xref:System.Windows.Controls.InkCanvas> recebe os pontos de caneta no thread da interface do usuário.  
  
2.  Ações que ocorrem após o usuário terminar o traço  
  
    1.  Quando o usuário termina o traço de desenho a <xref:System.Windows.Controls.InkCanvas> cria um <xref:System.Windows.Ink.Stroke> e o adiciona ao <xref:System.Windows.Controls.InkPresenter>, que é processada estaticamente.  
  
    2.  Os alertas de thread de interface do usuário a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> que o traço é estaticamente renderizado, portanto, o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> remove sua representação visual do traço.  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>Plug-ins de caneta e coleta de tinta  
 Cada <xref:System.Windows.UIElement> tem um <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  O <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objetos no <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> recebem e podem modificar os pontos de caneta no thread de caneta. O <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objetos recebem os pontos de caneta de acordo com sua ordem no <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  
  
 O diagrama a seguir ilustra a situação hipotética onde o <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção de um <xref:System.Windows.UIElement> contém `stylusPlugin1`, um <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, e `stylusPlugin2`, nessa ordem.  
  
 ![Ordem dos plug-ins da caneta afeta a saída. ] (../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 No diagrama anterior, o seguinte comportamento ocorre:  
  
1.  `StylusPlugin1` modifica os valores de x e y.  
  
2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> recebe os pontos de caneta modificados e renderiza-os no thread de processamento dinâmico.  
  
3.  `StylusPlugin2` recebe os pontos da caneta modificados e modifica mais os valores de x e y.  
  
4.  O aplicativo coleta os pontos da caneta e, quando o usuário termina o traço, renderiza estaticamente o traço.  
  
 Suponha que `stylusPlugin1` restrinja os pontos da caneta a um retângulo e `stylusPlugin2` mova os pontos da caneta para a direita.  No cenário anterior, o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> recebe os pontos de caneta restrito, mas não os pontos de caneta traduzidos.  Quando o usuário desenha o traço, o traço é renderizado dentro dos limites do retângulo, mas o traço não parece ser movido até que o usuário levante a caneta.  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>Executando operações com um plug-in de caneta no thread da interface do usuário  
 Como testes de acertos precisos não podem ser executados no thread da caneta, alguns elementos podem, ocasionalmente, receber entradas da caneta destinadas a outros elementos. Se você precisar certificar-se de que a entrada foi roteada corretamente antes de executar uma operação, assine e execute a operação no <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, ou <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> método. Esses métodos são invocados pelo thread do aplicativo após testes de acertos precisos terem sido executados. Para assinar esses métodos, chame o <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> método no método que ocorre no thread de caneta.  
  
 O diagrama a seguir ilustra o relacionamento entre o encadeamento de caneta e o thread de interface do usuário em relação a eventos caneta de um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.  
  
 ![Modelos de threading de tinta &#40;interface do usuário e caneta&#41;](../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>Renderizando tinta  
 Assim que o usuário desenha um traço, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderiza a tinta em um thread separado, para que a tinta pareça "fluir" a partir da caneta, mesmo quando o thread de interface do usuário estiver ocupado.  O <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cria uma árvore visual no thread de processamento dinâmico assim que ele coleta pontos de caneta.  Quando o usuário termina de traço, o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> pede para ser notificado quando o aplicativo faz o próximo passo de renderização.  Após o aplicativo concluir a próxima passagem de renderização, o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> limpa sua árvore visual.  O diagrama a seguir ilustra esse processo.  
  
 ![Diagrama de threading de tinta](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1.  O usuário inicia o traço.  
  
    1.  O <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cria a árvore visual.  
  
2.  O usuário está desenhando o traço.  
  
    1.  O <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cria a árvore visual.  
  
3.  O usuário termina o traço.  
  
    1.  O <xref:System.Windows.Controls.InkPresenter> adiciona o traço à sua árvore visual.  
  
    2.  A MIL (camada de integração de mídia) renderiza estaticamente os traços.  
  
    3.  O <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> limpa os elementos visuais.
