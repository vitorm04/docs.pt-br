---
title: Espaço em branco em XAML de processamento
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 89f8a4675b3edc23913549bc24f0d9ae16917519
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749925"
---
# <a name="white-space-processing-in-xaml"></a>Espaço em branco em XAML de processamento
As regras da linguagem XAML de estado que o espaço em branco significativo devem ser processado por um [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] implementação do processador. Este tópico documenta essas regras da linguagem XAML. Ele também documenta o tratamento de espaço em branco que é definido pela [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementação do processador XAML e o gravador XAML para serialização.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Definição de espaço em branco  
 Consistente com [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], o caractere de espaço em branco no [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] são espaço, avanço de linha e tabulação. Esses correspondem do [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] valores 0020, 000A e 0009 respectivamente.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalização de espaço em branco  
 Por padrão a normalização de espaço em branco a seguir ocorre quando um [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processos de processador um [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivo:  
  
1.  Caracteres de avanço de linha entre caracteres do Leste Asiático são removidos. Consulte a seção "Caracteres do Leste Asiático" mais adiante neste tópico para obter uma definição do termo.  
  
2.  Todos os caracteres de espaço em branco (espaço, avanço de linha, guia) são convertidos em espaços.  
  
3.  Todos os espaços consecutivos são excluídos e substituídos por um espaço.  
  
4.  Um espaço imediatamente após a marca de início é excluído.  
  
5.  Um espaço imediatamente antes da marca de fim é excluído.  
  
 "Default" corresponde ao estado indicado pelo valor de padrão de [XML: space](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md) atributo.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Espaço em branco no texto interno e os primitivos de cadeia de caracteres  
 As regras de normalização anterior se aplicam ao texto interno que é encontrado dentro de elementos XAML. Após a normalização, um processador XAML Converte qualquer texto interno em um tipo apropriado, da seguinte maneira:  
  
-   Se o tipo da propriedade não é uma coleção, mas não é diretamente um <xref:System.Object> tipo, o processador XAML tenta converter para aquele tipo usando seu conversor de tipo. Uma falha de conversão aqui causa um erro de tempo de compilação.  
  
-   Se o tipo da propriedade é uma coleção e o texto interno for contíguo (nenhum elemento de marcas intervenientes), o texto interno é analisado como um único <xref:System.String>. Se o tipo de coleção não pode aceitar <xref:System.String>, isso também faz com que um erro de tempo de compilação.  
  
-   Se o tipo da propriedade for <xref:System.Object>, o texto interno é analisado como um único <xref:System.String>. Se existirem marcas de elemento intervenientes, isso causa um erro de tempo de compilação porque o <xref:System.Object> tipo implica um único objeto (<xref:System.String> ou de outra forma).  
  
-   Se o tipo da propriedade é uma coleção e o texto interno não é contíguo, a primeira subcadeia de caracteres é convertida em um <xref:System.String> e adicionado como um item da coleção, o elemento intermediárias é adicionado como um item da coleção, e finalmente é a subcadeia de caracteres à direita (se houver) adicionado à coleção como um terceiro <xref:System.String> item.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Preservar espaço em branco  
 Há várias técnicas para preservar espaço em branco na fonte [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] para eventual apresentação não são afetados por [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] normalização de espaço em branco do processador.  
  
 **XML: space = "preserve"**: especificar esse atributo no nível do elemento onde preservação de espaço em branco é desejada. Este preserva todo espaço, que inclui os que podem ser adicionados por aplicativos de edição de código para "impressão bonita" espaços em branco alinha elementos como um aninhamento visualmente intuitivo. No entanto, se esses espaços são renderizados é determinado pelo modelo de conteúdo do elemento recipiente. Evite especificar `xml:space="preserve"` no nível raiz de porque a maioria dos modelos de objeto não considera o branco espaço como significativo, independentemente de como você pode definir o atributo. Definindo `xml:space` globalmente pode ter consequências para o desempenho no processamento (particularmente serialização) em algumas implementações de XAML. É uma melhor prática apenas definir o atributo especificamente no nível de elementos que renderiza o espaço em branco em cadeias de caracteres, ou são coleções de espaço em branco significativas.  
  
 **Entidades e espaços não separáveis**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dá suporte à colocação de qualquer [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] entidade dentro de um modelo de objeto de texto. Você pode usar entidades dedicadas, como espaço incondicional (&\#160; na codificação UTF-8). Você também pode usar controles de rich text que dão suporte a caracteres de espaço incondicional. Você deve ter cuidado se você estiver usando entidades para simular as características de layout como o recuo, porque a saída de tempo de execução das entidades irá variar com base em um número maior de fatores que os recursos para produzir resultados de recuo em um típico sistema de layout, como o uso adequado de painéis e margens. Por exemplo, as entidades são mapeadas para as fontes e podem alterar o tamanho em resposta a seleção de fonte do usuário.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Caracteres do Leste Asiático  
 "Caracteres do Leste Asiático" são definidos como um conjunto de [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] U + 20000 a U + 2FFFD e U + 30000 até U + 3FFFD de intervalos de caracteres. Esse subconjunto às vezes também é conhecido como "Ideogramas CJK". Para obter mais informações, consulte [http://www.unicode.org](http://www.unicode.org/).  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Modelos de conteúdo de espaço em branco e texto  
 Na prática, preservar espaço em branco é apenas um problema para um subconjunto de todos os modelos de conteúdo possíveis. Esse subconjunto é composto de modelos de conteúdo que podem levar um singleton <xref:System.String> tipo de alguma forma, um dedicado <xref:System.String> coleção ou uma mistura de <xref:System.String> e outros tipos em um <xref:System.Collections.IList> ou <xref:System.Collections.Generic.ICollection%601> coleção.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Modelos de conteúdo em branco e o texto no WPF  
 Para fins de ilustração, o restante desta seção faz referência a tipos específicos que são definidos pelo WPF. Os recursos de tratamento de espaço em branco que são descritos neste tópico são geralmente pertinentes aos serviços de XAML do .NET Framework e o WPF. Para ver esse comportamento em ação, você pode fazer experiências com alguma marcação XAML WPF, exibir os resultados em um gráfico de objeto e, em seguida, serializar para marcação novamente.  
  
 Mesmo para modelos de conteúdo que pode receber cadeias de caracteres, o comportamento padrão dentro desses modelos de conteúdo é que qualquer espaço em branco que permanece não é tratado como significativo. Por exemplo, <xref:System.Windows.Controls.ListBox> usa um <xref:System.Collections.IList>, mas o espaço em branco (como avanços de linha entre cada <xref:System.Windows.Controls.ListBoxItem>) não é preservado e não é renderizado. Se você tentar usar alimentações de linha como separadores entre cadeias de caracteres para <xref:System.Windows.Controls.ListBoxItem> itens, ele não funciona em todos os; as cadeias de caracteres que são separadas pela alimentação de linha são tratadas como uma cadeia de caracteres e um item.  
  
 As coleções que trate o espaço em branco como significativa normalmente são parte do modelo de documento de fluxo. A coleção principal que dá suporte ao comportamento de preservação de espaço em branco é <xref:System.Windows.Documents.InlineCollection>. Essa classe de coleção é declarado com o <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; quando esse atributo for encontrado, o [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processador tratará o espaço em branco dentro da coleção como significativo. A combinação de `xml:space="preserve"` e espaço em branco dentro de um <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indicada na coleção é que todos os espaços em branco é preservado e renderizados. A combinação de `xml:space="default"` e espaço em branco dentro de um <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> causa a normalização de espaço em branco inicial descrita anteriormente, que deixa um espaço em determinadas posições e esses espaços é preservada e renderizada. Qual o comportamento é desejável cabe a você, e você deve usar `xml:space` seletivamente para habilitar o comportamento desejado.  
  
 Além disso, determinados elementos embutidos que denota um linebreak em um modelo de documento de fluxo devem deliberadamente não apresentar um espaço extra mesmo em uma coleção significativa de espaço em branco. Por exemplo, o <xref:System.Windows.Documents.LineBreak> elemento tem a mesma finalidade, como o \<BR / > Marcar no [!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)]e para facilitar a leitura na marcação, normalmente um <xref:System.Windows.Documents.LineBreak> é separado de qualquer texto subsequente por uma alimentação de linha. Essa alimentação de linha não deve ser normalizada para se tornar um espaço à esquerda na linha subsequente. Para habilitar esse comportamento, a definição de classe para o <xref:System.Windows.Documents.LineBreak> elemento aplica-se a <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, que é interpretado pela [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processador para significar que o espaço em branco ao redor <xref:System.Windows.Documents.LineBreak> sempre é cortado.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Entidades de caractere XML e XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)  
 [XML: space manipulação em XAML](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md)
