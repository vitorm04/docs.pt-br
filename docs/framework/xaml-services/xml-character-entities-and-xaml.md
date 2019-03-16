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
ms.openlocfilehash: 3fefbe9696ba7618dc811c6ac8f600bb6322dad5
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58048053"
---
# <a name="xml-character-entities-and-xaml"></a>Entidades e XAML de caractere XML
XAML usa entidades de caracteres definidas no XML para caracteres especiais. Este tópico descreve algumas entidades de caractere específico e considerações gerais para outros conceitos XML em XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Entidades de caractere e problemas de escape que são exclusivos para XAML  
 Normalmente, a marcação XAML usa as mesmas entidades de caractere e sequências de escape que são definidas no XML.  
  
 A exceção principal é que chaves ({e}) têm significado em XAML, pois esses caracteres informam um processador XAML que uma sequência de caracteres delimitada por chaves deve ser interpretada como uma extensão de marcação. Para obter mais informações sobre extensões de marcação, consulte [extensões de marcação para visão geral de XAML](markup-extensions-for-xaml-overview.md).  
  
 No entanto, você ainda pode exibir as chaves como caracteres literais usando uma sequência de escape que é específica de XAML em vez de XML. Para obter mais informações, consulte [ {} sequência de Escape - extensão de marcação](escape-sequence-markup-extension.md).  
  
 Observe que uma barra invertida (\\) não requer uma sequência de escape quando ela é tratada como uma cadeia de caracteres.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Entidades de caractere XML  
 Conforme mencionado anteriormente, a maioria das entidades de caractere e sequências de escape que normalmente são usadas para gravar a marcação XAML são definidas por XML. Este tópico não fornece a lista completa dessas entidades; uma referência detalhada sobre as entidades pode ser encontrada na documentação externa, como nas especificações de XML. No entanto, para sua conveniência, este tópico lista algumas das entidades específicas de caracteres XML que normalmente são usadas na marcação XAML.  
  
|Caractere|Entidade|Observações|  
|---------------|------------|-----------|  
|& (E comercial)|\&amp;|Deve ser usado tanto para valores de atributo para o conteúdo de um elemento.|  
|> (maior-que caractere)|\&gt;|Deve ser usado para um valor de atributo, mas > é aceitável como o conteúdo de um elemento, desde que < não precedê-lo.|  
|< (menor-que caractere)|\&lt;|Deve ser usado para um valor de atributo, mas \< é aceitável como o conteúdo de um elemento, desde que > não segue.|  
|"(aspas normais)|\&quot;|Deve ser usado para um valor de atributo, mas uma marca de aspas reta (") é aceitável como o conteúdo de um elemento. Observe que os valores de atributo podem ser colocados por uma única marca de aspas reta (') ou por uma marca de aspas reta ("); qualquer caractere que aparecer primeiro define o compartimento de valor de atributo e a citação alternativa pode ser usada como um literal dentro do valor.|  
|' (aspa simples reta)|\&apos;|Deve ser usado para um valor de atributo, mas uma única marca de aspas reta (') é aceitável como o conteúdo de um elemento. Observe que os valores de atributo podem ser colocados por uma única marca de aspas reta (') ou por uma marca de aspas reta ("); qualquer caractere que aparecer primeiro define o compartimento de valor de atributo e a citação alternativa pode ser usada como um literal dentro do valor.|  
|(mapeamentos de caracteres numéricos)|&#*[inteiro]* ; ou &#x *[hex]*;|XAML dá suporte a mapeamentos de caracteres numéricos para a codificação ativa.|  
|(espaço incondicional)|&\#160; (supondo que a codificação UTF-8)|Para elementos de fluxo de documento, ou elementos que usam o texto como o WPF <xref:System.Windows.Controls.TextBox>, espaços não separáveis são retirados da marcação, mesmo para `xml:space="default"`. (Para obter mais informações, consulte [XAML de processamento de espaço em branco](whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Formato de comentário XML  
 XAML usa o formato de comentário XML: o início do comentário é `<!--`, é o fim do comentário `-->,` e a sequência `--` não deve ocorrer dentro do comentário.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Instruções de processamento de XML  
 XAML lida com as instruções de processamento de XML acordo com especificações de XML, que as instruções devem ser passadas de estado. Serviços de XAML do .NET Framework de processamento de XAML não usa nenhuma instrução de processamento. Outras estruturas existentes que usam XAML também não usar instruções de processamento de XAML.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Extensões de marcação e XAML do WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Gramática XamlName](xamlname-grammar.md)
- [Espaço em branco em XAML de processamento](whitespace-processing-in-xaml.md)
