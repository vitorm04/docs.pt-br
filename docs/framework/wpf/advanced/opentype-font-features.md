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
ms.openlocfilehash: 52fe73bccd625c9508b398874fd6b075af2445e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186814"
---
# <a name="opentype-font-features"></a>Recursos de fonte OpenType

Este tópico fornece uma visão geral de alguns dos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]principais recursos da tecnologia de fonte OpenType em .  
  
<a name="overview"></a>
## <a name="opentype-font-format"></a>Formato de fonte OpenType  
 O formato de fonte OpenType é uma extensão do formato de fonte TrueType®, adicionando suporte aos dados da fonte PostScript. O formato de fonte OpenType foi desenvolvido em conjunto pela Microsoft e Adobe Corporation. As fontes OpenType e os serviços do sistema operacional que suportam fontes OpenType fornecem aos usuários uma maneira simples de instalar e usar fontes, quer as fontes contenham contornos TrueType ou Contornos CFF (PostScript).  
  
 O formato de fonte OpenType aborda os seguintes desafios do desenvolvedor:  
  
- Suporte mais amplo a várias plataformas.  
  
- Melhor suporte para conjuntos de caracteres internacionais.  
  
- Melhor proteção para dados de fonte.  
  
- Arquivos menores para tornar a distribuição de fonte mais eficiente.  
  
- Suporte mais amplo para controle tipográfico avançado.  
  
