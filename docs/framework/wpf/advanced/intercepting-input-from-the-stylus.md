---
title: Interceptando entrada a partir da caneta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 17cf42a9d6d94d6ea12399561af5647df3b4d8c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181925"
---
# <a name="intercepting-input-from-the-stylus"></a>Interceptando entrada a partir da caneta
A <xref:System.Windows.Input.StylusPlugIns> arquitetura fornece um mecanismo para implementar <xref:System.Windows.Input.Stylus> controle de baixo nível <xref:System.Windows.Ink.Stroke> sobre a entrada e a criação de objetos de tinta digital. A <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classe fornece um mecanismo para você implementar o comportamento personalizado e aplicá-lo ao fluxo de dados provenientes do dispositivo stylus para o desempenho ideal.  
  
 Este tópico contém as seguintes subseções:  
  
- [Arquitetura](#Architecture)  
  
- [Implementando plug-ins de caneta](#ImplementingStylusPlugins)  
  
- [Adicionando seu plug-in a uma InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Conclusão](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Arquitetura  
 A <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> é a evolução das APIs [StylusInput,](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) descritas na [entrada de caneta de acesso e manipulação](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).  
  
 Cada <xref:System.Windows.UIElement> um <xref:System.Windows.UIElement.StylusPlugIns%2A> tem uma <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>propriedade que é uma. Você pode <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> adicionar a à <xref:System.Windows.UIElement.StylusPlugIns%2A> propriedade <xref:System.Windows.Input.StylusPoint> de um elemento para manipular dados à medida que são gerados. <xref:System.Windows.Input.StylusPoint>os dados consistem em todas as propriedades suportadas <xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint.Y%2A> pelo digitalizador <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> do sistema, incluindo os dados e pontos, bem como os dados.  
  
 Seus <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objetos são inseridos diretamente no <xref:System.Windows.Input.Stylus> fluxo de dados <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> provenientes do dispositivo quando você adiciona o <xref:System.Windows.UIElement.StylusPlugIns%2A> da propriedade. A ordem em que os <xref:System.Windows.UIElement.StylusPlugIns%2A> plug-ins são adicionados à <xref:System.Windows.Input.StylusPoint> coleta dita a ordem em que eles receberão dados. Por exemplo, se você adicionar um plug-in de filtro que restringe a entrada a uma determinada região e, em seguida, adicionar um plug-in que reconhece gestos à medida que eles são escritos, o plug-in que reconhece gestos receberá dados filtrados. <xref:System.Windows.Input.StylusPoint>  
  
<a name="ImplementingStylusPlugins"></a>
## <a name="implementing-stylus-plug-ins"></a>Implementando plug-ins de caneta  
 Para implementar um plug-in, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>obtenha uma classe de . Esta classe é aplicada o fluxo de dados <xref:System.Windows.Input.Stylus>como ele vem do . Nesta classe você pode modificar <xref:System.Windows.Input.StylusPoint> os valores dos dados.  
  
> [!CAUTION]
> Se <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> um arremesso ou causar uma exceção, a aplicação será encerrada. Você deve testar completamente os <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> controles que consomem um e <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> só usar um controle se você tiver certeza de que não lançará uma exceção.  
  
 O exemplo a seguir demonstra um plug-in que restringe <xref:System.Windows.Input.StylusPoint.X%2A> a <xref:System.Windows.Input.StylusPoint.Y%2A> entrada <xref:System.Windows.Input.StylusPoint> de caneta modificando <xref:System.Windows.Input.Stylus> os valores e valores nos dados à medida que ele vem do dispositivo.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Adicionando seu plug-in a uma InkCanvas  
 A maneira mais fácil de usar seu plug-in personalizado é implementar uma classe <xref:System.Windows.UIElement.StylusPlugIns%2A> que deriva do InkCanvas e adicioná-lo à propriedade.  
  
 O exemplo a <xref:System.Windows.Controls.InkCanvas> seguir demonstra um costume que filtra a tinta.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Se você adicionar um `FilterInkCanvas` ao seu aplicativo e executá-lo, observará que a tinta não fica restrita a uma região até após o usuário concluir um traço. Isso porque <xref:System.Windows.Controls.InkCanvas> o <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> tem um imóvel, que é <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> um <xref:System.Windows.UIElement.StylusPlugIns%2A> e já é um membro da coleção. O <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> costume adicionado <xref:System.Windows.UIElement.StylusPlugIns%2A> à coleção <xref:System.Windows.Input.StylusPoint> recebe <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> os dados após receber dados. Como resultado, <xref:System.Windows.Input.StylusPoint> os dados não serão filtrados até que o usuário levante a caneta para terminar um curso. Para filtrar a tinta à medida que `FilterPlugin` o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>usuário a desenha, você deve inserir o antes do .  
  
 O código C# a <xref:System.Windows.Controls.InkCanvas> seguir demonstra um costume que filtra a tinta à medida que é desenhada.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Conclusão  
 Ao derivar <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> suas próprias aulas <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> e inseri-las em coleções, você pode melhorar muito o comportamento de sua tinta digital. Você tem acesso <xref:System.Windows.Input.StylusPoint> aos dados como eles são gerados, dando-lhe a oportunidade de personalizar a <xref:System.Windows.Input.Stylus> entrada. Como você tem um acesso <xref:System.Windows.Input.StylusPoint> tão baixo aos dados, você pode implementar a coleta e renderização de tinta com o desempenho ideal para sua aplicação.  
  
## <a name="see-also"></a>Confira também

- [Tratamento de Tinta Avançado](advanced-ink-handling.md)
- [Acessar e manipular a entrada à caneta](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
