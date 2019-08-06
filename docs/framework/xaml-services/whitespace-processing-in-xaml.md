---
title: Processamento de espaço em branco em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 077f19690d204d3b8f682d01c51feee9e9edbfd4
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796818"
---
# <a name="white-space-processing-in-xaml"></a>Processamento de espaço em branco em XAML
As regras de idioma para o estado XAML que o espaço em branco significativo deve [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ser processado por uma implementação de processador. Este tópico documenta essas regras de linguagem XAML. Ele também documenta o tratamento de espaço em branco adicional que é [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] definido pela implementação do processador XAML e do gravador XAML para serialização.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Definição de espaço em branco  
 Consistente com [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], os caracteres de espaço em [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] branco no são espaço, avanço de alimentação e tabulação. Elas correspondem aos [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] valores 0020, 000A e 0009, respectivamente.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalização de espaço em branco  
 Por padrão, a normalização de espaço em branco a seguir [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ocorre quando um [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processador processa um arquivo:  
  
1. Os caracteres de avanço de alimentação entre os caracteres do Leste Asiático são removidos. Consulte a seção "caracteres do leste asiático" posteriormente neste tópico para obter uma definição desse termo.  
  
2. Todos os caracteres de espaço em branco (espaço, avanço de alimentação, tabulação) são convertidos em espaços.  
  
3. Todos os espaços consecutivos são excluídos e substituídos por um espaço.  
  
4. Um espaço imediatamente após a marca de início é excluído.  
  
5. Um espaço imediatamente antes de a marca de fim ser excluída.  
  
 "Default" corresponde ao estado indicado pelo valor padrão do atributo [XML: Space](xml-space-handling-in-xaml.md) .  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Espaço em branco no texto interno e primitivos de cadeia de caracteres  
 As regras anteriores de normalização se aplicam ao texto interno que é encontrado nos elementos XAML. Após a normalização, um processador XAML converte qualquer texto interno em um tipo apropriado da seguinte maneira:  
  
- Se o tipo da propriedade não for uma coleção, mas não for um <xref:System.Object> tipo diretamente, o processador XAML tentará converter para esse tipo usando seu conversor de tipo. Uma conversão com falha aqui causa um erro de tempo de compilação.  
  
- Se o tipo da propriedade for uma coleção e o texto interno for contíguo (sem marcas de elemento intervenientes), o texto interno será analisado como um único <xref:System.String>. Se o tipo de coleção não <xref:System.String>puder aceitar, isso também causará um erro em tempo de compilação.  
  
- Se o tipo da propriedade for <xref:System.Object>, o texto interno será analisado como um único. <xref:System.String> Se houver marcas de elemento intervenientes, isso causará um erro em tempo de <xref:System.Object> compilação porque o tipo implica um<xref:System.String> único objeto (ou outro).  
  
- Se o tipo da propriedade for uma coleção e o texto interno não for contíguo, a primeira subcadeia de caracteres será convertida em <xref:System.String> um e adicionada como um item de coleta, o elemento intermediário será adicionado como um item de coleta e, por fim, a subcadeia de caracteres à direita (se houver) for adicionado à coleção como um terceiro <xref:System.String> item.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Preservando o espaço em branco  
 Há várias técnicas para preservar o espaço em branco na fonte [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] para apresentação eventual que não são afetadas pela [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] normalização de espaço em branco do processador.  
  
 **xml:space="preserve"** : Especifique esse atributo no nível do elemento onde a preservação de espaço em branco é desejada. Isso preserva todo o espaço em branco, que inclui os espaços que podem ser adicionados pelos aplicativos de edição de código aos elementos "muito impressos" alinhados como um aninhamento visualmente intuitivo. No entanto, se esses espaços renderizados são determinados pelo modelo de conteúdo para o elemento contentor. Evite especificar `xml:space="preserve"` no nível raiz porque a maioria dos modelos de objeto não considera o espaço em branco tão significativo, independentemente de como você definiu o atributo. A `xml:space` configuração globalmente pode ter consequências de desempenho no processamento XAML (particularmente serialização) em algumas implementações. É uma prática melhor definir apenas o atributo especificamente no nível de elementos que processam o espaço em branco em cadeias de caracteres ou que são coleções significativas de espaço em branco.  
  
 **Entidades e espaços não separáveis**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] oferece suporte à [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] colocação de qualquer entidade dentro de um modelo de objeto de texto. Você pode usar entidades dedicadas como espaço não separável (&\#160; em codificação UTF-8). Você também pode usar controles de Rich Text que dão suporte a caracteres de espaço não separável. Você deve ter cuidado se estiver usando entidades para simular características de layout, como recuo, porque a saída de tempo de execução das entidades varia com base em um número maior de fatores do que os recursos para produzir resultados de recuo em um típico sistema de layout, como o uso adequado de painéis e margens. Por exemplo, as entidades são mapeadas para fontes e podem alterar o tamanho em resposta à seleção de fontes do usuário.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Caracteres do leste asiático  
 "Caracteres do leste asiático" é definido como um conjunto [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] de intervalos de caracteres u + 20000 a u + 2FFFD e u + 30000 a u + 3FFFD. Esse subconjunto às vezes também é chamado de "ideogramas CJK". Para obter mais informações, consulte <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Modelos de conteúdo de texto e espaço em branco  
 Na prática, preservar o espaço em branco é apenas uma preocupação para um subconjunto de todos os modelos de conteúdo possíveis. Esse subconjunto é composto por modelos de conteúdo que podem usar <xref:System.String> um tipo singleton de alguma forma, <xref:System.String> uma coleção dedicada ou uma mistura <xref:System.String> de e outros tipos em <xref:System.Collections.IList> uma <xref:System.Collections.Generic.ICollection%601> coleção ou.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Modelos de conteúdo de texto e espaço em branco no WPF  
 Para fins de ilustração, o restante desta seção faz referência a tipos específicos que são definidos pelo WPF. Os recursos de tratamento de espaço em branco que são descritos neste tópico geralmente são pertinentes aos serviços .NET Framework XAML e ao WPF. Para ver esse comportamento em ação, você pode experimentar alguma marcação XAML do WPF, exibir os resultados em um grafo de objeto e, em seguida, serializar novamente para marcação.  
  
 Mesmo para modelos de conteúdo que podem receber cadeias de caracteres, o comportamento padrão dentro desses modelos de conteúdo é que qualquer espaço em branco que permanece não é tratado como significativo. Por exemplo, <xref:System.Windows.Controls.ListBox> o recebe <xref:System.Collections.IList>um, mas o espaço em branco (como perpapers <xref:System.Windows.Controls.ListBoxItem>entre cada um) não é preservado e não renderizado. Se você tentar usar alimentação de linha como separadores entre cadeias de caracteres para <xref:System.Windows.Controls.ListBoxItem> itens, isso não funcionará; as cadeias de caracteres separadas pelas alimentações são tratadas como uma cadeia de caracteres e um item.  
  
 Essas coleções que tratam de espaço em branco como significativas normalmente são parte do modelo de documento de fluxo. A coleção primária que dá suporte ao comportamento de preservação de <xref:System.Windows.Documents.InlineCollection>espaço em branco é. Essa classe de coleção é declarada com a <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; quando esse atributo for encontrado, o processador tratará o [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] espaço em branco dentro da coleção como significativo. A combinação `xml:space="preserve"` e o espaço em branco dentro <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> de uma coleção denotada é que todo o espaço em branco é preservado e renderizado. A combinação `xml:space="default"` e o espaço em branco dentro <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> de uma causa a normalização inicial de espaço em branco descrito anteriormente, que deixa um espaço em determinadas posições e esses espaços são preservados e renderizados. O comportamento é desejável, e você deve usar `xml:space` seletivamente para habilitar o comportamento desejado.  
  
 Além disso, determinados elementos embutidos que connotam um LineBreak em um modelo de documento de fluxo devem deliberadamente não introduzir um espaço extra, mesmo em uma coleção significativa de espaço em branco. Por exemplo, o <xref:System.Windows.Documents.LineBreak> elemento tem a mesma finalidade que a \<marca br/> em HTML e para facilitar a leitura na marcação, normalmente um <xref:System.Windows.Documents.LineBreak> é separado de qualquer texto subsequente por uma alimentação de uma autoria. Esse avanço não deve ser normalizado para se tornar um espaço à esquerda na linha subsequente. Para habilitar esse comportamento, a definição de classe para <xref:System.Windows.Documents.LineBreak> o elemento aplica <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>o, que é então interpretado pelo processador para significar que o <xref:System.Windows.Documents.LineBreak> [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] espaço em branco ao redor é sempre cortado.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Entidades de caractere XML e XAML](xml-character-entities-and-xaml.md)
- [XML: tratamento de espaço em XAML](xml-space-handling-in-xaml.md)
