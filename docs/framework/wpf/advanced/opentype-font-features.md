---
title: Recursos de fonte OpenType
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 86921b610b4b42cfc0393af2966b70870bc650f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104475"
---
# <a name="opentype-font-features"></a>Recursos de fonte OpenType

Este tópico fornece uma visão geral de alguns dos principais recursos da tecnologia de fonte [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Formato de fonte OpenType  
 O formato de fonte [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] é uma extensão do formato de fonte [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)], adicionando suporte para dados de fonte PostScript. O formato de fonte [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] foi desenvolvido em conjunto pela [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] e pela Adobe Corporation. As fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] e os serviços do sistema operacional que dão suporte a fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] oferecem aos usuários uma maneira simples de usar e instalar fontes, independentemente de elas conterem estruturas de tópico do [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] ou estruturas de tópico do CFF (PostScript).  
  
 O formato de fonte [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] lida com os seguintes desafios do desenvolvedor:  
  
-   Suporte mais amplo a várias plataformas.  
  
-   Melhor suporte para conjuntos de caracteres internacionais.  
  
-   Melhor proteção para dados de fonte.  
  
-   Arquivos menores para tornar a distribuição de fonte mais eficiente.  
  
-   Suporte mais amplo para controle tipográfico avançado.  
  
> [!NOTE]
>  O SDK do Windows contém um conjunto de fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] de amostra que é possível usar com aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Essas fontes oferecem a maioria dos recursos ilustrados no restante deste tópico. Para obter mais informações, consulte [Pacote de fontes OpenType de amostra](sample-opentype-font-pack.md).  
  
 Consulte a [Especificação OpenType](https://go.microsoft.com/fwlink/?LinkId=96731) para ver detalhes sobre o formato de fonte [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)].  
  
### <a name="advanced-typographic-extensions"></a>Extensões tipográficas avançadas  
 As tabelas tipográficas avançadas (Tabelas de layout do [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]) ampliam a funcionalidade de fontes com estruturas de tópicos do [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] ou do CFF. As fontes de layout [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] contêm informações adicionais que ampliam a capacidade das fontes de dar suporte à tipografia internacional de alta qualidade. A maioria das fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] expõe somente um subconjunto dos recursos totais do [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] disponíveis. As fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fornecem os recursos a seguir.  
  
-   O mapeamento avançado entre caracteres e glifos dá suporte a ligaduras, formas posicionais, alternativos e outras substituições de fonte.  
  
-   Suporte para posicionamento bidimensional e anexação de glifos.  
  
