---
title: Visão geral do uso de layout automático
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 2fe473da3eeabef3852e3003e61b3b9604332855
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291264"
---
# <a name="use-automatic-layout-overview"></a>Visão geral do uso de layout automático

Este tópico apresenta diretrizes para desenvolvedores sobre como escrever aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] com interfaces do usuário localizáveis (UIs). No passado, a localização de uma interface do usuário era um processo demorado. Cada idioma para o qual a interface do usuário foi adaptada exigia um ajuste de pixel por pixel. Hoje, com o design certo e com os padrões de codificação corretos, as interfaces do projeto podem ser construídas para que os localizadores tenham menos redimensionamento e reposicionamento para fazer. A abordagem para escrever aplicativos que podem ser mais facilmente redimensionados e reposicionados é chamada de layout automático e pode ser obtida usando o design de aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a>Vantagens de usar o layout automático

Como o sistema de apresentação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é poderoso e flexível, ele fornece a capacidade de layout de elementos em um aplicativo que pode ser ajustado para atender aos requisitos de diferentes idiomas. A lista a seguir destaca algumas das vantagens do layout automático.

- A interface do usuário é bem exibida em qualquer idioma.

- Reduz a necessidade de reajustar a posição e o tamanho dos controles após o texto ser traduzido.

- Reduz a necessidade de reajustar o tamanho da janela.

- O layout da interface do usuário é renderizado corretamente em qualquer idioma.

- A localização pode ser reduzida a tal ponto que é pouco mais do que uma tradução de cadeia de caracteres.

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a>Layout automático e controles

O layout automático permite que um aplicativo ajuste o tamanho de um controle automaticamente. Por exemplo, um controle pode ser alterado para acomodar o tamanho de uma cadeia de caracteres. Essa funcionalidade permite que os localizadores traduzam a cadeia de caracteres; eles não precisam redimensionar o controle para ajustar o texto traduzido. O exemplo a seguir cria um botão com conteúdo em inglês.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

No exemplo, tudo que você tem que fazer para criar um botão em espanhol é mudar o texto. Por exemplo,

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

O gráfico a seguir mostra a saída dos exemplos de código:

![O mesmo botão com texto em idiomas diferentes](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a>Layout automático e padrões de codificação

O uso da abordagem de layout automático requer um conjunto de padrões de codificação e design e regras para produzir uma interface do usuário totalmente localizável. As diretrizes a seguir ajudarão na sua codificação de layout automático.

**Não usar posições absolutas**

- Não use <xref:System.Windows.Controls.Canvas> porque ele posiciona elementos absolutamente.

- Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> e <xref:System.Windows.Controls.Grid> para posicionar controles.

Para obter uma discussão sobre vários tipos de painéis, consulte [visão geral dos painéis](../controls/panels-overview.md).

**Não definir um tamanho fixo para uma janela**

- Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>. Por exemplo:

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**Adicionar um <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- Adicione um <xref:System.Windows.FrameworkElement.FlowDirection%2A> ao elemento raiz do seu aplicativo.

  O WPF fornece uma maneira conveniente para dar suporte a layouts horizontais, bidirecionais e verticais. Na estrutura de apresentação, a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A> pode ser usada para definir o layout. Os padrões de direção de fluxo são:

  - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) – layout horizontal para latim, leste asiático e assim por diante.

  - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) – bidirecional para árabe, Hebraico e assim por diante.

**Usar fontes compostas em vez de fontes físicas**

- Com fontes compostas, a propriedade <xref:System.Windows.Controls.Control.FontFamily%2A> não precisa ser localizada.

- Os desenvolvedores podem usar uma das seguintes fontes ou criar suas próprias.

  - Interface de Usuário Global
  - Global San Serif
  - Global Serif

**Adicionar XML: lang**

- Adicione o atributo `xml:lang` no elemento raiz da interface do usuário, como `xml:lang="en-US"` para um aplicativo em inglês.

- Como as fontes compostas usam `xml:lang` para determinar qual fonte usar, defina essa propriedade para dar suporte a cenários multilíngues.

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a>Layout automático e grades

O elemento <xref:System.Windows.Controls.Grid>, é útil para layout automático porque permite que um desenvolvedor Posicione elementos. Um controle <xref:System.Windows.Controls.Grid> é capaz de distribuir o espaço disponível entre seus elementos filho, usando uma organização de coluna e linha. Os elementos da interface do usuário podem abranger várias células e é possível ter grades dentro de grades. As grades são úteis porque permitem que você crie e posicione uma interface do usuário complexa. O exemplo a seguir demonstra o uso de uma grade para posicionar alguns botões e o texto. Observe que a altura e a largura das células são definidas como <xref:System.Windows.GridUnitType.Auto>; Portanto, a célula que contém o botão com uma imagem é ajustada para se ajustar à imagem.

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

O gráfico a seguir mostra a grade produzida pelo código anterior.

Grade de ![exemplo]de grade(./media/glob-grid.png "glob_grid")

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Layout automático e grades que utilizam a propriedade IsSharedSizeScope

Um elemento <xref:System.Windows.Controls.Grid> é útil em aplicativos localizáveis para criar controles que se ajustam para ajustar o conteúdo. No entanto, às vezes, você deseja que os controles mantenham um tamanho específico, independentemente do conteúdo. Por exemplo, se tiver os botões "OK", "Cancelar" e "Procurar", provavelmente você não desejará que os botões sejam redimensionados para se ajustarem ao conteúdo. Nesse caso, a propriedade anexada <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> é útil para compartilhar o mesmo dimensionamento entre vários elementos de grade. O exemplo a seguir demonstra como compartilhar dados de dimensionamento de coluna e linha entre vários elementos <xref:System.Windows.Controls.Grid>.

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> Para obter o exemplo de código completo, consulte [compartilhar Propriedades de dimensionamento entre grades](../controls/how-to-share-sizing-properties-between-grids.md).

## <a name="see-also"></a>Consulte também

- [Globalização para WPF](globalization-for-wpf.md)
- [Usar layout automático para criar um botão](how-to-use-automatic-layout-to-create-a-button.md)
- [Usar uma grade para layout automático](how-to-use-a-grid-for-automatic-layout.md)
