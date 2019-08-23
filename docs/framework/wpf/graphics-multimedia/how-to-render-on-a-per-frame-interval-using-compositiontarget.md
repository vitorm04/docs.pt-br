---
title: 'Como: Renderizar em um intervalo por quadro usando CompositionTarget'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 8864204ccdd1e860cc910dfe8baa2f25edfb2fcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956979"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Como: Renderizar em um intervalo por quadro usando CompositionTarget
O mecanismo de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece vários recursos para criar animações baseadas em quadros. No entanto, há cenários de aplicativo em que é necessário um controle mais refinado da renderização por quadro. O <xref:System.Windows.Media.CompositionTarget> objeto fornece a capacidade de criar animações personalizadas com base em um retorno de chamada por quadro.  
  
 <xref:System.Windows.Media.CompositionTarget>é uma classe estática que representa a superfície de exibição na qual seu aplicativo está sendo desenhado. O <xref:System.Windows.Media.CompositionTarget.Rendering> evento é gerado cada vez que a cena do aplicativo é desenhada. A taxa de quadros de renderização é o número de vezes que a cena é desenhada por segundo.  
  
> [!NOTE]
> Para obter um exemplo de código <xref:System.Windows.Media.CompositionTarget>completo usando, consulte [usando o exemplo de CompositionTarget](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.CompositionTarget.Rendering> evento é acionado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] durante o processo de renderização. O exemplo a seguir mostra como registrar um <xref:System.EventHandler> delegado para o método <xref:System.Windows.Media.CompositionTarget.Rendering> estático em <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 É possível usar o método de manipulador de eventos de renderização para criar conteúdo de personalizado de desenho. Esse método de manipulador de eventos é chamado uma vez por quadro. Toda vez que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realizar marshaling dos dados persistentes de renderização na árvore visual para o grafo de cena de composição, o método de manipulador de eventos será chamados. Além disso, se as alterações na árvore visual forçarem atualizações no grafo de cena de composição, o método de manipulador de eventos também será chamado. Observe que o método de manipulador de eventos será chamado após o cálculo do layout. No entanto, é possível modificar o layout no método de manipulador de eventos, o que significa que o layout será calculado mais uma vez antes da renderização.  
  
 O exemplo a seguir mostra como você pode fornecer um desenho personalizado <xref:System.Windows.Media.CompositionTarget> em um método de manipulador de eventos. Nesse caso, a cor do plano de fundo <xref:System.Windows.Controls.Canvas> do é desenhada com um valor de cor com base na posição da coordenada do mouse. Se você mover o mouse para dentro <xref:System.Windows.Controls.Canvas>do, sua cor do plano de fundo será alterada. Além disso, a taxa de quadros média será calculada, com base no tempo decorrido atual e no número total de quadros renderizados.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Você pode descobrir que seu desenho personalizado é executado em velocidades distintas em computadores diferentes. Isso ocorre porque seu desenho personalizado não independe da taxa de quadros. Dependendo do sistema que você está executando e da carga de trabalho desse sistema, o <xref:System.Windows.Media.CompositionTarget.Rendering> evento pode ser chamado um número diferente de vezes por segundo. Para obter informações sobre como determinar a capacidade de hardware de gráficos e o desempenho de um dispositivo que executa um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Camadas de Renderização de Gráficos](../advanced/graphics-rendering-tiers.md).  
  
 A adição ou remoção de <xref:System.EventHandler> um delegado de renderização enquanto o evento está sendo acionado será atrasada até o acionamento do evento ser concluído. Isso é consistente com <xref:System.MulticastDelegate>a manipulação de eventos baseados no CLR (Common Language Runtime). Observe também que não há uma garantia de que os eventos de renderização serão chamados em uma ordem específica. Se você tiver vários <xref:System.EventHandler> delegados que dependem de uma ordem específica, deverá registrar um único <xref:System.Windows.Media.CompositionTarget.Rendering> evento e multiplexar os delegados na ordem correta por conta própria.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.CompositionTarget>
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
