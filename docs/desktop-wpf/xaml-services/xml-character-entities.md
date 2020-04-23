---
title: Entidades e XAML de caractere XML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: aff96c5d0ee6bbf2bbe2f9e3b3ae091caa781f7a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071454"
---
# <a name="xml-character-entities-and-xaml"></a>Entidades e XAML de caractere XML

XAML usa entidades de caracteres definidas em XML para caracteres especiais. Este tópico descreve algumas entidades de caracteres específicas e considerações gerais para outros conceitos XML em XAML.

## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Entidades de personagens e questões de fuga que são exclusivas do XAML

A marcação XAML normalmente usa as mesmas entidades de caracteres e seqüências de fuga definidas em XML.

A principal exceção é que os aparelhos ({ e }) têm significado no XAML porque esses caracteres informam um processador XAML que uma seqüência de caracteres fechada por chaves deve ser interpretada como uma extensão de marcação. Para obter mais informações sobre extensões de marcação, consulte [Extensões de marcação para visão geral XAML](markup-extensions-overview.md).

No entanto, você ainda pode exibir as chaves como caracteres literais usando uma seqüência de escape que é particular para XAML em vez de XML. Para obter mais informações, consulte [ {} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).

Observe que uma\\barra invertida ( ) não requer uma seqüência de fuga quando é manuseada como uma corda.

## <a name="xml-character-entities"></a>Entidades de Personagens XML

Como mencionado anteriormente, a maioria das entidades de caracteres e seqüências de fuga que são normalmente usadas para escrever marcação XAML são definidas por XML. Este tópico não fornece a lista completa dessas entidades; uma referência detalhada para as entidades pode ser encontrada em documentação externa, como nas especificações XML. No entanto, por conveniência, este tópico lista algumas das entidades de caracteres XML específicas que são normalmente usadas na marcação XAML.

|Caractere|Entidade|Observações|
|---------------|------------|-----------|
|& (e comercial)|\&amp;|Deve ser usado tanto para valores de atributos quanto para o conteúdo de um elemento.|
|> (maior do que o caráter)|\&gt;|Deve ser usado para um valor de atributo, mas > é aceitável como o conteúdo de um elemento, desde que < não o precede.|
|< (menos que o caráter)|\&lt;|Deve ser usado para um \< valor de atributo, mas é aceitável como o conteúdo de um elemento desde que > não o siga.|
|" (marca de cotação reta)|\&quot;|Deve ser usado para um valor de atributo, mas uma marca de cotação reta (") é aceitável como o conteúdo de um elemento. Observe que os valores de atributo podem ser incluídos por uma única marca de cotação direta (') ou por uma marca de cotação direta ("); qualquer caractere que aparecer primeiro define o gabinete de valor de atributo, e a citação alternativa pode então ser usada como um literal dentro do valor.|
|' (marca de cotação única em linha reta)|\&apos;|Deve ser usado para um valor de atributo, mas uma única marca de cotação direta (') é aceitável como o conteúdo de um elemento. Observe que os valores de atributo podem ser incluídos por uma única marca de cotação direta (') ou por uma marca de cotação direta ("); qualquer caractere que aparecer primeiro define o gabinete de valor de atributo, e a citação alternativa pode então ser usada como um literal dentro do valor.|
|(mapeamentos numéricos de caracteres)|&#*[inteiro]*; ou &#x *[hex]*;|XAML suporta mapeamentos numéricos de caracteres na codificação ativa.|
|(espaço ininterrupto)|&\#160; (assumindo a codificação UTF-8)|Para elementos de documento de fluxo, ou <xref:System.Windows.Controls.TextBox>elementos que tomam texto, como o WPF, espaços ininterruptos não são normalizados fora da marcação, mesmo para `xml:space="default"`. (Para obter mais informações, consulte [o processamento de espaço branco em XAML](white-space-processing.md).)|

## <a name="xml-comment-format"></a>Formato de comentário XML

XAML usa o formato de comentário XML: o início do comentário é `<!--`, o final do comentário é `-->,` e a seqüência `--` não deve ocorrer dentro do comentário.

## <a name="xml-processing-instructions"></a>Instruções de processamento XML

XAML lida com instruções de processamento XML de acordo com as especificações XML, que afirmam que as instruções devem ser passadas. O processamento XAML em Serviços XAML .NET não usa nenhuma instrução de processamento. Outras estruturas existentes que usam XAML também não usam instruções de processamento do XAML.

## <a name="see-also"></a>Confira também

- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Gramática XamlName](xamlname-grammar.md)
- [Processamento de espaço em branco em XAML](white-space-processing.md)
