---
title: Introdução ao objeto GlyphRun e ao elemento de glifos
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181959"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Introdução ao objeto GlyphRun e ao elemento de glifos
Este tópico descreve <xref:System.Windows.Media.GlyphRun> o <xref:System.Windows.Documents.Glyphs> objeto e o elemento.  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a>Introdução ao GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fornece suporte avançado de texto, incluindo marcação <xref:System.Windows.Documents.Glyphs> em nível de glifos com acesso direto para clientes que desejam interceptar e persistir texto após a formatação. Esses recursos dão suporte crítico aos diferentes requisitos de renderização de texto em cada um dos cenários a seguir.  
  
1. Exibição em tela de documentos de formato fixo.  
  
2. Cenários de impressão.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] como uma linguagem de impressora do dispositivo.  
  
    - Escritor de documentos Microsoft XPS.  
  
    - Drivers de impressora anteriores, saída de aplicativos Win32 para o formato fixo.  
  
    - Formato do spool de impressão.  
  
3. Representação de documentos em formato fixo, incluindo clientes para versões anteriores do Windows e outros dispositivos de computação.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>e <xref:System.Windows.Media.GlyphRun> são projetados para apresentação de documentos em formato fixo e cenários de impressão. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fornece vários elementos [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para layout <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>geral e cenários como e . Para obter mais [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] informações sobre layout e cenários, consulte a [Tipografia no WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a>O Objeto GlyphRun  
 O <xref:System.Windows.Media.GlyphRun> objeto representa uma seqüência de glifos de uma única face de uma única fonte em um único tamanho, e com um único estilo de renderização.  
  
 <xref:System.Windows.Media.GlyphRun>inclui ambos os detalhes da <xref:System.Windows.Documents.Glyphs.Indices%2A> fonte, como as posições do glifo e do glifo individual. Ele também inclui os pontos de código Unicode originais dos quais a execução foi gerada, informações de mapeamento de deslocamento de buffer de caractere para glifos, e sinalizadores por caractere e por glifos.  
  
 <xref:System.Windows.Media.GlyphRun>tem um alto <xref:System.Windows.FrameworkElement>nível <xref:System.Windows.Documents.Glyphs>correspondente, . <xref:System.Windows.Documents.Glyphs>pode ser usado na árvore [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de elementos e na marcação para representar <xref:System.Windows.Media.GlyphRun> a saída.  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a>O Elemento Glyphs  
 O <xref:System.Windows.Documents.Glyphs> elemento representa a <xref:System.Windows.Media.GlyphRun> saída [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]de a in . A seguinte sintaxe de marcação é usada para descrever o <xref:System.Windows.Documents.Glyphs> elemento.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 As seguintes definições de propriedade correspondem aos quatro primeiros atributos na marcação de exemplo.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Especifica um identificador de recursos: nome do arquivo, uri (Web uniform resource identifier, identificador de recursos) ou referência de recursos no aplicativo .exe ou contêiner.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Especifica o tamanho da fonte em unidades de superfície de desenho (o padrão é 0,96 polegadas).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Especifica os sinalizadores para estilos em negrito e itálico.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Especifica o nível de layout bidirecional. Valores pares e zero implicam um layout da esquerda para a direita; valores ímpares implicam um layout da direita para a esquerda.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a>Propriedade de índices  
 A <xref:System.Windows.Documents.Glyphs.Indices%2A> propriedade é uma série de especificações de glifos. Quando uma sequência de glifos forma um único cluster, a especificação do primeiro glifo no cluster será precedida por uma especificação de quantos glifos e quantos pontos de código se combinam para formar o cluster. A <xref:System.Windows.Documents.Glyphs.Indices%2A> propriedade coleta em uma seqüência as seguintes propriedades.  
  
- Índices de glifo  
  
- Larguras de avanço de glifo  
  
- Combinando vetores de anexo de glifo  
  
- Mapeamento de cluster de pontos de código para glifos  
  
- Sinalizadores de glifo  
  
 Cada especificação de glifo tem o seguinte formato.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a>Métricas de glifo  
 Cada glifo define métricas que especificam como <xref:System.Windows.Documents.Glyphs>ele se alinha com outros . O gráfico a seguir define as várias qualidades tipográficas de dois caracteres de glifo diferentes.  
  
 ![Diagrama de medidas de glifo](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a>Marcação de glifos  
 O exemplo de código a seguir <xref:System.Windows.Documents.Glyphs> mostra [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]como usar várias propriedades do elemento em .  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Confira também

- [Tipografia no WPF](typography-in-wpf.md)
- [Documentos no WPF](documents-in-wpf.md)
- [Texto](optimizing-performance-text.md)
