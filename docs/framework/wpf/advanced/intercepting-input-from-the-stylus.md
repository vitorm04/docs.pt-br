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
ms.openlocfilehash: 0568e72e6d686ce08e6bd802f273e45dd623524b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374304"
---
# <a name="intercepting-input-from-the-stylus"></a>Interceptando entrada a partir da caneta
O <xref:System.Windows.Input.StylusPlugIns> arquitetura fornece um mecanismo para implementar o controle de baixo nível sobre <xref:System.Windows.Input.Stylus> de entrada e a criação de tinta digital <xref:System.Windows.Ink.Stroke> objetos. O <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classe fornece um mecanismo para que você possa implementar comportamento personalizado e aplicá-lo para o fluxo de dados provenientes do dispositivo de caneta para o desempenho ideal.  
  
 Este tópico contém as seguintes subseções:  
  
-   [Arquitetura](#Architecture)  
  
-   [Implementando plug-ins de caneta](#ImplementingStylusPlugins)  
  
-   [Adicionando seu plug-in a uma InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
-   [Conclusão](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Arquitetura  
 O <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> é a evolução do [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) APIs, como descritas em [acessando e manipulando entrada de caneta](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409), no [Microsoft Windows XP Tablet PC Edition Software Development Kit 1.7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Cada <xref:System.Windows.UIElement> tem uma <xref:System.Windows.UIElement.StylusPlugIns%2A> propriedade que é um <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Você pode adicionar um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a um elemento <xref:System.Windows.UIElement.StylusPlugIns%2A> propriedade manipular <xref:System.Windows.Input.StylusPoint> dados como ele são gerados. <xref:System.Windows.Input.StylusPoint> dados consistem em todas as propriedades suportadas pelo digitalizador do sistema, incluindo o <xref:System.Windows.Input.StylusPoint.X%2A> e <xref:System.Windows.Input.StylusPoint.Y%2A> ponto de dados, bem como <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> dados.  
  
 Sua <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objetos são inseridos diretamente no fluxo de dados provenientes do <xref:System.Windows.Input.Stylus> dispositivo quando você adiciona a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> para o <xref:System.Windows.UIElement.StylusPlugIns%2A> propriedade. A ordem na qual os plug-ins são adicionados para o <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção determina a ordem na qual eles irão receber <xref:System.Windows.Input.StylusPoint> dados. Por exemplo, se você adicionar um plug-in de filtro que restringe a entrada para uma região específica e, em seguida, adicionar um plug-in que reconheça gestos conforme eles são gravados, o plug-in que reconhece gestos receberá filtrado <xref:System.Windows.Input.StylusPoint> dados.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementando plug-ins de caneta  
 Para implementar um plug-in, derive uma classe de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Essa classe é aplicada ao fluxo de dados conforme eles chegam do <xref:System.Windows.Input.Stylus>. Nessa classe, você pode modificar os valores da <xref:System.Windows.Input.StylusPoint> dados.  
  
> [!CAUTION]
>  Se um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> gera ou causa uma exceção, o aplicativo será fechado. Você deve testar exaustivamente controles que consomem uma <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e usar um controle somente se você tiver certeza de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> não lançará uma exceção.  
  
 O exemplo a seguir demonstra um plug-in que restringe a entrada da caneta, modificando o <xref:System.Windows.Input.StylusPoint.X%2A> e <xref:System.Windows.Input.StylusPoint.Y%2A> os valores na <xref:System.Windows.Input.StylusPoint> dados como ela é proveniente de <xref:System.Windows.Input.Stylus> dispositivo.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Adicionando seu plug-in a uma InkCanvas  
 A maneira mais fácil de usar o plug-in personalizado é implementar uma classe que derive de InkCanvas e adicioná-lo para o <xref:System.Windows.UIElement.StylusPlugIns%2A> propriedade.  
  
 O exemplo a seguir demonstra um personalizado <xref:System.Windows.Controls.InkCanvas> que filtra a tinta.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Se você adicionar um `FilterInkCanvas` ao seu aplicativo e executá-lo, observará que a tinta não fica restrita a uma região até após o usuário concluir um traço. Isso ocorre porque o <xref:System.Windows.Controls.InkCanvas> tem uma <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> propriedade, que é um <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e já é um membro do <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção. Personalizado <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> adicionado ao <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção recebe o <xref:System.Windows.Input.StylusPoint> dados após <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> recebe os dados. Como resultado, o <xref:System.Windows.Input.StylusPoint> dados não serão filtrados até depois que o usuário levante a caneta para encerrar um traço. Para filtrar a tinta conforme o usuário a desenha, você deve inserir o `FilterPlugin` antes do <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 O código c# a seguir demonstra um personalizado <xref:System.Windows.Controls.InkCanvas> que filtra a tinta conforme ela é desenhada.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusão  
 Criando suas próprias <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes e inseri-las em <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> coleções, você pode aprimorar bastante o comportamento de sua tinta digital. Você tem acesso a <xref:System.Windows.Input.StylusPoint> dados como ele são gerados, oferecendo a oportunidade para personalizar o <xref:System.Windows.Input.Stylus> entrada. Porque você tem tal acesso de baixo nível para o <xref:System.Windows.Input.StylusPoint> dados, você pode implementar a coleção de tinta e renderizá-la com um desempenho ideal para seu aplicativo.  
  
## <a name="see-also"></a>Consulte também
- [Tratamento avançado de tinta](advanced-ink-handling.md)
- [Acessar e manipular a entrada à caneta](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
