---
title: Como renderizar em um intervalo por quadro usando CompositionTarget
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: cc043e6d225ad3dbe57a0924593fac0f68af7eb1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526435"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Como renderizar em um intervalo por quadro usando CompositionTarget
O mecanismo de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece vários recursos para criar animações baseadas em quadros. No entanto, há cenários de aplicativo em que é necessário um controle mais refinado da renderização por quadro. O <xref:System.Windows.Media.CompositionTarget> objeto fornece a capacidade de criar animações personalizadas com base em um retorno de chamada por quadro.  
  
 <xref:System.Windows.Media.CompositionTarget> é uma classe estática que representa a superfície de exibição em que seu aplicativo está sendo desenhado. O <xref:System.Windows.Media.CompositionTarget.Rendering> evento é gerado toda vez que cena do aplicativo é desenhada. A taxa de quadros de renderização é o número de vezes que a cena é desenhada por segundo.  
  
> [!NOTE]
>  Para obter um exemplo de código completo usando <xref:System.Windows.Media.CompositionTarget>, consulte [usando o exemplo CompositionTarget](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.CompositionTarget.Rendering> evento é acionado durante a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processo de renderização. O exemplo a seguir mostra como registrar um <xref:System.EventHandler> delegar para estático <xref:System.Windows.Media.CompositionTarget.Rendering> método em <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 É possível usar o método de manipulador de eventos de renderização para criar conteúdo de personalizado de desenho. Esse método de manipulador de eventos é chamado uma vez por quadro. Toda vez que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realizar marshaling dos dados persistentes de renderização na árvore visual para o grafo de cena de composição, o método de manipulador de eventos será chamados. Além disso, se as alterações na árvore visual forçarem atualizações no grafo de cena de composição, o método de manipulador de eventos também será chamado. Observe que o método de manipulador de eventos será chamado após o cálculo do layout. No entanto, é possível modificar o layout no método de manipulador de eventos, o que significa que o layout será calculado mais uma vez antes da renderização.  
  
 O exemplo a seguir mostra como você pode fornecer desenhos personalizados em um <xref:System.Windows.Media.CompositionTarget> método manipulador de eventos. Nesse caso, a cor de fundo a <xref:System.Windows.Controls.Canvas> é desenhada com um valor de cor com base na posição da coordenada do mouse. Se você mover o mouse dentro a <xref:System.Windows.Controls.Canvas>, suas alterações de cor do plano de fundo. Além disso, a taxa de quadros média será calculada, com base no tempo decorrido atual e no número total de quadros renderizados.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Você pode descobrir que seu desenho personalizado é executado em velocidades distintas em computadores diferentes. Isso ocorre porque seu desenho personalizado não independe da taxa de quadros. Dependendo do sistema estiver executando e a carga de trabalho do sistema, o <xref:System.Windows.Media.CompositionTarget.Rendering> evento pode ser chamado como um número diferente de vezes por segundo. Para obter informações sobre como determinar a capacidade de hardware de gráficos e o desempenho de um dispositivo que executa um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Camadas de Renderização de Gráficos](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 Adicionando ou removendo uma renderização <xref:System.EventHandler> delegado enquanto o evento está disparando será adiado até depois que o evento tenha terminado de acionamento. Isso é consistente com como <xref:System.MulticastDelegate>-eventos com base são manipulados no tempo de execução do CLR (Common Language). Observe também que não há uma garantia de que os eventos de renderização serão chamados em uma ordem específica. Se você tiver vários <xref:System.EventHandler> delegados que se baseiam em uma ordem específica, você deve registrar um único <xref:System.Windows.Media.CompositionTarget.Rendering> eventos e multiplexar os delegados no item correto ordem por conta própria.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.CompositionTarget>  
 [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
