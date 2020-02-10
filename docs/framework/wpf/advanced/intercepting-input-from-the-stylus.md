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
ms.openlocfilehash: 7629843730a82584e94448ceac1ea574906876c9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095132"
---
# <a name="intercepting-input-from-the-stylus"></a>Interceptando entrada a partir da caneta
A arquitetura de <xref:System.Windows.Input.StylusPlugIns> fornece um mecanismo para implementar o controle de baixo nível sobre <xref:System.Windows.Input.Stylus> entrada e a criação de objetos de <xref:System.Windows.Ink.Stroke> de tinta digital. A classe <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> fornece um mecanismo para implementar o comportamento personalizado e aplicá-lo ao fluxo de dados provenientes do dispositivo de caneta para o desempenho ideal.  
  
 Este tópico contém as seguintes subseções:  
  
- [Arquitetura](#Architecture)  
  
- [Implementando plug-ins de caneta](#ImplementingStylusPlugins)  
  
- [Adicionando seu plug-in a uma InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Conclusão](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Arquitetura  
 A <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> é a evolução das APIs [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) , descritas em [acessando e manipulando a entrada da caneta](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).  
  
 Cada <xref:System.Windows.UIElement> tem uma propriedade <xref:System.Windows.UIElement.StylusPlugIns%2A> que é uma <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Você pode adicionar um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à propriedade <xref:System.Windows.UIElement.StylusPlugIns%2A> de um elemento para manipular <xref:System.Windows.Input.StylusPoint> dados conforme eles são gerados. <xref:System.Windows.Input.StylusPoint> dados consistem em todas as propriedades com suporte no digitalizador do sistema, incluindo os dados do <xref:System.Windows.Input.StylusPoint.X%2A> e do ponto de <xref:System.Windows.Input.StylusPoint.Y%2A>, bem como <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> dados.  
  
 Os objetos <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> são inseridos diretamente no fluxo de dados proveniente do dispositivo <xref:System.Windows.Input.Stylus> quando você adiciona o <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à propriedade <xref:System.Windows.UIElement.StylusPlugIns%2A>. A ordem na qual os plug-ins são adicionados à coleção de <xref:System.Windows.UIElement.StylusPlugIns%2A> determina a ordem na qual eles receberão <xref:System.Windows.Input.StylusPoint> dados. Por exemplo, se você adicionar um plug-in de filtro que restringe a entrada a uma região específica e, em seguida, adicionar um plug-in que reconhece gestos conforme eles são gravados, o plug-in que reconhece gestos receberá <xref:System.Windows.Input.StylusPoint> dados filtrados.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementando plug-ins de caneta  
 Para implementar um plug-in, derive uma classe de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Essa classe é aplicada ao fluxo de dados à medida que chega da <xref:System.Windows.Input.Stylus>. Nessa classe, você pode modificar os valores dos dados de <xref:System.Windows.Input.StylusPoint>.  
  
> [!CAUTION]
> Se um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> gera ou gera uma exceção, o aplicativo será fechado. Você deve testar exaustivamente os controles que consomem um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e usar apenas um controle se você tiver certeza de que o <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> não gerará uma exceção.  
  
 O exemplo a seguir demonstra um plug-in que restringe a entrada da caneta modificando os valores <xref:System.Windows.Input.StylusPoint.X%2A> e <xref:System.Windows.Input.StylusPoint.Y%2A> nos dados de <xref:System.Windows.Input.StylusPoint> conforme eles são provenientes do dispositivo <xref:System.Windows.Input.Stylus>.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Adicionando seu plug-in a uma InkCanvas  
 A maneira mais fácil de usar seu plug-in personalizado é implementar uma classe derivada de InkCanvas e adicioná-la à propriedade <xref:System.Windows.UIElement.StylusPlugIns%2A>.  
  
 O exemplo a seguir demonstra um <xref:System.Windows.Controls.InkCanvas> personalizado que filtra a tinta.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Se você adicionar um `FilterInkCanvas` ao seu aplicativo e executá-lo, observará que a tinta não fica restrita a uma região até após o usuário concluir um traço. Isso ocorre porque o <xref:System.Windows.Controls.InkCanvas> tem uma propriedade <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>, que é uma <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e já é um membro da coleção de <xref:System.Windows.UIElement.StylusPlugIns%2A>. O <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personalizado adicionado à coleção de <xref:System.Windows.UIElement.StylusPlugIns%2A> recebe os dados de <xref:System.Windows.Input.StylusPoint> depois que <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> recebe dados. Como resultado, os dados de <xref:System.Windows.Input.StylusPoint> não serão filtrados até que o usuário levante a caneta para terminar um traço. Para filtrar a tinta à medida que o usuário a desenha, você deve inserir o `FilterPlugin` antes da <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 O código C# a seguir demonstra um <xref:System.Windows.Controls.InkCanvas> personalizado que filtra a tinta à medida que ela é desenhada.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusão  
 Ao derivar suas próprias classes de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e inseri-las em coleções de <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, você pode aprimorar muito o comportamento da sua tinta digital. Você tem acesso aos dados de <xref:System.Windows.Input.StylusPoint> conforme eles são gerados, oferecendo a oportunidade de personalizar a entrada de <xref:System.Windows.Input.Stylus>. Como você tem esse acesso de baixo nível aos dados de <xref:System.Windows.Input.StylusPoint>, você pode implementar a coleta e a renderização de tinta com desempenho ideal para seu aplicativo.  
  
## <a name="see-also"></a>Confira também

- [Tratamento avançado de tinta](advanced-ink-handling.md)
- [Acessar e manipular a entrada à caneta](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
