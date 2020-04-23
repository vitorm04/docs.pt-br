---
title: Processamento de espaço em branco em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 05f28c9115326424164b92e1b704c52bba31cf35
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071601"
---
# <a name="white-space-processing-in-xaml"></a>Processamento de espaço em branco em XAML

As regras de idioma para XAML afirmam que [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] um espaço branco significativo deve ser processado por uma implementação do processador. Este artigo documenta essas regras de linguagem XAML. Ele também documenta o manuseio adicional de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] espaço em branco que é definido pela implementação do processador XAML e do escritor XAML para serialização.

## <a name="white-space-definition"></a>Definição de espaço branco

Consistente com XML, os [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] caracteres de espaço branco são espaço, alimentação de linha e guia. Estes correspondem aos valores Unicode 0020, 000A e 0009, respectivamente.

## <a name="white-space-normalization"></a>Normalização do espaço branco

Por padrão, a seguinte normalização [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] do espaço [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] em branco ocorre quando um processador processa um arquivo:

1. Os caracteres de avanço de linha entre caracteres do leste asiático são removidos. Consulte a seção "Caracteres da Ásia Oriental" mais tarde neste tópico para uma definição deste termo.

2. Todos os caracteres de espaço branco (espaço, alimentação de linha, guia) são convertidos em espaços.

3. Todos os espaços consecutivos são excluídos e substituídos por um espaço.

4. Um espaço imediatamente posterior à marca inicial é excluído.

5. Um espaço imediatamente anterior à marca inicial é excluído.

"Padrão" corresponde ao estado denotado pelo valor padrão do atributo [xml:space](xml-space-handling.md).

## <a name="white-space-in-inner-text-and-string-primitives"></a>Espaço branco em texto interno, e primitivos de corda

As regras de normalização anteriores aplicam-se ao texto interno encontrado dentro dos elementos XAML. Após a normalização, um processador XAML converte qualquer texto interno em um tipo apropriado da seguinte forma:

- Se o tipo da propriedade não for uma <xref:System.Object> coleção, mas não for diretamente um tipo, o processador XAML tentará converter para esse tipo usando seu conversor de tipo. Uma conversão falha aqui causa um erro de tempo de compilação.

- Se o tipo de propriedade for uma coleção e o texto interno for contíguo (sem <xref:System.String>tags de elemento interveniente), o texto interno é analisado como um único . Se o tipo <xref:System.String>de coleta não puder aceitar, isso também causa um erro de tempo de compilação.

- Se o tipo de <xref:System.Object>propriedade for, o texto interno <xref:System.String>é analisado como um único . Se houver tags de elemento interveniente, isso causa <xref:System.Object> um erro de<xref:System.String> tempo de compilação porque o tipo implica um único objeto (ou de outra forma).

- Se o tipo da propriedade for uma coleção, e o texto interno não for contíguo, a primeira substring é convertida em um <xref:System.String> e adicionada como item de coleta, o elemento <xref:System.String> interveniente é adicionado como item de coleta e, finalmente, a substring de arrasto (se houver) é adicionada à coleção como um terceiro item.

## <a name="preserving-white-space"></a>Preservando o espaço branco

Existem várias técnicas para preservar [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] o espaço em branco [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] na fonte para uma eventual apresentação que não são afetadas pela normalização do espaço branco do processador.

**xml:space="preserve"**: Especifique este atributo no nível do elemento onde a preservação do espaço branco é desejada. Isso preserva todo o espaço em branco, o que inclui os espaços que podem ser adicionados por aplicativos de edição de código para "impressão bonita" alinhar elementos como um aninhamento visualmente intuitivo. No entanto, se esses espaços renderizam é determinado pelo modelo de conteúdo para o elemento contendo. Evite especificar `xml:space="preserve"` no nível raiz porque a maioria dos modelos de objetonão considera o espaço branco como significativo, independentemente de como você define o atributo. A `xml:space` definição global pode ter consequências de desempenho no processamento XAML (particularmente serialização) em algumas implementações. É uma prática melhor definir apenas o atributo especificamente no nível de elementos que tornam o espaço branco dentro das cordas, ou são coleções significativas de espaço branco.

