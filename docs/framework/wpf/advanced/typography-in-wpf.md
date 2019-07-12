---
title: Tipografia no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 94937b2c3e6935474d337c62bfd6698441dfcc2e
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860103"
---
# <a name="typography-in-wpf"></a>Tipografia no WPF
Este tópico apresenta os principais recursos tipográficos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Esses recursos incluem melhor qualidade e desempenho de renderização de texto, [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] suporte a tipografia, texto internacional aperfeiçoado, suporte de fonte aperfeiçoado e APIs (interfaces de programação de aplicativo).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Melhor qualidade e desempenho de texto  
 Texto no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é processado usando [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], que melhora a clareza e legibilidade do texto. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] é uma tecnologia de software desenvolvida por [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)], que melhora a legibilidade do texto em monitores LCD existentes, como telas de notebook, telas de Pocket PC e monitores de tela plana. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] utiliza uma renderização subpixel que permite que o texto seja exibido com maior fidelidade para sua forma verdadeira alinhando caracteres numa parte fracionária de um pixel. A resolução extra aumenta a nitidez dos detalhes mínimos na exibição de texto, tornando a leitura por longos períodos muito mais fácil. Outra melhoria de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é a suavização na direção y, que ajusta a parte superior e inferior de curvas rasas em caracteres de texto. Para obter mais detalhes sobre recursos [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], consulte [visão geral de ClearType](cleartype-overview.md).  
  
 ![Texto com suavização para direção de y de ClearType](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Texto com suavização da direção y do ClearType  
  
 O pipeline de renderização do texto inteiro pode ser acelerado por hardware em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desde que seu computador satisfaça o nível mínimo de hardware requerido. Renderização que não pode ser executada usando hardware cai para renderização de software. Aceleração por hardware afeta todas as fases do pipeline de processamento de texto — desde armazenar glifos individuais, compor glifos em sequências, aplicar efeitos, para aplicar o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] algoritmo de mesclagem na saída final exibida. Para obter mais informações sobre aceleração de hardware, consulte [camadas de renderização de gráficos](graphics-rendering-tiers.md).  
  
 ![Diagrama do pipeline de renderização de texto](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Além disso, texto animado, seja por caractere ou glifo, tira total proveito dos gráficos de capacidade de hardware habilitada por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Isso resulta em animação de texto suave.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Tipografia rica  
 O [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] formato de fonte é uma extensão do formato de fonte [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]. O formato de fonte [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] foi desenvolvido em conjunto pela [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] e a Adobe e fornece um conjunto rico de características tipográficas avançadas. O <xref:System.Windows.Documents.Typography> objeto expõe a muitos dos recursos avançados do [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] fontes, como alternativas estilísticas. O [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] fornece um conjunto de fontes de amostra [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] que são criadas com recursos avançados, como as fontes Pericles e Pescadero. Para obter mais informações, consulte [Pacote de fontes OpenType de amostra](sample-opentype-font-pack.md).  
  
 A fonte Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] contém glifos adicionais que fornecem alternativos estilísticos para o conjunto padrão de glifos. O texto a seguir exibe glifos alternativos estilísticos.  
  
 ![Texto usando glifos alternativos estilísticos OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "texto usando glifos alternativos estilísticos OpenType")  
  
 Swashes são glifos decorativos que utilizam ornamentação elaborada, geralmente associada à caligrafia. O texto a seguir exibe glifos padrão e swash para a fonte Pescadero.  
  
 ![Texto usando glifos padrão e swash OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "texto usando glifos padrão e swash OpenType")  
  
 Para obter mais detalhes sobre recursos [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)], consulte [Recursos da fonte OpenType](opentype-font-features.md).  
  
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
  
- Separado <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>, e <xref:System.Windows.FontStyle> tipos para definir um <xref:System.Windows.Media.FontFamily>. Isso fornece maior flexibilidade do que na programação [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], em que as combinações boolianas de negrito e itálico são utilizadas para definir uma família de fontes.  
  
- Direção de escrita (horizontal versus vertical) manipulada de forma independente do nome da fonte.  
  
- Vinculação e Fallback de fonte em um arquivo portátil [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], usando a tecnologia de fonte composta. Fontes compostas permitem a construção de fontes multilíngue de alcance completo. Fontes compostas também fornecem um mecanismo que evita exibir glifos que faltam. Para obter mais informações, consulte os comentários no <xref:System.Windows.Media.FontFamily> classe.  
  
- Fontes internacionais criadas por meio de fontes compostas, utilizando um grupo de fontes de único idioma. Isso economiza recurso ao desenvolver fontes para múltiplos idiomas.  
  
- Fontes compostas inseridas em um documento, fornecendo assim portabilidade ao documento. Para obter mais informações, consulte os comentários no <xref:System.Windows.Media.FontFamily> classe.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Novas Interfaces de programação de aplicativo texto (APIs)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece o texto de várias APIs para desenvolvedores utilizarem ao incluir texto em seus aplicativos. Essas APIs são agrupadas em três categorias:  
  
