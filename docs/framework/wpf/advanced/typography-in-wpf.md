---
title: Tipografia
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 501a4221c99d405484a2fb908641d27d1f38f266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187344"
---
# <a name="typography-in-wpf"></a>Tipografia no WPF
Este tópico apresenta os principais recursos tipográficos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Esses recursos incluem melhor qualidade e desempenho da renderização de texto, suporte à tipografia OpenType, texto internacional aprimorado, suporte aprimorado à fonte e novas APIs (Text Application Programming Interfaces, interfaces de programação de aplicativos de texto).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>
## <a name="improved-quality-and-performance-of-text"></a>Melhor qualidade e desempenho de texto  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] texto é renderizado usando o Microsoft ClearType, o que melhora a clareza e a legibilidade do texto. ClearType é uma tecnologia de software desenvolvida pela Microsoft que melhora a legibilidade do texto em LCDs existentes (Liquid Crystal Displays), como telas de laptop, telas de Pocket PC e monitores de tela plana. O ClearType usa renderização de subpixel que permite que o texto seja exibido com uma maior fidelidade à sua verdadeira forma, alinhando caracteres em uma parte fracionada de um pixel. A resolução extra aumenta a nitidez dos detalhes mínimos na exibição de texto, tornando a leitura por longos períodos muito mais fácil. Outra melhoria do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType é o anti-aliasing de direção y, que suaviza os topos e fundos de curvas rasas em caracteres de texto. Para obter mais detalhes sobre os recursos do ClearType, consulte [ClearType Overview](cleartype-overview.md).  
  
 ![Texto com contra-aliasing clearType y-direction](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Texto com suavização da direção y do ClearType  
  
 O pipeline de renderização do texto inteiro pode ser acelerado por hardware em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desde que seu computador satisfaça o nível mínimo de hardware requerido. Renderização que não pode ser executada usando hardware cai para renderização de software. A aceleração do hardware afeta todas as fases do pipeline de renderização de texto — desde armazenar glifos individuais, compor glifos em gifas, aplicar efeitos, até aplicar o algoritmo de mistura ClearType à saída final exibida. Para obter mais informações sobre aceleração de hardware, consulte [camadas de renderização de gráficos](graphics-rendering-tiers.md).  
  
 ![Diagrama do pipeline de renderização de texto](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Além disso, texto animado, seja por caractere ou glifo, tira total proveito dos gráficos de capacidade de hardware habilitada por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Isso resulta em animação de texto suave.  
  
<a name="Rich_Typography"></a>
## <a name="rich-typography"></a>Tipografia rica  
 O formato de fonte OpenType é uma extensão do formato de fonte TrueType®. O formato de fonte OpenType foi desenvolvido em conjunto pela Microsoft e a Adobe, e fornece uma rica variedade de recursos tipográficos avançados. O <xref:System.Windows.Documents.Typography> objeto expõe muitas das características avançadas das fontes OpenType, como alternativas estilísticas e swashes. O Windows SDK fornece um conjunto de fontes OpenType de exemplo que são projetadas com recursos ricos, como as fontes Péricles e Pescadero. Para obter mais informações, consulte [Sample OpenType Font Pack](sample-opentype-font-pack.md).  
  
 A fonte Péricles OpenType contém glifos adicionais que fornecem alternativas estilísticas ao conjunto padrão de glifos. O texto a seguir exibe glifos alternativos estilísticos.  
  
 ![Texto usando glifos alternativos estilísticos OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Texto usando glifos alternativos estilísticos OpenType")  
  
 Swashes são glifos decorativos que utilizam ornamentação elaborada, geralmente associada à caligrafia. O texto a seguir exibe glifos padrão e swash para a fonte Pescadero.  
  
 ![Texto usando glifos padrão e swash OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Texto usando glifos padrão e swash OpenType")  
  
 Para obter mais detalhes sobre os recursos do OpenType, consulte [OpenType Font Features](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>
## <a name="enhanced-international-text-support"></a>Suporte a texto internacional melhorado  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece suporte a texto internacional melhorado fornecendo os seguintes recursos:  
  
- Espaçamento automático em todos os sistemas de escrita, utilizando medida adaptativa.  
  
- Amplo suporte a texto internacional. Para obter mais informações, consulte [globalização do WPF](globalization-for-wpf.md).  
  
- Quebra de linha orientada pelo idioma, hifenização e justificação.  
  
<a name="Enhanced_Font_Support"></a>
## <a name="enhanced-font-support"></a>Suporte a fonte melhorado  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece suporte a fonte melhorado fornecendo os seguintes recursos:  
  
- Unicode para todo o texto. Comportamento de fonte e a seleção não requerem charset ou codepage.  
  
- Comportamento de fonte independente de configurações globais, como localidade do sistema.  
  
- Separar <xref:System.Windows.FontWeight> <xref:System.Windows.FontStretch>, <xref:System.Windows.FontStyle> e tipos <xref:System.Windows.Media.FontFamily>para definir um . Isso fornece maior flexibilidade do que na programação Win32, na qual combinações booleanas de itálico e negrito são usadas para definir uma família de fontes.  
  
- Direção de escrita (horizontal versus vertical) manipulada de forma independente do nome da fonte.  
  
- Vinculação de fontes e recuo de fonte em um arquivo XML portátil, usando a tecnologia de fonte composta. Fontes compostas permitem a construção de fontes multilíngue de alcance completo. Fontes compostas também fornecem um mecanismo que evita exibir glifos que faltam. Para obter mais informações, consulte <xref:System.Windows.Media.FontFamily> as observações na classe.  
  
- Fontes internacionais criadas por meio de fontes compostas, utilizando um grupo de fontes de único idioma. Isso economiza recurso ao desenvolver fontes para múltiplos idiomas.  
  
- Fontes compostas inseridas em um documento, fornecendo assim portabilidade ao documento. Para obter mais informações, consulte <xref:System.Windows.Media.FontFamily> as observações na classe.  
  
<a name="New_Text_APIs"></a>
## <a name="new-text-application-programming-interfaces-apis"></a>Novas Interfaces de programação de aplicativo texto (APIs)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece várias APIs de texto para os desenvolvedores usarem ao incluir texto em seus aplicativos. Essas APIs são agrupadas em três categorias:  
  
- **Layout e interface de usuário**. Os controles de texto comuns para a interface gráfica do usuário (GUI).  
  
- **Desenho de texto leve**. Permite que você desenhe texto diretamente a objetos.  
  
- **Formatação de texto avançada**. Permite que você implemente um mecanismo de texto personalizado.  
  
### <a name="layout-and-user-interface"></a>Layout e interface do usuário  
 No mais alto nível de funcionalidade, as [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] APIs de <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>texto <xref:System.Windows.Controls.TextBox>fornecem controles comuns, tais como , e . Esses controles fornecem os elementos básicos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dentro de um aplicativo e oferecem uma maneira fácil de apresentar e interagir com texto. Controles como <xref:System.Windows.Controls.RichTextBox> e <xref:System.Windows.Controls.PasswordBox> permitem um manuseio de texto mais avançado ou especializado. E classes <xref:System.Windows.Documents.TextRange>como <xref:System.Windows.Documents.TextSelection>, <xref:System.Windows.Documents.TextPointer> e permitem manipulação de texto útil. Esses [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controles fornecem propriedades <xref:System.Windows.Controls.Control.FontFamily%2A> <xref:System.Windows.Controls.Control.FontSize%2A>como <xref:System.Windows.Controls.Control.FontStyle%2A>, e , que permitem controlar a fonte que é usada para renderizar o texto.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Usando efeitos de Bitmap, transformações e efeitos de texto  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite que você crie usos visualmente interessantes de texto utilizando características como efeitos de bitmap, transformações e efeitos de texto. O exemplo a seguir mostra um tipo comum de um efeito de sombra aplicado a texto.  
  
 ![Sombra de texto com Maciez &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg)
  
 O exemplo a seguir mostra um efeito de sombra e ruído aplicado ao texto.  
  
 ![Sombra de texto com ruído](./media/typography-in-wpf/drop-shadow-noise-text.jpg)
  
 O exemplo a seguir mostra um efeito de brilho externo aplicado ao texto.  
  
 ![Sombra de texto usando OuterGlowBitmapEffect](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.  
  
 ![Sombra de texto usando BlurBitmapEffect](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 O exemplo a seguir mostra a segunda linha de texto com escala ajustada em 150% no eixo x e a terceira linha de texto ajustada em 150% no eixo y.  
  
 ![Texto com escala ajustada usando um ScaleTransform](./media/typography-in-wpf/scaled-text-scaletransform.jpg)
  
 O exemplo a seguir mostra texto distorcido ao longo do eixo x.  
  
 ![Texto distorcido usando SkewTransform](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 Um <xref:System.Windows.Media.TextEffect> objeto é um objeto auxiliar que permite tratar o texto como um ou mais grupos de caracteres em uma seqüência de texto. O exemplo a seguir mostra um caractere individual sendo rotacionado. Cada caractere é rotacionado de forma independente em intervalos de 1 segundo.  
  
 ![Captura de tela do efeito de girar o texto](./media/typography-in-wpf/rotating-text-effect.jpg)
  
#### <a name="using-flow-documents"></a>Usando os documentos de fluxo  
 Além dos controles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] comuns, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece um controle de <xref:System.Windows.Documents.FlowDocument> layout para apresentação de texto — o elemento. O <xref:System.Windows.Documents.FlowDocument> elemento, em <xref:System.Windows.Controls.DocumentViewer> conjunto com o elemento, fornece um controle para grandes quantidades de texto com diferentes requisitos de layout. Os controles de layout fornecem acesso <xref:System.Windows.Documents.Typography> à tipografia avançada através [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do objeto e propriedades relacionadas à fonte de outros controles.  
  
 O exemplo a seguir mostra <xref:System.Windows.Controls.FlowDocumentReader>o conteúdo de texto hospedado em um , que fornece suporte de pesquisa, navegação, paginação e dimensionamento de conteúdo.  
  
 ![Captura de tela que mostra fontes OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Para obter mais informações, consulte [Documentos no WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Desenho de texto leve  
 Você pode desenhar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] texto diretamente <xref:System.Windows.Media.DrawingContext.DrawText%2A> para objetos usando o método do <xref:System.Windows.Media.DrawingContext> objeto. Para usar este método, <xref:System.Windows.Media.FormattedText> você cria um objeto. Esse objeto permite que você desenhe texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. A funcionalidade do <xref:System.Windows.Media.FormattedText> objeto contém grande parte da funcionalidade dos sinalizadores DrawText na API do Windows. Além disso, <xref:System.Windows.Media.FormattedText> o objeto contém funcionalidades como suporte a elipses, em que uma elipse é exibida quando o texto excede seus limites. O exemplo a seguir mostra o texto que tem diversos formatos aplicados a ele, incluindo um gradiente linear na segunda e terceira palavras.  
  
 ![Texto exibido usando o objeto FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)
  
 Você pode converter texto <xref:System.Windows.Media.Geometry> formatado em objetos, permitindo criar outros tipos de texto visualmente interessante. Por exemplo, você <xref:System.Windows.Media.Geometry> pode criar um objeto com base no contorno de uma seqüência de texto.  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais interessantes modificando o traço, o preenchimento e o realce do texto convertido.  
  
 ![Texto com diferentes cores de preenchimento e traço](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texto com pincel de imagem aplicado ao traçado e destaque](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Para obter mais <xref:System.Windows.Media.FormattedText> informações sobre o objeto, consulte [Desenho de texto formatado](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Formatação de texto avançada  
 No nível mais avançado das APIs de texto, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece a capacidade <xref:System.Windows.Media.TextFormatting.TextFormatter> de criar layout <xref:System.Windows.Media.TextFormatting> de texto personalizado usando o objeto e outros tipos no namespace. As <xref:System.Windows.Media.TextFormatting.TextFormatter> classes associadas permitem que você implemente um layout de texto personalizado que suporte sua própria definição de formatos de caracteres, estilos de parágrafo, regras de quebra de linha e outros recursos de layout para texto internacional. Há poucos casos em que você desejaria substituir a implementação padrão do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suporte ao layout de texto. No entanto, se você estivesse criando um aplicativo ou controle de edição de texto, poderia exigir uma implementação diferente da implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão.  
  
 Ao contrário de uma <xref:System.Windows.Media.TextFormatting.TextFormatter> API de texto tradicional, a interação com um cliente de layout de texto através de um conjunto de métodos de retorno de chamada. Exige que o cliente forneça esses métodos <xref:System.Windows.Media.TextFormatting.TextSource> em uma implementação da classe. O diagrama a seguir ilustra a interação <xref:System.Windows.Media.TextFormatting.TextFormatter>do layout de texto entre o aplicativo cliente e .  
  
 ![Diagrama de cliente de layout de texto e TextFormatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Para obter mais detalhes sobre como criar o layout de texto personalizado, consulte [formatação de texto avançada](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [Visão geral de ClearType](cleartype-overview.md)
- [Recursos de fonte OpenType](opentype-font-features.md)
- [Desenhando texto formatado](drawing-formatted-text.md)
- [Formatação avançada de texto](advanced-text-formatting.md)
- [Texto](optimizing-performance-text.md)
- [Tipografia da Microsoft](https://docs.microsoft.com/typography/)
