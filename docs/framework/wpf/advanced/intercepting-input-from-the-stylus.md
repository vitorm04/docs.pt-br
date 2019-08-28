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
ms.openlocfilehash: 2547c0aa2f3a14080868c2760fa8999eb99d3d16
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046325"
---
# <a name="intercepting-input-from-the-stylus"></a>Interceptando entrada a partir da caneta
A <xref:System.Windows.Input.StylusPlugIns> arquitetura fornece um mecanismo para implementar o controle de baixo nível <xref:System.Windows.Input.Stylus> sobre a entrada e a criação de <xref:System.Windows.Ink.Stroke> objetos de tinta digital. A <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classe fornece um mecanismo para implementar o comportamento personalizado e aplicá-lo ao fluxo de dados provenientes do dispositivo de caneta para o desempenho ideal.  
  
 Este tópico contém as seguintes subseções:  
  
- [Arquitetura](#Architecture)  
  
- [Implementando plug-ins de caneta](#ImplementingStylusPlugins)  
  
- [Adicionando seu plug-in a uma InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Conclusão](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Arquitetura  
 O <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> é a evolução das APIs [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) , descritas em [acessando e manipulando a entrada de caneta](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409), no [Microsoft Windows XP Tablet PC Edition Software Development Kit 1,7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Cada <xref:System.Windows.UIElement> um tem <xref:System.Windows.UIElement.StylusPlugIns%2A> uma propriedade que é <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>um. Você pode adicionar um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à <xref:System.Windows.UIElement.StylusPlugIns%2A> propriedade de um elemento para manipular <xref:System.Windows.Input.StylusPoint> dados conforme eles são gerados. <xref:System.Windows.Input.StylusPoint>os dados consistem em todas as propriedades com suporte do digitalizador do sistema <xref:System.Windows.Input.StylusPoint.X%2A> , <xref:System.Windows.Input.StylusPoint.Y%2A> incluindo os dados de ponto e <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> , bem como os dados.  
  
 Os <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objetos são inseridos diretamente no fluxo de dados provenientes <xref:System.Windows.Input.Stylus> do dispositivo quando <xref:System.Windows.UIElement.StylusPlugIns%2A> você adiciona o <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à propriedade. A ordem na qual os plug-ins são adicionados à <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção determina a ordem na qual eles receberão <xref:System.Windows.Input.StylusPoint> dados. Por exemplo, se você adicionar um plug-in de filtro que restringe a entrada a uma região específica e, em seguida, adicionar um plug-in que reconhece gestos conforme eles são gravados, o plug-in que reconhece <xref:System.Windows.Input.StylusPoint> gestos receberá dados filtrados.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementando plug-ins de caneta  
 Para implementar um plug-in, derive uma classe <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>de. Essa classe é aplicada ao fluxo de dados à medida que chega do <xref:System.Windows.Input.Stylus>. Nessa classe, você pode modificar os valores dos <xref:System.Windows.Input.StylusPoint> dados.  
  
> [!CAUTION]
> Se um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> lançar ou causar uma exceção, o aplicativo será fechado. Você deve testar exaustivamente os controles que <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> consomem um e usar apenas um controle se <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> você tiver certeza de que o não lançará uma exceção.  
  
 O exemplo a seguir demonstra um plug-in que restringe a entrada da caneta modificando <xref:System.Windows.Input.StylusPoint.X%2A> os <xref:System.Windows.Input.StylusPoint.Y%2A> valores e nos <xref:System.Windows.Input.StylusPoint> dados conforme eles chegam do <xref:System.Windows.Input.Stylus> dispositivo.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Adicionando seu plug-in a uma InkCanvas  
 A maneira mais fácil de usar seu plug-in personalizado é implementar uma classe derivada de InkCanvas e adicioná-la à <xref:System.Windows.UIElement.StylusPlugIns%2A> propriedade.  
  
 O exemplo a seguir demonstra um <xref:System.Windows.Controls.InkCanvas> personalizado que filtra a tinta.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Se você adicionar um `FilterInkCanvas` ao seu aplicativo e executá-lo, observará que a tinta não fica restrita a uma região até após o usuário concluir um traço. Isso ocorre porque o <xref:System.Windows.Controls.InkCanvas> tem uma <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> Propriedade, que é um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e já é um membro da <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção. O personalizado <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> que você adicionou <xref:System.Windows.UIElement.StylusPlugIns%2A> à coleção recebe os <xref:System.Windows.Input.StylusPoint> dados depois <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> de receber dados. Como resultado, os <xref:System.Windows.Input.StylusPoint> dados não serão filtrados até que o usuário levante a caneta para terminar um traço. Para filtrar a tinta à medida que o usuário a desenha, você deve `FilterPlugin` inserir o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>antes de.  
  
 O código C# a seguir demonstra um <xref:System.Windows.Controls.InkCanvas> personalizado que filtra a tinta à medida que ela é desenhada.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusão  
 Ao derivar suas próprias <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes e inseri-las em <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> coleções, você pode aprimorar muito o comportamento da sua tinta digital. Você tem acesso aos <xref:System.Windows.Input.StylusPoint> dados conforme eles são gerados, dando a oportunidade de personalizar a <xref:System.Windows.Input.Stylus> entrada. Como você tem esse acesso de baixo nível aos <xref:System.Windows.Input.StylusPoint> dados, é possível implementar coleta de tinta e renderização com desempenho ideal para seu aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Tratamento avançado de tinta](advanced-ink-handling.md)
- [Acessar e manipular a entrada à caneta](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