- **Layout e interface do usuário**. Controles de texto comuns para o [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
- **Desenho de texto leve**. Permite que você desenhe texto diretamente a objetos.  
  
- **Formatação de texto avançada**. Permite que você implemente um mecanismo de texto personalizado.  
  
### <a name="layout-and-user-interface"></a>Layout e interface do usuário  
 O nível mais alto de funcionalidade, as APIs de texto fornecem comum [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] controles como <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, e <xref:System.Windows.Controls.TextBox>. Esses controles fornecem os elementos básicos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dentro de um aplicativo e oferecem uma maneira fácil de apresentar e interagir com texto. Controles como <xref:System.Windows.Controls.RichTextBox> e <xref:System.Windows.Controls.PasswordBox> habilitar mais avançado ou especializado de manipulação de texto. E classes como <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, e <xref:System.Windows.Documents.TextPointer> habilitar a manipulação de texto útil. Eles [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controles fornecem propriedades tais como <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, e <xref:System.Windows.Controls.Control.FontStyle%2A>, que permitem que você controle a fonte que é usada para renderizar o texto.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Usando efeitos de Bitmap, transformações e efeitos de texto  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite que você crie usos visualmente interessantes de texto utilizando características como efeitos de bitmap, transformações e efeitos de texto. O exemplo a seguir mostra um tipo comum de um efeito de sombra aplicado a texto.  
  
 ![Sombra de texto com Suavidade &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
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
  
 Um <xref:System.Windows.Media.TextEffect> objeto é um objeto auxiliar que permite que você trate texto como um ou mais grupos de caracteres em uma cadeia de caracteres de texto. O exemplo a seguir mostra um caractere individual sendo rotacionado. Cada caractere é rotacionado de forma independente em intervalos de 1 segundo.  
  
 ![Captura de tela do efeito de texto girar texto](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Usando os documentos de fluxo  
 Além do comum [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece um controle de layout para apresentação de texto — o <xref:System.Windows.Documents.FlowDocument> elemento. O <xref:System.Windows.Documents.FlowDocument> elemento, em conjunto com o <xref:System.Windows.Controls.DocumentViewer> elemento, fornece um controle para grandes quantidades de texto com diferentes requisitos de layout. Controles de layout fornecem acesso a tipografia avançada através do <xref:System.Windows.Documents.Typography> objeto e propriedades relacionadas a fonte dos outros [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controles.  
  
 O exemplo a seguir mostra o conteúdo de texto hospedado em um <xref:System.Windows.Controls.FlowDocumentReader>, que fornece pesquisa, navegação, paginação e suporte a dimensionamento de conteúdo.  
  
 ![Captura de tela que mostra as fontes OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Para obter mais informações, consulte [Documentos no WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Desenho de texto leve  
 Você pode desenhar texto diretamente para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos usando o <xref:System.Windows.Media.DrawingContext.DrawText%2A> método o <xref:System.Windows.Media.DrawingContext> objeto. Para usar esse método, você cria um <xref:System.Windows.Media.FormattedText> objeto. Esse objeto permite que você desenhe texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. A funcionalidade do <xref:System.Windows.Media.FormattedText> objeto contém muito da funcionalidade dos sinalizadores de DrawText na API do Windows. Além disso, o <xref:System.Windows.Media.FormattedText> objeto contém a funcionalidade, como suporte a reticências, no qual reticências são exibidas quando o texto excede seu limite. O exemplo a seguir mostra o texto que tem diversos formatos aplicados a ele, incluindo um gradiente linear na segunda e terceira palavras.  
  
 ![Texto exibido utilizando objeto FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Você pode converter texto formatado em <xref:System.Windows.Media.Geometry> objetos, permitindo que você crie outros tipos de texto visualmente interessantes. Por exemplo, você pode criar um <xref:System.Windows.Media.Geometry> objeto com base no contorno de uma cadeia de caracteres de texto.  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais interessantes modificando o traço, o preenchimento e o realce do texto convertido.  
  
 ![Texto com diferentes cores de preenchimento e traço](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texto com pincel de imagem aplicado para traçar e realce](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Para obter mais informações sobre o <xref:System.Windows.Media.FormattedText> do objeto, consulte [Desenhando texto formatado](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Formatação de texto avançada  
 Mais avançado nível do texto APIs, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece a capacidade de criar o layout de texto personalizado usando o <xref:System.Windows.Media.TextFormatting.TextFormatter> objeto e outros tipos no <xref:System.Windows.Media.TextFormatting> namespace. O <xref:System.Windows.Media.TextFormatting.TextFormatter> e classes associadas permitem que você implemente layout de texto personalizado que dá suporte a sua própria definição de formatos de caractere, estilos de parágrafo, regras de quebra de linha e outras características de layout para texto internacional. Há poucos casos em que você desejaria substituir a implementação padrão do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suporte ao layout de texto. No entanto, se você estivesse criando um aplicativo ou controle de edição de texto, poderia exigir uma implementação diferente da implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão.  
  
 Ao contrário de um texto tradicional [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], o <xref:System.Windows.Media.TextFormatting.TextFormatter> interage com um cliente de layout de texto por meio de um conjunto de métodos de retorno de chamada. Requer que o cliente forneça esses métodos em uma implementação da <xref:System.Windows.Media.TextFormatting.TextSource> classe. O diagrama a seguir ilustra a interação de layout de texto entre o aplicativo cliente e <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagrama de cliente de layout de texto e TextFormatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Para obter mais detalhes sobre como criar o layout de texto personalizado, consulte [formatação de texto avançada](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [Visão geral de ClearType](cleartype-overview.md)
- [Recursos de fonte OpenType](opentype-font-features.md)
- [Desenhando texto formatado](drawing-formatted-text.md)
- [Formatação de texto avançada](advanced-text-formatting.md)
- [Texto](optimizing-performance-text.md)
- [Tipografia da Microsoft](https://docs.microsoft.com/typography/)