-   Informações explícitas de script e de linguagem contidas na fonte para que um aplicativo de processamento de texto possa ajustar seu comportamento de acordo.  
  
 As tabelas de layout do [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] são descritas mais detalhadamente na seção [“Tabelas de arquivos de fonte”](https://www.microsoft.com/typography/otspec/otff.htm) da especificação do [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)].  
  
 O restante desta visão geral apresenta a amplitude e a flexibilidade de alguns do visualmente interessantes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] recursos que são expostos pelas propriedades do <xref:System.Windows.Documents.Typography> objeto. Para obter mais informações sobre esse objeto, consulte [Classe de tipografia](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Variantes  
 As variantes são usadas para renderizar diferentes estilos tipográficos, como sobrescritos e subscritos.  
  
### <a name="superscripts-and-subscripts"></a>Sobrescritos e Subscritos  
 O <xref:System.Windows.Documents.Typography.Variants%2A> propriedade permite que você defina valores de sobrescrito e subscritos para um [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonte.  
  
 O texto a seguir exibe sobrescritos para a fonte Palatino Linotype.  
  
 ![Texto usando sobrescritos OpenType](./media/opentype-font-features/opentype-superscripts.gif "texto usando sobrescritos OpenType")  
  
 O exemplo de marcação a seguir mostra como definir sobrescritos para a fonte Palatino Linotype, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 O texto a seguir exibe subscritos para a fonte Palatino Linotype.  
  
 ![Texto usando subscritos OpenType](./media/opentype-font-features/opentype-subscripts.gif "texto usando subscritos OpenType")  
  
 O exemplo de marcação a seguir mostra como definir subscritos para a fonte Palatino Linotype, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Usos decorativos de sobrescritos e subscritos  
 Sobrescritos e subscritos também podem ser utilizados para criar efeitos decorativos em textos que contêm maiúsculas e minúsculas. O texto a seguir exibe texto sobrescrito e subscrito para a fonte Palatino Linotype. Observe que as letras maiúsculas não são afetadas.  
  
 ![Texto usando sobrescritos OpenType e subscritos](./media/opentype-font-features/opentype-superscripts-subscripts.gif "texto usando sobrescritos OpenType e subscritos")  

 O exemplo de marcação a seguir mostra como definir sobrescritos e subscritos para uma fonte, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Letras maiúsculas  
 As letras maiúsculas são um conjunto de formas tipográficas que renderizam texto em glifos no estilo maiúsculo. Normalmente, quando o texto inteiro é renderizado em letras maiúsculas, o espaçamento entre elas pode parecer muito apertado, e o peso e a proporção das letras, muito pesados. O [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dá suporte a alguns formatos de estilo para letras maiúsculas, incluindo maiúsculas pequenas, minimaiúsculas, títulos e espaçamento de maiúsculas. Esses formatos de estilo permitem controlar a aparência das letras maiúsculas.  
  
 O texto a seguir exibe letras maiúsculas padrão para a fonte Pescadero, seguidas pelas letras nos estilos “SmallCaps” e “AllSmallCaps”. Nesse caso, o mesmo tamanho da fonte é usado para todas as três palavras.  
  
 ![Texto usando letras maiusculas OpenType](./media/opentype-font-features/opentype-capitals.gif "texto usando letras maiusculas OpenType")  
  
 O exemplo de marcação a seguir mostra como definir maiusculas para a fonte Pescadero, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto. Quando o formato “SmallCaps” é utilizado, todas as letras maiúsculas à esquerda são ignoradas.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Letras maiúsculas inclinadas  
 As letras maiúsculas inclinadas são mais leves, em peso e proporção, e foram concebidas para dar uma aparência mais elegante do que as letras maiúsculas normais. Normalmente, elas são usadas em tamanhos de fonte maiores, como títulos. O texto a seguir exibe maiúsculas normais e inclinadas para a fonte Pescadero. Observe as larguras mais estreitas das hastes na segunda linha do texto.  
  
 ![Texto usando letras maiusculas OpenType inclinadas](./media/opentype-font-features/opentype-titling-capitals.gif "texto usando letras maiusculas OpenType inclinadas")  
  
 O exemplo de marcação a seguir mostra como definir maiusculas inclinadas para a fonte Pescadero, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Espaçamento de letras maiúsculas  
 O espaçamento de letras maiúsculas é um recurso que permite oferecer um espaçamento maior ao usar somente letras maiúsculas no texto. Letras maiusculas são normalmente criadas para combinar com letras minúsculas. Espaçamento que parece atraente entre e uma letra maiuscula e minúscula podem parecer muito apertados quando todas as letras maiusculas são usadas. O texto a seguir exibe espaçamento normal e de maiusculas para a fonte Pescadero.  
  
 ![Texto usando espaçamento de letras maiusculas OpenType](./media/opentype-font-features/opentype-capital-spacing.gif "texto usando espaçamento de letras maiusculas OpenType ")  
 
 O exemplo de marcação a seguir mostra como definir o espaçamento de letras maiusculas para a fonte Pescadero, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligaduras  
 Ligaduras são dois ou mais glifos que formam um único glifo com o objetivo de criar um texto mais legível ou atraente. As fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] oferecem suporte a quatro tipos de ligaduras:  
  
-   **Ligaduras padrão**. Concebidas para aumentar a legibilidade. As ligaduras padrão incluem “fi”, “fl” e “ff”.  
  
-   **Ligaduras contextuais**. Concebida para aumentar a legibilidade, pois oferece um melhor comportamento de ligação entre os caracteres que compõem a ligadura.  
  
-   **Ligaduras discricionárias**. Concebidas para serem ornamentais, não especificamente para facilitar a leitura.  
  
-   **Ligaduras históricas**. Concebidas para serem históricas, não especificamente para facilitar a leitura.  
  
 O texto a seguir exibe glifos com ligadura padrão para a fonte Pericles.  
  
 ![Texto usando ligaduras padrão OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "texto usando ligaduras padrão OpenType")  
  
 O exemplo de marcação a seguir mostra como definir glifos de ligadura padrão para a fonte Pericles, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 O texto a seguir exibe glifos com ligadura discricionária para a fonte Pericles.  
  
 ![Texto usando ligaduras discricionárias OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "texto usando ligaduras discricionárias OpenType")  
  
 O exemplo de marcação a seguir mostra como definir glifos de ligadura discricionária para a fonte Pericles, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Por padrão, as fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] habilitam ligaduras padrão. Por exemplo, se a fonte Palatino Linotype for usada, as ligaduras padrão “fi”, “ff” e “fl” aparecerão como um glifo de caracteres combinados. Observe que o par de caracteres para cada ligadura padrão toca um no outro.  
  
 ![Texto usando ligaduras padrão OpenType com a fonte Palatino](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "texto usando ligaduras padrão OpenType com a fonte Palatino")    
   
 No entanto, é possível desabilitar os recursos de ligadura padrão para que uma ligadura padrão como “ff” seja exibida como dois glifos separados, em vez de como um glifo de caracteres combinados.  
  
 ![Texto usando ligaduras padrão OpenType desabilitadas](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "texto usando ligaduras padrão OpenType desabilitadas")  
    
 O exemplo de marcação a seguir mostra como desabilitar glifos de ligadura padrão para a fonte Palatino Linotype, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Swashes  
 Swashes são glifos decorativos que utilizam ornamentação elaborada, geralmente associada à caligrafia. O texto a seguir exibe glifos padrão e swash para a fonte Pescadero.  
  
 ![Texto usando glifos padrão e swash OpenType](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "texto usando glifos padrão e swash OpenType")  

 Muitas vezes, os swashes são utilizados como elementos decorativos em frases curtas, como anúncios de eventos. O texto a seguir usa swashes para enfatizar as letras maiusculas do nome do evento.  
  
 ![Texto usando swashes OpenType](./media/opentype-font-features/opentype-swashes.gif "texto usando swashes OpenType")  
  
 O exemplo de marcação a seguir mostra como definir swashes para uma fonte, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Swashes contextuais  
 Algumas combinações de glifos swash podem causar uma aparência pouco atraente, como descendentes sobrepostos em letras adjacentes. Usar um swash contextual permite que você use um glifo swash substituto que produz uma melhor aparência. O texto a seguir mostra a mesma palavra antes e depois um swash contextual é aplicado.  
  
 ![Texto usando swashes contextuais OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "texto usando swashes contextuais OpenType")  
  
 O exemplo de marcação a seguir mostra como definir um swash contextual para a fonte Pescadero, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Alternativos  
 Os alternativos são glifos que podem ser substituídos por um glifo padrão. As fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)], como a fonte Pericles usada nos exemplos a seguir, pode conter glifos alternativos que você pode usar para criar aparências diferentes para o texto. O texto a seguir exibe glifos padrão para a fonte Pericles.  
  
 ![Texto usando glifos padrão OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "texto usando glifos padrão OpenType")  

 A fonte Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] contém glifos adicionais que fornecem alternativos estilísticos para o conjunto padrão de glifos. O texto a seguir exibe glifos alternativos estilísticos.  
  
 ![Texto usando glifos alternativos estilísticos OpenType](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "texto usando glifos alternativos estilísticos OpenType")  
  
 O exemplo de marcação a seguir mostra como definir glifos alternativos estilísticos para a fonte Pericles, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 O texto a seguir exibe vários outros glifos alternativos estilísticos para a fonte Pericles.  
  
 ![Texto usando glifos alternativos estilísticos OpenType para a fonte Pericles](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "texto usando glifos alternativos estilísticos OpenType para a fonte Pericles")

 O exemplo de marcação a seguir mostra como definir esses outros glifos alternativos estilísticos.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Alternativos contextuais aleatórios  
 Os alternativos contextuais aleatórios fornecem vários glifos substitutos para um único caractere. Quando implementada com fontes do tipo de script, esse recurso pode simular manuscrito por meio de um conjunto de glifos escolhidos aleatoriamente com pequenas diferenças na aparência. O texto a seguir usa alternativos contextuais aleatórios para a fonte Lindsey. Observe que a letra "a" varia ligeiramente de aparência  
  
 ![Texto usando alternativos contextuais aleatórios OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "texto usando alternativos contextuais aleatórios OpenType")  
  
 O exemplo de marcação a seguir mostra como definir alternativos contextuais aleatórios para a fonte Lindsey, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Formas históricas  
 As formas históricas são convenções tipográficas que foram comuns no passado. O texto a seguir exibe a frase “Boston, Massachusetts” usando uma forma histórica de glifos para a fonte Palatino Linotype.  
  
 ![Texto usando formas históricas OpenType](./media/opentype-font-features/opentype-historical-forms.gif "texto usando formas históricas OpenType")  
   
 O exemplo de marcação a seguir mostra como definir formas históricas para a fonte Palatino Linotype, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Estilos numéricos  
 As fontes OpenType dão suporte a um grande número de recursos que podem ser usados com valores numéricos em texto.  
  
