---
title: Tipografia no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 45f74a4dd2164f332314ad79a18eab49efb520d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549121"
---
# <a name="typography-in-wpf"></a>Tipografia no WPF
Este tópico apresenta os principais recursos tipográficos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Esses recursos incluem melhor qualidade e desempenho de renderização de texto, [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] suporte a tipografia, texto internacional aperfeiçoado, suporte de fonte aperfeiçoado e APIs (interfaces de programação de aplicativo).  
  

  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Melhor qualidade e desempenho de texto  
 Texto no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é processado usando [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], que melhora a clareza e legibilidade do texto. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] é uma tecnologia de software desenvolvida por [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)], que melhora a legibilidade do texto em monitores LCD existentes, como telas de notebook, telas de Pocket PC e monitores de tela plana. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] utiliza uma renderização subpixel que permite que o texto seja exibido com maior fidelidade para sua forma verdadeira alinhando caracteres numa parte fracionária de um pixel. A resolução extra aumenta a nitidez dos detalhes mínimos na exibição de texto, tornando a leitura por longos períodos muito mais fácil. Outra melhoria de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é a suavização na direção y, que ajusta a parte superior e inferior de curvas rasas em caracteres de texto. Para obter mais detalhes sobre recursos [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], consulte [visão geral de ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 ![Texto com y ClearType&#45;direção anti&#45;alias](../../../../docs/framework/wpf/advanced/media/typographyinwpf02.gif "TypographyInWPF02")  
Texto com suavização da direção y do ClearType  
  
 O pipeline de renderização do texto inteiro pode ser acelerado por hardware em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desde que seu computador satisfaça o nível mínimo de hardware requerido. Renderização que não pode ser executada usando hardware cai para renderização de software. Aceleração por hardware afeta todas as fases do pipeline de processamento de texto — desde armazenar glifos individuais, compor glifos em sequências, aplicar efeitos, para aplicar o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] algoritmo de mesclagem na saída final exibida. Para obter mais informações sobre aceleração de hardware, consulte [camadas de renderização de gráficos](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 ![Diagrama do pipeline de renderização de texto](../../../../docs/framework/wpf/advanced/media/typographyinwpf01.png "TypographyInWPF01")  
Diagrama do pipeline de renderização de texto  
  
 Além disso, texto animado, seja por caractere ou glifo, tira total proveito dos gráficos de capacidade de hardware habilitada por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Isso resulta em animação de texto suave.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Tipografia rica  
 O [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] formato de fonte é uma extensão do formato de fonte [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]. O formato de fonte [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] foi desenvolvido em conjunto pela [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] e a Adobe e fornece um conjunto rico de características tipográficas avançadas. O <xref:System.Windows.Documents.Typography> objeto expõe a muitos dos recursos avançados do [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] fontes, como alternativas estilísticas. O [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] fornece um conjunto de fontes de amostra [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] que são criadas com recursos avançados, como as fontes Pericles e Pescadero. Para obter mais informações, consulte [Pacote de fontes OpenType de amostra](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 A fonte Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] contém glifos adicionais que fornecem alternativos estilísticos para o conjunto padrão de glifos. O texto a seguir exibe glifos alternativos estilísticos.  
  
 ![Texto usando glifos de alternativas estilísticos OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
Texto usando glifos alternativos estilísticos OpenType  
  
 Swashes são glifos decorativos que utilizam ornamentação elaborada, geralmente associada à caligrafia. O texto a seguir exibe glifos padrão e decorados para a fonte Pescadero.  
  
 ![Texto usando glifos de OpenType padrão e decorados](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
Texto usando glifos padrão e swash OpenType  
  
 Para obter mais detalhes sobre recursos [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)], consulte [Recursos da fonte OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Suporte a texto internacional melhorado  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece suporte a texto internacional melhorado fornecendo os seguintes recursos:  
  
-   Espaçamento automático em todos os sistemas de escrita, utilizando medida adaptativa.  
  
-   Amplo suporte a texto internacional. Para obter mais informações, consulte [globalização do WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md).  
  
-   Quebra de linha orientada pelo idioma, hifenização e justificação.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Suporte a fonte melhorado  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece suporte a fonte melhorado fornecendo os seguintes recursos:  
  
-   Unicode para todo o texto. Comportamento de fonte e a seleção não requerem charset ou codepage.  
  
-   Comportamento de fonte independente de configurações globais, como localidade do sistema.  
  
-   Separada <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>, e <xref:System.Windows.FontStyle> tipos para definir um <xref:System.Windows.Media.FontFamily>. Isso fornece maior flexibilidade do que na programação [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], em que as combinações boolianas de negrito e itálico são utilizadas para definir uma família de fontes.  
  
-   Direção de escrita (horizontal versus vertical) manipulada de forma independente do nome da fonte.  
  
-   Vinculação e Fallback de fonte em um arquivo portátil [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], usando a tecnologia de fonte composta. Fontes compostas permitem a construção de fontes multilíngue de alcance completo. Fontes compostas também fornecem um mecanismo que evita exibir glifos que faltam. Para obter mais informações, consulte os comentários na <xref:System.Windows.Media.FontFamily> classe.  
  
-   Fontes internacionais criadas por meio de fontes compostas, utilizando um grupo de fontes de único idioma. Isso economiza recurso ao desenvolver fontes para múltiplos idiomas.  
  
-   Fontes compostas inseridas em um documento, fornecendo assim portabilidade ao documento. Para obter mais informações, consulte os comentários na <xref:System.Windows.Media.FontFamily> classe.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Novas Interfaces de programação de aplicativo texto (APIs)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece vários textos [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] para desenvolvedores utilizarem ao incluir texto em seus aplicativos. Estes [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] são agrupados em três categorias:  
  
-   **Layout e interface do usuário**. Controles de texto comuns para o [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
-   **Desenho de texto leve**. Permite que você desenhe texto diretamente a objetos.  
  
-   **Formatação de texto avançada**. Permite que você implemente um mecanismo de texto personalizado.  
  
### <a name="layout-and-user-interface"></a>Layout e interface do usuário  
 O nível mais alto de funcionalidade, o texto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fornecer comuns [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] controles como <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, e <xref:System.Windows.Controls.TextBox>. Esses controles fornecem os elementos básicos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dentro de um aplicativo e oferecem uma maneira fácil de apresentar e interagir com texto. Controla como <xref:System.Windows.Controls.RichTextBox> e <xref:System.Windows.Controls.PasswordBox> habilitar mais avançado ou especializado de manipulação de texto. E classes como <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, e <xref:System.Windows.Documents.TextPointer> possibilitam manipulação útil de texto. Essas [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controles fornecem propriedades como <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, e <xref:System.Windows.Controls.Control.FontStyle%2A>, que permitem que você controle a fonte que é usada para renderizar o texto.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Usando efeitos de Bitmap, transformações e efeitos de texto  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite que você crie usos visualmente interessantes de texto utilizando características como efeitos de bitmap, transformações e efeitos de texto. O exemplo a seguir mostra um tipo comum de um efeito de sombra aplicado a texto.  
  
 ![Sombra de texto com Suavidade &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Texto com uma sombra  
  
 O exemplo a seguir mostra um efeito de sombra e ruído aplicado ao texto.  
  
 ![Sombra de texto com ruído](../../../../docs/framework/wpf/advanced/media/shadowtext04.jpg "ShadowText04")  
Texto com uma sombra e ruído  
  
 O exemplo a seguir mostra um efeito de brilho externo aplicado ao texto.  
  
 ![Sombra de texto usando OuterGlowBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext05.jpg "ShadowText05")  
Texto com um efeito de brilho externo  
  
 O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.  
  
 ![Sombra de texto usando BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Texto com um efeito de desfoque  
  
 O exemplo a seguir mostra a segunda linha de texto com escala ajustada em 150% no eixo x e a terceira linha de texto ajustada em 150% no eixo y.  
  
 ![Texto dimensionado usando ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Texto utilizando uma ScaleTransform  
  
 O exemplo a seguir mostra texto distorcido ao longo do eixo x.  
  
 ![Texto inclinado usando SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Texto utilizando uma SkewTransform  
  
 Um <xref:System.Windows.Media.TextEffect> objeto é um objeto auxiliar que permite que você trate texto como um ou mais grupos de caracteres em uma cadeia de caracteres de texto. O exemplo a seguir mostra um caractere individual sendo rotacionado. Cada caractere é rotacionado de forma independente em intervalos de 1 segundo.  
  
 ![Captura de tela de efeito de texto girar texto](../../../../docs/framework/wpf/advanced/media/texteffect01.jpg "TextEffect01")  
Exemplo de uma animação de efeito de giro  
  
#### <a name="using-flow-documents"></a>Usando os documentos de fluxo  
 Além de comuns [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controles, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece um controle de layout para apresentação de texto — o <xref:System.Windows.Documents.FlowDocument> elemento. O <xref:System.Windows.Documents.FlowDocument> elemento, em conjunto com o <xref:System.Windows.Controls.DocumentViewer> elemento, fornece um controle para grandes quantidades de texto com diversos requisitos de layout. Controles de layout fornecem acesso a tipografia avançada através de <xref:System.Windows.Documents.Typography> objeto e as propriedades relacionadas a fonte de outros [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controles.  
  
 O exemplo a seguir mostra o conteúdo de texto hospedado em um <xref:System.Windows.Controls.FlowDocumentReader>, que fornece pesquisa, navegação, paginação e suporte a dimensionamento de conteúdo.  
  
 ![Usando OpenType fontes captura de tela de exemplo](../../../../docs/framework/wpf/advanced/media/typographyinwpf-03.png "TypographyInWPF_03")  
Texto hospedado em um FlowDocumentReader  
  
 Para obter mais informações, consulte [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Desenho de texto leve  
 Você pode desenhar texto diretamente para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objetos usando o <xref:System.Windows.Media.DrawingContext.DrawText%2A> método do <xref:System.Windows.Media.DrawingContext> objeto. Para usar esse método, você cria um <xref:System.Windows.Media.FormattedText> objeto. Esse objeto permite que você desenhe texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. A funcionalidade do <xref:System.Windows.Media.FormattedText> objeto contém muitas das funcionalidades dos sinalizadores DrawText na API do Win32. Além disso, o <xref:System.Windows.Media.FormattedText> objeto contém a funcionalidade, como suporte a reticências, no qual reticências são exibidas quando o texto excede seu limite. O exemplo a seguir mostra o texto que tem diversos formatos aplicados a ele, incluindo um gradiente linear na segunda e terceira palavras.  
  
 ![Texto exibido usando o objeto FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Texto exibido utilizando objeto FormattedText  
  
 Você pode converter texto formatado em <xref:System.Windows.Media.Geometry> objetos, permitindo que você crie outros tipos de texto visualmente interessante. Por exemplo, você pode criar um <xref:System.Windows.Media.Geometry> objeto com base no contorno de uma cadeia de caracteres de texto.  
  
 ![Estrutura de tópicos de texto usando um pincel de gradiente linear](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Contorno do texto usando um pincel de gradiente linear  
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais interessantes modificando o traço, o preenchimento e o realce do texto convertido.  
  
 ![Texto com diferentes cores de preenchimento e traço](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Exemplo de configuração de borda e preenchimento com diferentes cores.  
  
 ![Texto com pincel de imagem aplicado ao traço](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Exemplo de um pincel de imagem aplicado ao traço  
  
 ![Texto com pincel de imagem aplicado ao traço](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Exemplo de um pincel de imagem aplicado ao traço e ao realce  
  
 Para obter mais informações sobre o <xref:System.Windows.Media.FormattedText> de objeto, consulte [texto formatado de desenho](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Formatação de texto avançada  
 No máximo nível avançado do texto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece a capacidade de criar o layout de texto personalizado usando o <xref:System.Windows.Media.TextFormatting.TextFormatter> objeto e outros tipos do <xref:System.Windows.Media.TextFormatting> namespace. O <xref:System.Windows.Media.TextFormatting.TextFormatter> e classes associadas permitem que você implemente layout de texto personalizado que suporte sua própria definição de formatos de caractere, estilos de parágrafo, regras de quebra de linha e outras características de layout para texto internacional. Há poucos casos em que você desejaria substituir a implementação padrão do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suporte ao layout de texto. No entanto, se você estivesse criando um aplicativo ou controle de edição de texto, poderia exigir uma implementação diferente da implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão.  
  
 Ao contrário de um texto tradicional [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], o <xref:System.Windows.Media.TextFormatting.TextFormatter> interage com um cliente de layout de texto por meio de um conjunto de métodos de retorno de chamada. Requer que o cliente forneça esses métodos em uma implementação de <xref:System.Windows.Media.TextFormatting.TextSource> classe. O diagrama a seguir ilustra a interação de layout de texto entre o aplicativo cliente e <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagrama de cliente de layout de texto e TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interação entre o aplicativo e o TextFormatter  
  
 Para obter mais detalhes sobre como criar o layout de texto personalizado, consulte [formatação de texto avançada](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.FormattedText>  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>  
 [Visão geral de ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [Recursos de fonte OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Desenhando texto formatado](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [Formatação de texto avançada](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md)  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Tipografia da Microsoft](http://www.microsoft.com/typography/default.mspx)
