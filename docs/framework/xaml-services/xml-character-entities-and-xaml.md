---
title: Entidades e XAML de caractere XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b325c931579606f6d1d90eb821766a4110acfd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xml-character-entities-and-xaml"></a>Entidades e XAML de caractere XML
XAML usa entidades de caractere definidas no XML para caracteres especiais. Este tópico descreve algumas entidades de caractere específico e considerações gerais para outros conceitos XML em XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Entidades de caractere e problemas de escape que são exclusivos para XAML  
 Marcação XAML normalmente usa as mesmas entidades de caractere e sequências de escape que são definidas no XML.  
  
 A exceção principal é que chaves ({e}) têm significado em XAML, pois esses caracteres informam um processador XAML que uma sequência de caracteres delimitada por chaves deve ser interpretada como uma extensão de marcação. Para obter mais informações sobre extensões de marcação, consulte [extensões de marcação para XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
 No entanto, você ainda pode exibir as chaves como caracteres literais usando uma sequência de escape que é específica de XAML em vez de XML. Para obter mais informações, consulte [{sequência de Escape - extensão de marcação](escape-sequence-markup-extension.md).  
  
 Observe que uma barra invertida (\\) não requer uma sequência de escape quando ela é tratada como uma cadeia de caracteres.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Entidades de caractere XML  
 Conforme mencionado anteriormente, a maioria das entidades de caractere e sequências de escape que são normalmente usadas para gravar marcação XAML são definidas pelo XML. Este tópico não fornece a lista completa dessas entidades; uma referência detalhada para as entidades pode ser encontrada em documentação externa, como nas especificações de XML. No entanto, para sua conveniência, este tópico lista algumas das entidades de caractere XML específicas são geralmente usadas na marcação XAML.  
  
|Caractere|Entidade|Observações|  
|---------------|------------|-----------|  
|& (E comercial)|\&amp;|Deve ser usado para valores de atributo e conteúdo de um elemento.|  
|> (maior-de caractere)|\&gt;|Deve ser usado para um valor de atributo, mas > é aceitável como o conteúdo de um elemento, contanto que < não precedê-lo.|  
|< (menor-de caractere)|\&lt;|Deve ser usado para um valor de atributo, mas \< é aceitável como o conteúdo de um elemento, contanto que > não segue.|  
|"(aspas normais)|\&quot;|Deve ser usado para um valor de atributo, mas uma aspa simples (') é aceitável como o conteúdo de um elemento. Observe que os valores de atributo podem ser delimitados por uma aspa simples simples (') ou por uma aspa simples ('); qualquer caractere que aparecer primeiro define o compartimento do valor de atributo e as aspas alternativa podem ser usada como um literal dentro do valor.|  
|' (aspa simples reta)|\&apos;|Deve ser usado para um valor de atributo, mas uma reta aspas simples (') é aceitável como o conteúdo de um elemento. Observe que os valores de atributo podem ser delimitados por uma aspa simples simples (') ou por uma aspa simples ('); qualquer caractere que aparecer primeiro define o compartimento do valor de atributo e as aspas alternativa podem ser usada como um literal dentro do valor.|  
|(mapeamentos de caracteres numéricos)|&#*[inteiro]* ; ou & #x*[hex]*;|XAML oferece suporte a mapeamentos de caracteres numéricos para a codificação ativa.|  
|(espaço incondicional)|&\#160; (supondo que a codificação UTF-8)|Para elementos de fluxo de documento, ou elementos que recebem texto como o WPF <xref:System.Windows.Controls.TextBox>, espaços não separáveis são retirados da marcação, mesmo para `xml:space="default"`. (Para obter mais informações, consulte [processamento de espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Formato de comentário XML  
 XAML usa o formato de comentário XML: o início do comentário é `<!--`, é o fim do comentário `-->,` e a sequência `--` não deve ocorrer dentro do comentário.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Instruções de processamento de XML  
 XAML lida com as instruções de processamento de XML de acordo com as especificações de XML, que as instruções devem ser passadas do estado. Serviços XAML do .NET Framework de processamento de XAML não usa nenhuma instrução de processamento. Outras estruturas existentes que usam XAML também não usar instruções de processamento de XAML.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensões de marcação e XAML do WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Gramática XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [Processamento de Espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