> [!NOTE]
> O Windows SDK contém um conjunto de fontes OpenType de exemplo que você pode usar com [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos. Essas fontes oferecem a maioria dos recursos ilustrados no restante deste tópico. Para obter mais informações, consulte [Sample OpenType Font Pack](sample-opentype-font-pack.md).  
  
Para obter detalhes sobre o formato da fonte OpenType, consulte a [especificação OpenType](https://docs.microsoft.com/typography/opentype/spec/).  
  
### <a name="advanced-typographic-extensions"></a>Extensões tipográficas avançadas  
 As tabelas tipográficas avançadas (tabelas opentype layout) estendem a funcionalidade das fontes com contornos TrueType ou CFF. As fontes openType Layout contêm informações adicionais que ampliam os recursos das fontes para suportar tipografia internacional de alta qualidade. A maioria das fontes OpenType expõe apenas um subconjunto dos recursos totais do OpenType disponíveis. As fontes OpenType fornecem os seguintes recursos.  
  
- O mapeamento avançado entre caracteres e glifos dá suporte a ligaduras, formas posicionais, alternativos e outras substituições de fonte.  
  
- Suporte para posicionamento bidimensional e anexação de glifos.  
  
- Informações explícitas de script e de linguagem contidas na fonte para que um aplicativo de processamento de texto possa ajustar seu comportamento de acordo.  
  
 As tabelas OpenType Layout são descritas com mais detalhes na seção ["Tabelas de arquivos](https://www.microsoft.com/typography/otspec/otff.htm) de fonte" da especificação OpenType.  
  
 O restante desta visão geral introduz a amplitude e flexibilidade de alguns dos recursos do OpenType <xref:System.Windows.Documents.Typography> visualmente interessantes que são expostos pelas propriedades do objeto. Para obter mais informações sobre esse objeto, consulte [Classe de tipografia](#typography_class).  
  
<a name="variants"></a>
## <a name="variants"></a>Variantes  
 As variantes são usadas para renderizar diferentes estilos tipográficos, como sobrescritos e subscritos.  
  
### <a name="superscripts-and-subscripts"></a>Sobrescritos e Subscritos  
 A <xref:System.Windows.Documents.Typography.Variants%2A> propriedade permite definir valores de seleção e subscrito para uma fonte OpenType.  
  
 O texto a seguir exibe sobrescritos para a fonte Palatino Linotype.  
  
 ![Texto usando sobrescritos OpenType](./media/opentype-font-features/opentype-superscripts.gif "Texto usando sobrescritos OpenType")  
  
 O exemplo de marcação a seguir mostra como definir sobrescritos <xref:System.Windows.Documents.Typography> para a fonte Palatino Linotype, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 O texto a seguir exibe subscritos para a fonte Palatino Linotype.  
  
 ![Texto usando subscritos OpenType](./media/opentype-font-features/opentype-subscripts.gif "Texto usando subscritos OpenType")  
  
 O exemplo de marcação a seguir mostra como definir subscritos <xref:System.Windows.Documents.Typography> para a fonte Palatino Linotype, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Usos decorativos de sobrescritos e subscritos  
 Sobrescritos e subscritos também podem ser utilizados para criar efeitos decorativos em textos que contêm maiúsculas e minúsculas. O texto a seguir exibe texto sobrescrito e subscrito para a fonte Palatino Linotype. Observe que as letras maiúsculas não são afetadas.  
  
 ![Texto usando sobrescritos e subscritos OpenType](./media/opentype-font-features/opentype-superscripts-subscripts.gif "Texto usando sobrescritos e subscritos OpenType")  

 O exemplo de marcação a seguir mostra como definir sobrescritos <xref:System.Windows.Documents.Typography> e subscritos para uma fonte, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>
## <a name="capitals"></a>Letras maiúsculas  
 As letras maiúsculas são um conjunto de formas tipográficas que renderizam texto em glifos no estilo maiúsculo. Normalmente, quando o texto inteiro é renderizado em letras maiúsculas, o espaçamento entre elas pode parecer muito apertado, e o peso e a proporção das letras, muito pesados. O OpenType suporta uma série de formatos de estilo para capitais, incluindo pequenas capitais, pequenas capitais, títulos e espaçamento de capital. Esses formatos de estilo permitem controlar a aparência das letras maiúsculas.  
  
 O texto a seguir exibe letras maiúsculas padrão para a fonte Pescadero, seguidas pelas letras nos estilos “SmallCaps” e “AllSmallCaps”. Neste caso, o mesmo tamanho de fonte é usado para as três palavras.  
  
 ![Texto usando letras maiúsculas OpenType](./media/opentype-font-features/opentype-capitals.gif "Texto usando letras maiúsculas OpenType")  
  
 O exemplo de marcação a seguir mostra como definir capitais <xref:System.Windows.Documents.Typography> para a fonte Pescadero, usando propriedades do objeto. Quando o formato “SmallCaps” é utilizado, todas as letras maiúsculas à esquerda são ignoradas.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Letras maiúsculas inclinadas  
 As letras maiúsculas inclinadas são mais leves, em peso e proporção, e foram concebidas para dar uma aparência mais elegante do que as letras maiúsculas normais. Normalmente, elas são usadas em tamanhos de fonte maiores, como títulos. O texto a seguir exibe maiúsculas normais e inclinadas para a fonte Pescadero. Observe as larguras mais estreitas das hastes na segunda linha do texto.  
  
 ![Texto usando letras maiúsculas OpenType inclinadas](./media/opentype-font-features/opentype-titling-capitals.gif "Texto usando letras maiúsculas OpenType inclinadas")  
  
 O exemplo de marcação a seguir mostra como definir capitais de titling para a fonte Pescadero, usando propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Espaçamento de letras maiúsculas  
 O espaçamento de letras maiúsculas é um recurso que permite oferecer um espaçamento maior ao usar somente letras maiúsculas no texto. Letras maiúsculas são tipicamente projetadas para se misturar com letras minúsculas. O espaçamento que parece atraente entre uma letra maiúscula e uma letra minúscula pode parecer muito apertado quando todas as letras maiúsculas são usadas. O texto a seguir exibe o espaçamento normal e de capital para a fonte Pescadero.  
  
 ![Texto usando espaçamento de letras maiúsculas OpenType](./media/opentype-font-features/opentype-capital-spacing.gif "Texto usando espaçamento de letras maiúsculas OpenType")  

 O exemplo de marcação a seguir mostra como definir o espaçamento de capital para a fonte Pescadero, usando propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>
## <a name="ligatures"></a>Ligaduras  
 Ligaduras são dois ou mais glifos que formam um único glifo com o objetivo de criar um texto mais legível ou atraente. As fontes OpenType suportam quatro tipos de ligaduras:  
  
- **Ligaduras padrão**. Concebidas para aumentar a legibilidade. As ligaduras padrão incluem “fi”, “fl” e “ff”.  
  
- **Ligaduras contextuais**. Concebida para aumentar a legibilidade, pois oferece um melhor comportamento de ligação entre os caracteres que compõem a ligadura.  
  
- **Ligaduras discricionárias**. Concebidas para serem ornamentais, não especificamente para facilitar a leitura.  
  
- **Ligaduras históricas**. Concebidas para serem históricas, não especificamente para facilitar a leitura.  
  
 O texto a seguir exibe glifos com ligadura padrão para a fonte Pericles.  
  
 ![Texto usando ligaduras padrão OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "Texto usando ligaduras padrão OpenType")  
  
 O exemplo de marcação a seguir mostra como definir glifos de ligadura <xref:System.Windows.Documents.Typography> padrão para a fonte Péricles, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 O texto a seguir exibe glifos com ligadura discricionária para a fonte Pericles.  
  
 ![Texto usando ligaduras discricionárias OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "Texto usando ligaduras discricionárias OpenType")  
  
 O exemplo de marcação a seguir mostra como definir glifos de ligadura <xref:System.Windows.Documents.Typography> discricionária para a fonte Péricles, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Por padrão, as fontes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] OpenType em habilitar ligaduras padrão. Por exemplo, se a fonte Palatino Linotype for usada, as ligaduras padrão “fi”, “ff” e “fl” aparecerão como um glifo de caracteres combinados. Observe que o par de caracteres para cada ligadura padrão toca um no outro.  
  
 ![Texto usando ligaduras padrão OpenType com Linótipo Palatino](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Texto usando ligaduras padrão OpenType com Linótipo Palatino")

 No entanto, é possível desabilitar os recursos de ligadura padrão para que uma ligadura padrão como “ff” seja exibida como dois glifos separados, em vez de como um glifo de caracteres combinados.  
  
 ![Texto usando ligaduras padrão OpenType desabilitadas](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Texto usando ligaduras padrão OpenType desabilitadas")  

 O exemplo de marcação a seguir mostra como desativar glifos de ligadura padrão <xref:System.Windows.Documents.Typography> para a fonte Palatino Linotype, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>
## <a name="swashes"></a>Swashes  
 Swashes são glifos decorativos que utilizam ornamentação elaborada, geralmente associada à caligrafia. O texto a seguir exibe glifos padrão e swash para a fonte Pescadero.  
  
 ![Texto usando glifos padrão e swash OpenType](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "Texto usando glifos padrão e swash OpenType")  

 Muitas vezes, os swashes são utilizados como elementos decorativos em frases curtas, como anúncios de eventos. O texto a seguir usa swashes para enfatizar as letras maiúsculas do nome do evento.  
  
 ![Texto usando swashes OpenType](./media/opentype-font-features/opentype-swashes.gif "Texto usando swashes OpenType")  
  
 O exemplo de marcação a seguir mostra como definir swashes para uma fonte, usando propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Swashes contextuais  
 Algumas combinações de glifos swash podem causar uma aparência pouco atraente, como descendentes sobrepostos em letras adjacentes. Usar uma lavagem contextual permite que você use um glifo de swash substituto que produz uma aparência melhor. O texto a seguir mostra a mesma palavra antes e depois de uma lavagem contextual ser aplicada.  
  
 ![Texto usando swashes contextuais OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "Texto usando swashes contextuais OpenType")  
  
 O exemplo de marcação a seguir mostra como definir uma lavagem contextual <xref:System.Windows.Documents.Typography> para a fonte Pescadero, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>
## <a name="alternates"></a>Alternativos  
 Os alternativos são glifos que podem ser substituídos por um glifo padrão. As fontes OpenType, como a fonte Péricles usada nos exemplos a seguir, podem conter glifos alternativos que você pode usar para criar diferentes aparências para texto. O texto a seguir exibe glifos padrão para a fonte Pericles.  
  
 ![Texto usando glifos padrão OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "Texto usando glifos padrão OpenType")  

 A fonte Péricles OpenType contém glifos adicionais que fornecem alternativas estilísticas ao conjunto padrão de glifos. O texto a seguir exibe glifos alternativos estilísticos.  
  
 ![Texto usando glifos alternativos estilísticos OpenType](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "Texto usando glifos alternativos estilísticos OpenType")  
  
 O exemplo de marcação a seguir mostra como definir glifos alternativos estilísticos para a fonte Péricles, usando propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 O texto a seguir exibe vários outros glifos alternativos estilísticos para a fonte Pericles.  
  
 ![Texto usando glifos alternativos estilísticos OpenType para a fonte Péricles](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Texto usando glifos alternativos estilísticos OpenType para a fonte Péricles")

 O exemplo de marcação a seguir mostra como definir esses outros glifos alternativos estilísticos.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Alternativos contextuais aleatórios  
 Os alternativos contextuais aleatórios fornecem vários glifos substitutos para um único caractere. Quando implementado com fontes do tipo script, este recurso pode simular a caligrafia usando um conjunto de glifos escolhidos aleatoriamente com pequenas diferenças na aparência. O texto a seguir usa alternativas contextuais aleatórias para a fonte Lindsey. Observe que a letra "a" varia ligeiramente na aparência  
  
 ![Texto usando alternativos contextuais aleatórios OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "Texto usando alternativos contextuais aleatórios OpenType")  
  
 O exemplo de marcação a seguir mostra como definir alternativas contextuais aleatórias para a fonte Lindsey, usando propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Formas históricas  
 As formas históricas são convenções tipográficas que foram comuns no passado. O texto a seguir exibe a frase “Boston, Massachusetts” usando uma forma histórica de glifos para a fonte Palatino Linotype.  
  
 ![Texto usando formas históricas OpenType](./media/opentype-font-features/opentype-historical-forms.gif "Texto usando formas históricas OpenType")  

 O exemplo de marcação a seguir mostra como definir formas históricas para a fonte Palatino Linotype, usando propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>
## <a name="numerical-styles"></a>Estilos numéricos  
 As fontes OpenType dão suporte a um grande número de recursos que podem ser usados com valores numéricos em texto.  
  
### <a name="fractions"></a>Frações  
 As fontes OpenType suportam estilos para frações, incluindo cortados e empilhados.  
  
 O texto a seguir exibe estilos de fração para a fonte Palatino Linotype.  
  
 ![Texto usando frações cortadas e empilhadas OpenType](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "Texto usando frações cortadas e empilhadas OpenType")  

 O exemplo de marcação a seguir mostra como definir estilos de <xref:System.Windows.Documents.Typography> fração para a fonte Palatino Linotype, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Numerais em estilo antigo  
 As fontes OpenType suportam um formato numeral de estilo antigo. Esse formato é útil para exibir numerais em estilos que não são mais padrão. O texto a seguir exibe uma data do século 18 em formatos de numerais padrão e em estilo antigo para a fonte Palatino Linotype.  
  
 ![Texto usando numerais em estilo antigo OpenType](./media/opentype-font-features/opentype-old-style-numerals.gif "Texto usando numerais em estilo antigo OpenType")  

 O texto a seguir exibe numerais padrão para a fonte Palatino Linotype, seguidos por numerais em estilo antigo.  
  
 ![Texto usando conjuntos de numerais em estilo antigo OpenType](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "Texto usando conjuntos de numerais em estilo antigo OpenType")  
  
 O exemplo de marcação a seguir mostra como definir numerais de estilo <xref:System.Windows.Documents.Typography> antigo para a fonte Palatino Linotype, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Figuras proporcionais e tabulares  
 As fontes OpenType suportam um recurso de figura proporcional e tabular para controlar o alinhamento das larguras ao usar numerais. As figuras proporcionais tratam cada numeral como tendo uma largura diferente — “1” é mais estreito do que “5”. As figuras tabulares são tratadas como numerais de larguras iguais para se alinharem verticalmente, o que aumenta a legibilidade de informações do tipo financeiro.  
  
 O texto a seguir exibe duas figuras proporcionais na primeira coluna, usando a fonte Miramonte. Observe a diferença de largura entre os numerais "5" e "1". A segunda coluna mostra os mesmos dois valores numéricos com as larguras ajustadas usando o recurso de figura tabular.  
  
 ![Texto usando figuras proporcionais e tabulares OpenType](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "Texto usando figuras proporcionais e tabulares OpenType")  

 O exemplo de marcação a seguir mostra como definir figuras proporcionais <xref:System.Windows.Documents.Typography> e tabulares para a fonte Miramonte, usando propriedades do objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Zero cortado  
 As fontes OpenType suportam um formato numeral zero cortado para enfatizar a diferença entre a letra "O" e o numeral "0". Muitas vezes, o número zero cortado é utilizado para identificadores em informações financeiras e comerciais.  
  
 O texto a seguir exibe um identificador de ordem de exemplo usando a fonte Miramonte. A primeira linha usa numerais padrão. A segunda linha usou numerais cortados zero para fornecer melhor contraste com a letra maiúscula "O".  
  
 ![Texto usando o número zero cortado OpenType](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "Texto usando o número zero cortado OpenType")  

 O exemplo de marcação a seguir mostra como definir numerais zero cortados para a fonte Miramonte, usando propriedades do <xref:System.Windows.Documents.Typography> objeto.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>
## <a name="typography-class"></a>Classe de tipografia  
 O <xref:System.Windows.Documents.Typography> objeto expõe o conjunto de recursos que uma fonte OpenType suporta. Ao definir as <xref:System.Windows.Documents.Typography> propriedades de na marcação, você pode facilmente escrever documentos que aproveitam os recursos do OpenType.  
  
 O texto a seguir exibe letras maiúsculas padrão para a fonte Pescadero, seguidas pelas letras nos estilos “SmallCaps” e “AllSmallCaps”. Neste caso, o mesmo tamanho de fonte é usado para as três palavras.  
  
 ![Texto usando letras maiúsculas OpenType](./media/opentype-font-features/opentype-capitals.gif "Texto usando letras maiúsculas OpenType")  

 O exemplo de marcação a seguir mostra como definir capitais <xref:System.Windows.Documents.Typography> para a fonte Pescadero, usando propriedades do objeto. Quando o formato “SmallCaps” é utilizado, todas as letras maiúsculas à esquerda são ignoradas.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 O exemplo de código a seguir realiza a mesma tarefa que o exemplo de marcação anterior.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Propriedades da classe de tipografia  
 A tabela a seguir lista as propriedades, <xref:System.Windows.Documents.Typography> valores e configurações padrão do objeto.  
  
|Propriedade|Valor(es)|Valor Padrão|  
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
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji>&#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full>&#124; <xref:System.Windows.FontEastAsianWidths.Half> <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
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
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior>&#124; <xref:System.Windows.FontVariants.Normal> <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> <xref:System.Windows.FontVariants.Subscript> &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Documents.Typography>
- [Especificação OpenType](https://docs.microsoft.com/typography/opentype/spec/)
- [Tipografia no WPF](typography-in-wpf.md)
- [Pacote de fontes OpenType de amostra](sample-opentype-font-pack.md)
- [Empacotando fontes com aplicativos](packaging-fonts-with-applications.md)
