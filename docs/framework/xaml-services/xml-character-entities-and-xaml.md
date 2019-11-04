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
ms.openlocfilehash: 92bf49ac1ae67fb8d2e268eeaaf63cd72d9f6251
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458808"
---
# <a name="xml-character-entities-and-xaml"></a>Entidades e XAML de caractere XML
O XAML usa entidades de caracteres definidas em XML para caracteres especiais. Este tópico descreve algumas entidades de caractere específicas e considerações gerais para outros conceitos XML em XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Entidades de caracteres e problemas de escape que são exclusivos do XAML  
 A marcação XAML normalmente usa as mesmas entidades de caractere e sequências de escape que são definidas em XML.  
  
 A principal exceção é que as chaves ({e}) têm significância em XAML porque esses caracteres informam um processador XAML que uma sequência de caracteres entre chaves deve ser interpretada como uma extensão de marcação. Para obter mais informações sobre extensões de marcação, consulte [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).  
  
 No entanto, você ainda pode exibir as chaves como caracteres literais usando uma sequência de escape que é específica para XAML em vez de XML. Para obter mais informações, consulte [{} escape Sequence-Markup Extension](escape-sequence-markup-extension.md).  
  
 Observe que uma barra invertida (\\) não requer uma sequência de escape quando ela é tratada como uma cadeia de caracteres.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Entidades de caractere XML  
 Como mencionado anteriormente, a maioria das entidades de caractere e as sequências de escape normalmente usadas para gravar marcação XAML são definidas pelo XML. Este tópico não fornece a lista completa dessas entidades; uma referência detalhada para as entidades pode ser encontrada na documentação externa, como em especificações XML. No entanto, para sua conveniência, este tópico lista algumas das entidades de caractere XML específicas que normalmente são usadas na marcação XAML.  
  
|Caractere|Entidade|Anotações|  
|---------------|------------|-----------|  
|& (e comercial)|\&amp;|Deve ser usado para valores de atributo e para o conteúdo de um elemento.|  
|> (caractere maior que)|\&gt;|Deve ser usado para um valor de atributo, mas > é aceitável como o conteúdo de um elemento, desde que < não o preceda.|  
|< (caractere menor que)|\&lt;|Deve ser usado para um valor de atributo, mas \< é aceitável como o conteúdo de um elemento, desde que > não o siga.|  
|"(aspa reta)|\&quot;|Deve ser usado para um valor de atributo, mas uma aspa reta (") é aceitável como o conteúdo de um elemento. Observe que os valores de atributo podem ser colocados por uma aspa simples (') ou por uma aspa reta ("); o caractere que aparece primeiro define o compartimento de valor do atributo e a aspa alternativa pode ser usada como um literal dentro do valor.|  
|' (aspa reta simples)|\&apos;|Deve ser usado para um valor de atributo, mas uma única aspa simples (') é aceitável como o conteúdo de um elemento. Observe que os valores de atributo podem ser colocados por uma aspa simples (') ou por uma aspa reta ("); o caractere que aparece primeiro define o compartimento de valor do atributo e a aspa alternativa pode ser usada como um literal dentro do valor.|  
|(mapeamentos de caracteres numéricos)|&# *[inteiro]* ; ou & #x *[hex]* ;|O XAML dá suporte a mapeamentos de caracteres numéricos na codificação ativa.|  
|(espaço não separável)|&\#160; (supondo que a codificação UTF-8)|Para elementos do documento de fluxo ou elementos que usam texto como o <xref:System.Windows.Controls.TextBox>do WPF, espaços não separáveis não são normalizados da marcação, mesmo para `xml:space="default"`. (Para obter mais informações, consulte [espaço em branco processamento em XAML](whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Formato de comentário XML  
 O XAML usa o formato de comentário XML: o início do comentário é `<!--`, o final do comentário é `-->,` e a sequência `--` não deve ocorrer dentro do comentário.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Instruções de processamento XML  
 O XAML lida com as instruções de processamento XML de acordo com as especificações de XML, que são o estado que as instruções devem passar. O processamento XAML no .NET Framework serviços XAML não usa nenhuma instrução de processamento. Outras estruturas existentes que usam XAML também não usam instruções de processamento do XAML.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML do WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Gramática XamlName](xamlname-grammar.md)
- [Processamento de espaço em branco em XAML](whitespace-processing-in-xaml.md)
