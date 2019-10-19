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
ms.openlocfilehash: 2f7bb3fb4f28b063c78dde9f9f354b38a5e707f3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581901"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Introdução ao objeto GlyphRun e ao elemento de glifos
Este tópico descreve o objeto <xref:System.Windows.Media.GlyphRun> e o elemento <xref:System.Windows.Documents.Glyphs>.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Introdução ao GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece suporte de texto avançado, incluindo marcação de nível de glifo com acesso direto a <xref:System.Windows.Documents.Glyphs> para clientes que desejam interceptar e persistir texto após a formatação. Esses recursos dão suporte crítico aos diferentes requisitos de renderização de texto em cada um dos cenários a seguir.  
  
1. Exibição em tela de documentos de formato fixo.  
  
2. Cenários de impressão.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] como uma linguagem de impressora do dispositivo.  
  
    - Microsoft XPS Document Writer.  
  
    - A saída de drivers de impressão anteriores é de aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] para o formato fixo.  
  
    - Formato do spool de impressão.  
  
3. Representação de documento de formato fixo, incluindo clientes para versões anteriores do Windows e outros dispositivos de computação.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun> são projetados para cenários de impressão e de apresentação de documentos de formato fixo. o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece vários elementos para o layout geral e cenários de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], como <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.TextBlock>. Para mais informações sobre layout e cenários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consulte [Tipografia no WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>O Objeto GlyphRun  
 O objeto <xref:System.Windows.Media.GlyphRun> representa uma sequência de glifos de uma única face de uma única fonte em um único tamanho e com um único estilo de renderização.  
  
 <xref:System.Windows.Media.GlyphRun> inclui os detalhes da fonte, como glifo <xref:System.Windows.Documents.Glyphs.Indices%2A> e posições de glifo individuais. Ele também inclui os pontos de código Unicode originais para os quais a execução foi gerada, informações de mapeamento de deslocamento de buffer de caractere para glifo e sinalizadores por caractere e por glifo.  
  
 <xref:System.Windows.Media.GlyphRun> tem uma <xref:System.Windows.FrameworkElement> de alto nível correspondente, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs> pode ser usada na árvore de elementos e na marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para representar <xref:System.Windows.Media.GlyphRun> saída.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>O Elemento Glyphs  
 O elemento <xref:System.Windows.Documents.Glyphs> representa a saída de um <xref:System.Windows.Media.GlyphRun> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. A sintaxe de marcação a seguir é usada para descrever o elemento <xref:System.Windows.Documents.Glyphs>.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 As seguintes definições de propriedade correspondem aos quatro primeiros atributos na marcação de exemplo.  
  
|propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Especifica um identificador de recurso: nome do arquivo, URI (Uniform Resource Identifier) da Web ou referência de recurso no Application. exe ou no contêiner.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Especifica o tamanho da fonte em unidades de superfície de desenho (o padrão é 0,96 polegadas).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Especifica os sinalizadores para estilos em negrito e itálico.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Especifica o nível de layout bidirecional. Valores pares e zero implicam um layout da esquerda para a direita; valores ímpares implicam um layout da direita para a esquerda.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Propriedade de índices  
 A propriedade <xref:System.Windows.Documents.Glyphs.Indices%2A> é uma cadeia de especificações de glifo. Quando uma sequência de glifos forma um único cluster, a especificação do primeiro glifo no cluster será precedida por uma especificação de quantos glifos e quantos pontos de código se combinam para formar o cluster. A propriedade <xref:System.Windows.Documents.Glyphs.Indices%2A> coleta em uma cadeia de caracteres as propriedades a seguir.  
  
- Índices de glifo  
  
- Larguras de avanço de glifo  
  
- Combinando vetores de anexo de glifo  
  
- Mapeamento de cluster de pontos de código para glifos  
  
- Sinalizadores de glifo  
  
 Cada especificação de glifo tem o seguinte formato.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Métricas de glifo  
 Cada glifo define as métricas que especificam como ela se alinha com outras <xref:System.Windows.Documents.Glyphs>. O gráfico a seguir define as várias qualidades tipográficas de dois caracteres de glifo diferentes.  
  
 ![Diagraph de medidas de glifo](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Marcação de glifos  
 O exemplo de código a seguir mostra como usar várias propriedades do elemento <xref:System.Windows.Documents.Glyphs> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Consulte também

- [Tipografia no WPF](typography-in-wpf.md)
- [Documentos no WPF](documents-in-wpf.md)
- [Texto](optimizing-performance-text.md)