### <a name="fractions"></a>Frações  
 As fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dão suporte a estilos para frações, incluindo cortadas e empilhadas.  
  
 O texto a seguir exibe estilos de fração para a fonte Palatino Linotype.  
  
 ![Texto usando OpenType frações cortadas e empilhadas](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "texto usando OpenType frações cortadas e empilhadas")  
   
 O exemplo de marcação a seguir mostra como definir estilos de fração para a fonte Palatino Linotype, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Numerais em estilo antigo  
 As fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dão suporte a um formato de numerais em estilo antigo. Esse formato é útil para exibir numerais em estilos que não são mais padrão. O texto a seguir exibe uma data do século 18 em formatos de numerais padrão e em estilo antigo para a fonte Palatino Linotype.  
  
 ![Texto usando numerais em estilo antigos OpenType](./media/opentype-font-features/opentype-old-style-numerals.gif "texto usando numerais em estilo antigos OpenType")  
    
 O texto a seguir exibe numerais padrão para a fonte Palatino Linotype, seguidos por numerais em estilo antigo.  
  
 ![Texto usando conjuntos estilo antigo OpenType numerais](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "texto usando o antigos conjuntos de numerais em estilo OpenType")  
  
 O exemplo de marcação a seguir mostra como definir numerais em estilo antigo para a fonte Palatino Linotype, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Figuras proporcionais e tabulares  
 As fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dão suporte a um recurso de figura proporcional e tabular para controlar o alinhamento de larguras ao usar numerais. As figuras proporcionais tratam cada numeral como tendo uma largura diferente — “1” é mais estreito do que “5”. As figuras tabulares são tratadas como numerais de larguras iguais para se alinharem verticalmente, o que aumenta a legibilidade de informações do tipo financeiro.  
  
 O texto a seguir exibe duas figuras proporcionais na primeira coluna, usando a fonte Miramonte. Observe a diferença de largura entre os numerais "5" e "1". A segunda coluna mostra os mesmos dois valores numéricos com suas larguras ajustadas usando o recurso de figura tabular.  
  
 ![Texto usando as figuras proporcionais e tabulares OpenType](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "texto usando as figuras proporcionais e tabulares OpenType")  
    
 O exemplo de marcação a seguir mostra como definir figuras proporcionais e tabulares para a fonte Miramonte, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Zero cortado  
 As fontes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dão suporte a um formato numérico de zero cortado para enfatizar a diferença entre a letra “O” e o número “0”. Muitas vezes, o número zero cortado é utilizado para identificadores em informações financeiras e comerciais.  
  
 O texto a seguir exibe um identificador do pedido de exemplo usando a fonte Miramonte. A primeira linha usa numerais padrão. A segunda linha usada número zero cortado para fornecer um melhor contraste com a letra "O" maiuscula.  
  
 ![Texto usando OpenType zero cortado](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "texto usando OpenType zero cortado")  
    
 O exemplo de marcação a seguir mostra como definir número zero cortado para a fonte Miramonte, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Classe de tipografia  
 O <xref:System.Windows.Documents.Typography> objeto expõe o conjunto de recursos que um [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dá suporte a fonte. Definindo as propriedades de <xref:System.Windows.Documents.Typography> na marcação, você pode facilmente criar documentos que tiram proveito da [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] recursos.  
  
 O texto a seguir exibe letras maiúsculas padrão para a fonte Pescadero, seguidas pelas letras nos estilos “SmallCaps” e “AllSmallCaps”. Nesse caso, o mesmo tamanho da fonte é usado para todas as três palavras.  
  
 ![Texto usando letras maiusculas OpenType](./media/opentype-font-features/opentype-capitals.gif "texto usando letras maiusculas OpenType")  
    
 O exemplo de marcação a seguir mostra como definir maiusculas para a fonte Pescadero, usando as propriedades do <xref:System.Windows.Documents.Typography> objeto. Quando o formato “SmallCaps” é utilizado, todas as letras maiúsculas à esquerda são ignoradas.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 O exemplo de código a seguir realiza a mesma tarefa que o exemplo de marcação anterior.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Propriedades da classe de tipografia  
 A tabela a seguir lista as propriedades, valores e configurações padrão da <xref:System.Windows.Documents.Typography> objeto.  
  
|Propriedade|Valor(es)|Valor padrão|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Valor numérico – byte|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Valor numérico – byte|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|valor numérico – byte|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|valor numérico – byte|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Documents.Typography>
- [Especificação OpenType](https://go.microsoft.com/fwlink/?LinkId=96731)
- [Tipografia no WPF](typography-in-wpf.md)
- [Pacote de fontes OpenType de exemplo](sample-opentype-font-pack.md)
- [Empacotando fontes com aplicativos](packaging-fonts-with-applications.md)