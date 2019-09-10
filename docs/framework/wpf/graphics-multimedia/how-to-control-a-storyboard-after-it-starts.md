---
title: 'Como: Controlar um Storyboard após sua inicialização'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855871"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Como: Controlar um Storyboard após sua inicialização

Este exemplo mostra como usar o código para controlar um <xref:System.Windows.Media.Animation.Storyboard> depois de iniciado. Para controlar um storyboard no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> e <xref:System.Windows.TriggerAction> objetos; para obter um exemplo, consulte [usar gatilhos de eventos para controlar um storyboard depois que ele é iniciado](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

Para iniciar um storyboard, você usa seu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método, que distribui as animações do storyboard para as propriedades que eles animam e inicia o storyboard.

Para tornar um storyboard controlável, use o <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método e especifique **true** como o segundo parâmetro. Em seguida, use os métodos interativos do storyboard para pausar, retomar, procurar, parar, acelerar ou retardar o storyboard ou avançar para seu período de preenchimento. A seguir temos uma lista de métodos interativos de storyboard:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pausa o storyboard.

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Retoma um storyboard pausado.

- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Define a velocidade interativa do storyboard.

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Procura o storyboard no local especificado.

- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Procura o storyboard no local especificado. Ao contrário <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> do método, essa operação é processada antes do próximo tique.

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Avança o storyboard para seu período de preenchimento, se ele tiver um.

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Para o storyboard.

No exemplo a seguir, diversos métodos de storyboard são usados para controlar de forma interativa um storyboard.

> [!NOTE]
> Para ver um exemplo de controle de um storyboard usando gatilhos com [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consulte [usar gatilhos de eventos para controlar um storyboard depois que ele for iniciado](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

## <a name="example"></a>Exemplo

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a>Consulte também

- [Usar gatilhos de evento para controlar um storyboard depois de ter começado](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
