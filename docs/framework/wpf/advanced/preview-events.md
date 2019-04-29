---
title: Eventos de visualização
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 75165df94aa8b508ef85cf970933efb98b9d62ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772867"
---
# <a name="preview-events"></a>Eventos de visualização
Eventos de Visualização, também conhecidos como eventos de túnel, são eventos roteados em que a direção da rota vai da raiz do aplicativo em direção ao elemento que gerou o evento e é relatado como origem nos dados do evento. Nem todos os cenários de eventos têm suporte ou precisam de eventos de visualização. Este tópico descreve as situações em que os eventos de visualização existem, como aplicativos ou componentes devem lidar com eles e casos em que criar eventos de visualização em componentes ou classes personalizados pode ser apropriado.  
  
## <a name="preview-events-and-input"></a>Eventos de visualização e entrada  
 Quando você lida com eventos de Visualização em geral, tenha cuidado marcação de eventos manipulados nos dados. Manipular um evento de Visualização em qualquer elemento que não o elemento que o gerou (o elemento relatado como origem nos dados do evento) tem o efeito de não fornecer a um elemento a oportunidade de manipular o evento que o originou. Às vezes, esse será o resultado desejado, particularmente se os elementos em questão existirem em relacionamentos dentro da composição de um controle.  
  
 Especificamente para eventos de entrada, eventos de Visualização também compartilham instâncias de dados de evento com o evento de propagação equivalente. Se você usar um manipulador de classe de evento de Visualização para marcar o evento de entrada manipulado, o manipulador de classe de evento de entrada de propagação não será invocado. Ou, se você usar um manipulador de instância de evento de Visualização para marcar o evento manipulado, os manipuladores para o evento de propagação normalmente não serão invocados. Manipuladores de classe ou manipuladores de instância podem ser registrados ou anexados com uma opção a ser invocada mesmo que o evento esteja marcado como manipulado, mas essa técnica não costuma ser usada.  
  
 Para obter mais informações sobre manipulação de classes e como ela se relaciona a eventos de Visualização, consulte [Marcando eventos roteados como manipulados e manipulação de classe](marking-routed-events-as-handled-and-class-handling.md).  
  
### <a name="working-around-event-suppression-by-controls"></a>Resolvendo a supressão de eventos por controles  
 Um cenário em que os eventos de Visualização são comumente usados é a manipulação de controles compostos de eventos de entrada. Às vezes, o autor do controle suprime a criação de um determinado evento em seu controle, talvez para substituir um evento definido por componente que carrega mais informações ou implica um comportamento mais específico. Por exemplo, uma [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> suprime <xref:System.Windows.UIElement.MouseLeftButtonDown> e <xref:System.Windows.UIElement.MouseRightButtonDown> eventos levantados pelo <xref:System.Windows.Controls.Button> ou seus elementos compostos em favor da captura de mouse e gerando um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos que sempre é gerado pelo <xref:System.Windows.Controls.Button> em si. O evento e seus dados continuam ao longo da rota, mas, como o <xref:System.Windows.Controls.Button> marca os dados de evento como <xref:System.Windows.RoutedEventArgs.Handled%2A>, somente os manipuladores para o evento que indicou especificamente que eles devem agir na `handledEventsToo` caso são invocados.  Se outros elementos na direção da raiz do seu aplicativo ainda quiserem ter uma oportunidade de lidar com um evento suprimido por controle, uma alternativa será anexar manipuladores ao código com `handledEventsToo` especificado como `true`. Porém, geralmente, uma técnica simples é alterar a direção de roteamento que você processa para que seja equivalente à de uma Visualização de um evento de entrada. Por exemplo, se um controle suprime <xref:System.Windows.UIElement.MouseLeftButtonDown>, tente anexar um manipulador para <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> em vez disso. Essa técnica funciona somente para eventos de entrada do elemento base, como <xref:System.Windows.UIElement.MouseLeftButtonDown>. Esses eventos de entrada usam pares de túnel/bolha, geram ambos os eventos e compartilham os dados do evento.  
  
 Cada uma dessas técnicas tem efeitos colaterais ou limitações. O efeito colateral de manipular o evento de Visualização é que manipular o evento nesse ponto pode desabilitar manipuladores que esperam manipular o evento de propagação e, portanto, a limitação é que geralmente não é uma boa ideia marcar o evento como manipulado enquanto ele ainda está na parte de Visualização da rota. A limitação da técnica `handledEventsToo` é que você não pode especificar um manipulador `handledEventsToo` em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] como um atributo, é preciso registrar o manipulador de eventos no código depois de obter uma referência de objeto para o elemento ao qual o manipulador será anexado.  
  
## <a name="see-also"></a>Consulte também

- [Marcando eventos roteados como manipulados e tratamento de classes](marking-routed-events-as-handled-and-class-handling.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
