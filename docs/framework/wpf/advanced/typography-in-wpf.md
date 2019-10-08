---
title: Tipografia no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 11087ed4da23d73fc8edc36680dd1b3587c011ce
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004918"
---
# <a name="typography-in-wpf"></a>Tipografia no WPF
Este tópico apresenta os principais recursos tipográficos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Esses recursos incluem qualidade e desempenho aprimorados de renderização de texto, suporte a tipografia OpenType, texto internacional aprimorado, suporte avançado a fontes e novas APIs (interfaces de programação de aplicativo) de texto.  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Melhor qualidade e desempenho de texto  
 O texto no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é renderizado usando o Microsoft ClearType, o que aumenta a clareza e a legibilidade do texto. O ClearType é uma tecnologia de software desenvolvida pela Microsoft que melhora a legibilidade do texto em LCDs existentes (monitores Liquid Crystal), como telas de laptops, telas de Pocket PC e monitores de tela plana. O ClearType usa renderização de sub-pixel, que permite que o texto seja exibido com uma maior fidelidade à sua forma verdadeira alinhando caracteres em uma parte fracionária de um pixel. A resolução extra aumenta a nitidez dos detalhes mínimos na exibição de texto, tornando a leitura por longos períodos muito mais fácil. Outra melhoria do ClearType no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é a suavização da direção y, que suaviza as partes superiores e inferiores das curvas superficiais em caracteres de texto. Para obter mais detalhes sobre os recursos de ClearType, consulte [visão geral de ClearType](cleartype-overview.md).  
  
 ![Texto com suavização de direção y ClearType](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Texto com suavização da direção y do ClearType  
  
 O pipeline de renderização do texto inteiro pode ser acelerado por hardware em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desde que seu computador satisfaça o nível mínimo de hardware requerido. Renderização que não pode ser executada usando hardware cai para renderização de software. A aceleração de hardware afeta todas as fases do pipeline de renderização de texto — desde o armazenamento de glifos individuais, a composição de glifos em execuções de glifos, a aplicação de efeitos, a aplicação do algoritmo de mesclagem ClearType à saída final exibida. Para obter mais informações sobre aceleração de hardware, consulte [camadas de renderização de gráficos](graphics-rendering-tiers.md).  
  
 ![Diagrama do pipeline de renderização de texto](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Além disso, texto animado, seja por caractere ou glifo, tira total proveito dos gráficos de capacidade de hardware habilitada por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Isso resulta em animação de texto suave.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Tipografia rica  
 O formato de fonte OpenType é uma extensão do formato de fonte TrueType®. O formato de fonte OpenType foi desenvolvido em conjunto pela Microsoft e pela Adobe e fornece uma variedade avançada de recursos tipográficos avançados. O objeto <xref:System.Windows.Documents.Typography> expõe muitos dos recursos avançados das fontes OpenType, como alternativas estilísticos e traços violentos. O SDK do Windows fornece um conjunto de fontes OpenType de exemplo que são projetadas com recursos avançados, como as fontes Pericles e Pescadero. Para obter mais informações, consulte [Pacote de fontes OpenType de amostra](sample-opentype-font-pack.md).  
  
 A fonte OpenType de Pericles contém glifos adicionais que fornecem alternativas estilísticos ao conjunto padrão de glifos. O texto a seguir exibe glifos alternativos estilísticos.  
  
 ![Texto usando glifos alternativos de texto alternativo OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "usando glifos alternativos estilísticos OpenType")  
  
 Swashes são glifos decorativos que utilizam ornamentação elaborada, geralmente associada à caligrafia. O texto a seguir exibe os glifos padrão e Swash para a fonte Pescadero.  
  
 ![Texto usando glifos OpenType padrão e traços violentos](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "usando glifos OpenType padrão e Swash")  
  
 Para obter mais detalhes sobre os recursos do OpenType, consulte [recursos de fonte OpenType](opentype-font-features.md).  
  
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
  
- Separe os tipos <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch> e <xref:System.Windows.FontStyle> para definir um <xref:System.Windows.Media.FontFamily>. Isso fornece maior flexibilidade do que na programação [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], em que as combinações boolianas de negrito e itálico são utilizadas para definir uma família de fontes.  
  
- Direção de escrita (horizontal versus vertical) manipulada de forma independente do nome da fonte.  
  
- Vinculação e Fallback de fonte em um arquivo portátil [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], usando a tecnologia de fonte composta. Fontes compostas permitem a construção de fontes multilíngue de alcance completo. Fontes compostas também fornecem um mecanismo que evita exibir glifos que faltam. Para obter mais informações, consulte os comentários na classe <xref:System.Windows.Media.FontFamily>.  
  
- Fontes internacionais criadas por meio de fontes compostas, utilizando um grupo de fontes de único idioma. Isso economiza recurso ao desenvolver fontes para múltiplos idiomas.  
  
- Fontes compostas inseridas em um documento, fornecendo assim portabilidade ao documento. Para obter mais informações, consulte os comentários na classe <xref:System.Windows.Media.FontFamily>.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Novas Interfaces de programação de aplicativo texto (APIs)  
 o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece várias APIs de texto para os desenvolvedores usarem ao incluir texto em seus aplicativos. Essas APIs são agrupadas em três categorias:  
  
- **Layout e interface do usuário**. Os controles de texto comuns para a GUI (interface gráfica do usuário).  
  
- **Desenho de texto leve**. Permite que você desenhe texto diretamente a objetos.  
  
- **Formatação de texto avançada**. Permite que você implemente um mecanismo de texto personalizado.  
  
### <a name="layout-and-user-interface"></a>Layout e interface do usuário  
 No nível mais alto de funcionalidade, as APIs de texto fornecem controles [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] comuns, como <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Controls.TextBox>. Esses controles fornecem os elementos básicos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dentro de um aplicativo e oferecem uma maneira fácil de apresentar e interagir com texto. Controles como <xref:System.Windows.Controls.RichTextBox> e <xref:System.Windows.Controls.PasswordBox> permitem manipulação de texto mais avançada ou especializada. E classes como <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection> e <xref:System.Windows.Documents.TextPointer> habilitam a manipulação de texto útil. Esses controles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fornecem propriedades como <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A> e <xref:System.Windows.Controls.Control.FontStyle%2A>, que permitem controlar a fonte usada para renderizar o texto.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Usando efeitos de Bitmap, transformações e efeitos de texto  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite que você crie usos visualmente interessantes de texto utilizando características como efeitos de bitmap, transformações e efeitos de texto. O exemplo a seguir mostra um tipo comum de um efeito de sombra aplicado a texto.  
  
 ![Sombra de texto com suavidade &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
 O exemplo a seguir mostra um efeito de sombra e ruído aplicado ao texto.  
  
 ![Sombra de texto com ruído](./media/typography-in-wpf/drop-shadow-noise-text.jpg) 
  
 O exemplo a seguir mostra um efeito de brilho externo aplicado ao texto.  
  
 ![Sombra de texto usando um OuterGlowBitmapEffect](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.  
  
 ![Sombra de texto usando um BlurBitmapEffect](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 O exemplo a seguir mostra a segunda linha de texto com escala ajustada em 150% no eixo x e a terceira linha de texto ajustada em 150% no eixo y.  
  
 ![Texto dimensionado usando um ScaleTransform](./media/typography-in-wpf/scaled-text-scaletransform.jpg) 
  
 O exemplo a seguir mostra texto distorcido ao longo do eixo x.  
  
 ![Texto inclinado usando SkewTransform](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 Um objeto <xref:System.Windows.Media.TextEffect> é um objeto auxiliar que permite tratar o texto como um ou mais grupos de caracteres em uma cadeia de texto. O exemplo a seguir mostra um caractere individual sendo rotacionado. Cada caractere é rotacionado de forma independente em intervalos de 1 segundo.  
  
 ![Captura de tela do texto de rotação do efeito de texto](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Usando os documentos de fluxo  
 Além dos controles comuns de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece um controle de layout para a apresentação de texto — o elemento <xref:System.Windows.Documents.FlowDocument>. O elemento <xref:System.Windows.Documents.FlowDocument>, em conjunto com o elemento <xref:System.Windows.Controls.DocumentViewer>, fornece um controle para grandes quantidades de texto com requisitos de layout variáveis. Os controles de layout fornecem acesso à tipografia avançada por meio do objeto <xref:System.Windows.Documents.Typography> e propriedades relacionadas à fonte de outros controles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 O exemplo a seguir mostra o conteúdo de texto hospedado em um <xref:System.Windows.Controls.FlowDocumentReader>, que fornece suporte de pesquisa, navegação, paginação e dimensionamento de conteúdo.  
  
 ![Captura de tela que mostra as fontes OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Para obter mais informações, consulte [Documentos no WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Desenho de texto leve  
 Você pode desenhar texto diretamente em objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando o método <xref:System.Windows.Media.DrawingContext.DrawText%2A> do objeto <xref:System.Windows.Media.DrawingContext>. Para usar esse método, você cria um objeto <xref:System.Windows.Media.FormattedText>. Esse objeto permite que você desenhe texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. A funcionalidade do objeto <xref:System.Windows.Media.FormattedText> contém grande parte da funcionalidade dos sinalizadores DrawText na API do Windows. Além disso, o objeto <xref:System.Windows.Media.FormattedText> contém funcionalidades, como suporte a reticências, em que uma elipse é exibida quando o texto excede seus limites. O exemplo a seguir mostra o texto que tem diversos formatos aplicados a ele, incluindo um gradiente linear na segunda e terceira palavras.  
  
 ![Texto exibido usando o objeto FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Você pode converter texto formatado em objetos <xref:System.Windows.Media.Geometry>, permitindo que você crie outros tipos de texto visualmente interessante. Por exemplo, você pode criar um objeto <xref:System.Windows.Media.Geometry> com base no contorno de uma cadeia de texto.  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais interessantes modificando o traço, o preenchimento e o realce do texto convertido.  
  
 ![Texto com cores diferentes para preenchimento e traço](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texto com pincel de imagem aplicado a Stroke e realce](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Para obter mais informações sobre o objeto <xref:System.Windows.Media.FormattedText>, consulte [desenho de texto formatado](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Formatação de texto avançada  
 No nível mais avançado das APIs de texto, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece a capacidade de criar layout de texto personalizado usando o objeto <xref:System.Windows.Media.TextFormatting.TextFormatter> e outros tipos no namespace <xref:System.Windows.Media.TextFormatting>. O <xref:System.Windows.Media.TextFormatting.TextFormatter> e as classes associadas permitem que você implemente o layout de texto personalizado que dá suporte à sua própria definição de formatos de caractere, estilos de parágrafo, regras de quebra de linha e outros recursos de layout para texto internacional. Há poucos casos em que você desejaria substituir a implementação padrão do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suporte ao layout de texto. No entanto, se você estivesse criando um aplicativo ou controle de edição de texto, poderia exigir uma implementação diferente da implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão.  
  
 Ao contrário de uma API de texto tradicional, o <xref:System.Windows.Media.TextFormatting.TextFormatter> interage com um cliente de layout de texto por meio de um conjunto de métodos de retorno de chamada. Ele requer que o cliente forneça esses métodos em uma implementação da classe <xref:System.Windows.Media.TextFormatting.TextSource>. O diagrama a seguir ilustra a interação de layout de texto entre o aplicativo cliente e <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagrama de cliente de layout de texto e TextFormatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Para obter mais detalhes sobre como criar o layout de texto personalizado, consulte [formatação de texto avançada](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [Visão geral de ClearType](cleartype-overview.md)
- [Recursos de fonte OpenType](opentype-font-features.md)
- [Desenhando texto formatado](drawing-formatted-text.md)
- [Formatação de texto avançada](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Tipografia da Microsoft](https://docs.microsoft.com/typography/)