**Entidades e espaços não-quebra**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] suporta a colocação de qualquer entidade Unicode dentro de um modelo de objeto de texto. Você pode usar entidades dedicadas como \#espaço ininterrupto (&160; na codificação UTF-8). Você também pode usar controles de texto avançados com suporte a caracteres de espaço sem quebras. Você deve ser cauteloso se estiver usando entidades para simular características de layout, como a denagem, porque a saída de tempo de execução das entidades variará com base em um número maior de fatores do que as capacidades para produzir resultados de indenação em um sistema de layout típico, como o uso adequado de painéis e margens. Por exemplo, as entidades são mapeadas para fontes e podem alterar o tamanho em resposta à seleção de fontes do usuário.

## <a name="east-asian-characters"></a>Personagens do Leste Asiático

"Caracteres da Ásia Oriental" é definido como um conjunto de caracteres Unicode faixas U+20000 a U+2FFFD e U+30000 a U+3FFFD. Este subconjunto também é às vezes referido como "ideógrafos CJK". Para obter mais informações, consulte <https://www.unicode.org>.

## <a name="white-space-and-text-content-models"></a>Modelos de conteúdo de espaço e texto em branco

Na prática, preservar o espaço em branco é apenas uma preocupação para um subconjunto de todos os modelos de conteúdo possíveis. Esse subconjunto é composto de modelos <xref:System.String> de conteúdo que podem <xref:System.String> tomar um tipo <xref:System.String> singleton de <xref:System.Collections.IList> alguma <xref:System.Collections.Generic.ICollection%601> forma, uma coleção dedicada, ou uma mistura de e outros tipos em uma coleção ou coleção.

### <a name="white-space-and-text-content-models-in-wpf"></a>Modelos de conteúdo de espaço e texto em branco no WPF

Para fins de ilustração, o restante desta seção faz referência a tipos específicos definidos pelo WPF. Os recursos de manuseio de espaço branco descritos neste artigo são pertinentes tanto aos Serviços .NET XAML quanto ao WPF. Para ver esse comportamento em ação, você pode experimentar alguma marcação WPF XAML, visualizar os resultados em um gráfico de objetoe, em seguida, serializar de volta para marcação novamente.

Mesmo para modelos de conteúdo que podem levar cordas, o comportamento padrão dentro desses modelos de conteúdo é que qualquer espaço branco que permanece não é tratado como significativo. Por exemplo, <xref:System.Windows.Controls.ListBox> <xref:System.Collections.IList>leva um , mas o espaço branco <xref:System.Windows.Controls.ListBoxItem>(como feeds de linha entre cada um ) não é preservado e não renderizado. Se você tentar usar feeds de linha como <xref:System.Windows.Controls.ListBoxItem> separadores entre strings para itens, ele não funciona em tudo; as strings que são separadas pelos feeds de linha são tratadas como uma corda e um item.

Essas coleções que tratam o espaço branco como significativo são tipicamente parte do modelo de documento de fluxo. A principal coleção que apoia o <xref:System.Windows.Documents.InlineCollection>comportamento de preservação do espaço branco é . Esta classe de coleta <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>é declarada com o ; quando este atributo [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é encontrado, o processador tratará o espaço em branco dentro da coleção como significativo. A combinação `xml:space="preserve"` de espaço <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> branco dentro de uma coleção denotada é que todo o espaço branco é preservado e renderizado. A combinação `xml:space="default"` de espaço <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> branco dentro de um causa a normalização inicial do espaço branco descrita anteriormente, que deixa um espaço em determinadas posições, e esses espaços são preservados e renderizados. Qual comportamento é desejável depende de você, e você deve usar `xml:space` seletivamente para ativar o comportamento que deseja.

Além disso, certos elementos inline que conotam uma quebra de linha em um modelo de documento de fluxo não devem deliberadamente introduzir um espaço extra, mesmo em uma coleção significativa de espaço branco. Por exemplo, <xref:System.Windows.Documents.LineBreak> o elemento tem \<o mesmo propósito que a tag BR/> em <xref:System.Windows.Documents.LineBreak> HTML, e para legibilidade na marcação, normalmente um é separado de qualquer texto subseqüente por um feed de linha de autoria. Esse feed de linha não deve ser normalizado para se tornar um espaço líder na linha subseqüente. Para permitir esse comportamento, a <xref:System.Windows.Documents.LineBreak> definição de <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>classe para o [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] elemento aplica o , <xref:System.Windows.Documents.LineBreak> que é então interpretado pelo processador para significar que o espaço branco ao redor é sempre aparado.

## <a name="see-also"></a>Confira também

- [Visão geral xaml (WPF)](../fundamentals/xaml.md)
- [Entidades de caracteres XML e XAML](xml-character-entities.md)
- [xml:manuseio de espaço em XAML](xml-space-handling.md)
