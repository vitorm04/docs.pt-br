---
title: Como renderizar em um intervalo por quadro usando CompositionTarget
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
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7616a418b9f2f6b175b925e4385322c42546e9bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Como renderizar em um intervalo por quadro usando CompositionTarget
O mecanismo de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece vários recursos para criar animações baseadas em quadros. No entanto, há cenários de aplicativo em que é necessário um controle mais refinado da renderização por quadro. O <xref:System.Windows.Media.CompositionTarget> fornece a capacidade de criar animações personalizadas com base em um retorno de chamada por quadro.  
  
 <xref:System.Windows.Media.CompositionTarget>é uma classe estática que representa a superfície de exibição em que seu aplicativo está sendo desenhado. O <xref:System.Windows.Media.CompositionTarget.Rendering> é gerado sempre que cena do aplicativo é desenhada. A taxa de quadros de renderização é o número de vezes que a cena é desenhada por segundo.  
  
> [!NOTE]
>  Para um exemplo de código completo usando <xref:System.Windows.Media.CompositionTarget>, consulte [usando o exemplo CompositionTarget](http://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.CompositionTarget.Rendering> evento é acionado durante o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processo de renderização. O exemplo a seguir mostra como você registra um <xref:System.EventHandler> delegue estático <xref:System.Windows.Media.CompositionTarget.Rendering> método <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 É possível usar o método de manipulador de eventos de renderização para criar conteúdo de personalizado de desenho. Esse método de manipulador de eventos é chamado uma vez por quadro. Toda vez que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realizar marshaling dos dados persistentes de renderização na árvore visual para o grafo de cena de composição, o método de manipulador de eventos será chamados. Além disso, se as alterações na árvore visual forçarem atualizações no grafo de cena de composição, o método de manipulador de eventos também será chamado. Observe que o método de manipulador de eventos será chamado após o cálculo do layout. No entanto, é possível modificar o layout no método de manipulador de eventos, o que significa que o layout será calculado mais uma vez antes da renderização.  
  
 O exemplo a seguir mostra como você pode fornecer desenhos personalizados em um <xref:System.Windows.Media.CompositionTarget> método manipulador de eventos. Nesse caso, a cor de fundo de <xref:System.Windows.Controls.Canvas> é desenhada com um valor de cor com base na posição coordenada do mouse. Se você mover o mouse dentro do <xref:System.Windows.Controls.Canvas>, suas alterações de cor do plano de fundo. Além disso, a taxa de quadros média será calculada, com base no tempo decorrido atual e no número total de quadros renderizados.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Você pode descobrir que seu desenho personalizado é executado em velocidades distintas em computadores diferentes. Isso ocorre porque seu desenho personalizado não independe da taxa de quadros. Dependendo do sistema que você está executando e a carga de trabalho do sistema, o <xref:System.Windows.Media.CompositionTarget.Rendering> evento pode ser chamado como um número diferente de vezes por segundo. Para obter informações sobre como determinar a capacidade de hardware de gráficos e o desempenho de um dispositivo que executa um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Camadas de Renderização de Gráficos](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 Adicionando ou removendo uma renderização de <xref:System.EventHandler> delegado enquanto o evento está disparando será atrasado até após o evento de disparo. Isso é consistente com o comportamento <xref:System.MulticastDelegate>-eventos com base são tratados no tempo de execução do CLR (Common Language). Observe também que não há uma garantia de que os eventos de renderização serão chamados em uma ordem específica. Se você tiver vários <xref:System.EventHandler> delegados que se baseiam em uma ordem específica, você deve registrar um único <xref:System.Windows.Media.CompositionTarget.Rendering> eventos e multiplexar os representantes na corretas ordem por conta própria.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.CompositionTarget>  
 [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
