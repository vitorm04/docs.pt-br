---
title: Visão geral do uso de layout automático
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: a43b3c0e008025171e3b1fdeba3bc514d01e28c8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856031"
---
# <a name="use-automatic-layout-overview"></a>Visão geral do uso de layout automático
Este tópico apresenta diretrizes para desenvolvedores sobre como escrever [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos com localizáveis [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. No passado, a localização de um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] era um processo demorado. Cada idioma que o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado exigia um ajuste pixel por pixel. Hoje, com o design e o direito de padrões de codificação, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] pode ser criado para que os localizadores tenham menos redimensionamento e reposicionamento. A abordagem para escrever aplicativos que podem ser mais facilmente redimensionados e reposicionados é chamada de layout automático e pode ser obtida usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] design do aplicativo.  
  
<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>Vantagens de usar o layout automático  
 Porque o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de apresentação é poderoso e flexível, ele fornece a capacidade de dispor os elementos em um aplicativo que pode ser ajustada para atender às necessidades de diferentes idiomas. A lista a seguir destaca algumas das vantagens do layout automático.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é bem exibido em qualquer idioma.  
  
-   Reduz a necessidade de reajustar a posição e o tamanho dos controles após o texto ser traduzido.  
  
-   Reduz a necessidade de reajustar o tamanho da janela.  
  
-   O layout [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderiza adequadamente em qualquer idioma.  
  
-   A localização pode ser reduzida a tal ponto que é pouco mais do que uma tradução de cadeia de caracteres.  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>Layout automático e controles  
 O layout automático permite que um aplicativo ajuste o tamanho de um controle automaticamente. Por exemplo, um controle pode ser alterado para acomodar o tamanho de uma cadeia de caracteres. Essa funcionalidade permite que os localizadores traduzam a cadeia de caracteres; eles não precisam redimensionar o controle para ajustar o texto traduzido. O exemplo a seguir cria um botão com conteúdo em inglês.  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 No exemplo, tudo que você tem que fazer para criar um botão em espanhol é mudar o texto. Por exemplo,  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 O gráfico a seguir mostra a saída dos exemplos de código.  
  
 ![O mesmo botão com texto em diferentes idiomas](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Botão redimensionável automaticamente  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>Layout automático e padrões de codificação  
 Usando a abordagem de layout automático requer um conjunto de regras para produzir um completamente localizável e padrões de codificação e design [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. As diretrizes a seguir ajudarão na sua codificação de layout automático.  
  
| Padrões de codificação | Descrição |
| ---------------------- | ----------------- |
| Não use posições absolutas. | <ul><li>Não use <xref:System.Windows.Controls.Canvas> porque ele posiciona elementos absolutamente.</li><li>Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, e <xref:System.Windows.Controls.Grid> para posicionar controles.</li><li>Para uma discussão sobre diversos tipos de painéis, consulte [visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md).</li></ul> |
| Não defina um tamanho fixo para uma janela. | -Use <xref:System.Windows.Window.SizeToContent%2A>.<br />Por exemplo:<br /><br /> [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)] |
| Adicionar um <xref:System.Windows.FrameworkElement.FlowDirection%2A>. | <ul><li>Adicionar um <xref:System.Windows.FrameworkElement.FlowDirection%2A> ao elemento raiz do seu aplicativo.</li><li>O WPF fornece uma maneira conveniente de dar suporte a horizontais, bidirecionais e layouts verticais. No framework de apresentação, o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade pode ser usada para definir o layout. Os padrões de direção de fluxo são:<br /><br /> <ul><li><xref:System.Windows.FlowDirection.LeftToRight> (LrTb) — layout horizontal para latim, Leste Asiático e assim por diante.</li><li><xref:System.Windows.FlowDirection.RightToLeft> (RlTb) — bidirecional para árabe, hebraico e assim por diante.</li></ul></li></ul> |
| Use fontes de composição em vez de fontes físicas. | <ul><li>Com fontes compostas, o <xref:System.Windows.Controls.Control.FontFamily%2A> propriedade não precisa ser localizada.</li><li>Os desenvolvedores podem usar uma das seguintes fontes ou criar suas próprias.<br /><br /> <ul><li>Interface de Usuário Global</li><li>Global San Serif</li><li>Global Serif</li></ul></li></ul> |
| Adicionar xml:lang. | <ul><li>Adicione a `xml:lang` atributo no elemento raiz do seu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], como `xml:lang="en-US"` para um aplicativo em inglês.</li><li>Como usam fontes de composição `xml:lang` para determinar qual fonte utilizar, defina essa propriedade para dar suporte a cenários multilíngues.</li></ul> |
  
<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>Layout automático e grades  
 O <xref:System.Windows.Controls.Grid> elemento, é útil para layout automático porque ele permite que um desenvolvedor posicione elementos. Um <xref:System.Windows.Controls.Grid> controle é capaz de distribuir o espaço disponível entre seus elementos filhos, usando uma disposição de linha e coluna. O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos podem abranger várias células, e é possível que haja grades dentro de grades. As grades são úteis porque permitem que você crie e posicione complexos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O exemplo a seguir demonstra o uso de uma grade para posicionar alguns botões e o texto. Observe que a altura e largura das células são definidas como <xref:System.Windows.GridUnitType.Auto>; portanto, a célula que contém o botão com uma imagem é ajustada para ajustar a imagem.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 O gráfico a seguir mostra a grade produzida pelo código anterior.  
  
 ![Exemplo de grade](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Grade  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Layout automático e grades que utilizam a propriedade IsSharedSizeScope  
 Um <xref:System.Windows.Controls.Grid> elemento é útil em aplicativos localizáveis para criar controles que são ajustadas para que o conteúdo. No entanto, às vezes, você deseja que os controles mantenham um tamanho específico, independentemente do conteúdo. Por exemplo, se tiver os botões "OK", "Cancelar" e "Procurar", provavelmente você não desejará que os botões sejam redimensionados para se ajustarem ao conteúdo. Nesse caso, o <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> propriedade anexada é útil para compartilhar o mesmo tamanho entre vários elementos da grade. O exemplo a seguir demonstra como compartilhar dados entre vários de tamanho de linha e coluna <xref:System.Windows.Controls.Grid> elementos.  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Observação** para o exemplo de código completo, consulte [compartilhar propriedades de dimensionamento entre grades](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>Consulte também  
 [Globalização para WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Usar layout automático para criar um botão](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Usar uma grade para layout automático](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
