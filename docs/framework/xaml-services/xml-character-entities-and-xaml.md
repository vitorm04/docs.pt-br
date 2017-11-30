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
ms.openlocfilehash: 5973c67b26e07bba69383cc625ff34493d825a41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-character-entities-and-xaml"></a><span data-ttu-id="9cabf-102">Entidades e XAML de caractere XML</span><span class="sxs-lookup"><span data-stu-id="9cabf-102">XML Character Entities and XAML</span></span>
<span data-ttu-id="9cabf-103">XAML usa entidades de caractere definidas no XML para caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="9cabf-103">XAML uses character entities defined in XML for special characters.</span></span> <span data-ttu-id="9cabf-104">Este tópico descreve algumas entidades de caractere específico e considerações gerais para outros conceitos XML em XAML.</span><span class="sxs-lookup"><span data-stu-id="9cabf-104">This topic describes some specific character entities and general considerations for other XML concepts in XAML.</span></span>  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a><span data-ttu-id="9cabf-105">Entidades de caractere e problemas de escape que são exclusivos para XAML</span><span class="sxs-lookup"><span data-stu-id="9cabf-105">Character Entities and Escaping Issues That Are Unique to XAML</span></span>  
 <span data-ttu-id="9cabf-106">Marcação XAML normalmente usa as mesmas entidades de caractere e sequências de escape que são definidas no XML.</span><span class="sxs-lookup"><span data-stu-id="9cabf-106">XAML markup typically uses the same character entities and escape sequences that are defined in XML.</span></span>  
  
 <span data-ttu-id="9cabf-107">A exceção principal é que chaves ({e}) têm significado em XAML, pois esses caracteres informam um processador XAML que uma sequência de caracteres delimitada por chaves deve ser interpretada como uma extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="9cabf-107">The main exception is that braces ({ and }) have significance in XAML because these characters inform a XAML processor that a character sequence enclosed by braces must be interpreted as a markup extension.</span></span> <span data-ttu-id="9cabf-108">Para obter mais informações sobre extensões de marcação, consulte [extensões de marcação para XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9cabf-108">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
 <span data-ttu-id="9cabf-109">No entanto, você ainda pode exibir as chaves como caracteres literais usando uma sequência de escape que é específica de XAML em vez de XML.</span><span class="sxs-lookup"><span data-stu-id="9cabf-109">However, you can still display the braces as literal characters by using an escape sequence that is particular to XAML instead of XML.</span></span> <span data-ttu-id="9cabf-110">Para obter mais informações, consulte [{sequência de Escape - extensão de marcação](escape-sequence-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="9cabf-110">For more information, see [{} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).</span></span>  
  
 <span data-ttu-id="9cabf-111">Observe que uma barra invertida (\\) não requer uma sequência de escape quando ela é tratada como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9cabf-111">Note that a backslash (\\) does not require an escape sequence when it is handled as a string.</span></span>  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a><span data-ttu-id="9cabf-112">Entidades de caractere XML</span><span class="sxs-lookup"><span data-stu-id="9cabf-112">XML Character Entities</span></span>  
 <span data-ttu-id="9cabf-113">Conforme mencionado anteriormente, a maioria das entidades de caractere e sequências de escape que são normalmente usadas para gravar marcação XAML são definidas pelo XML.</span><span class="sxs-lookup"><span data-stu-id="9cabf-113">As mentioned previously, most character entities and escape sequences that are typically used to write XAML markup are defined by XML.</span></span> <span data-ttu-id="9cabf-114">Este tópico não fornece a lista completa dessas entidades; uma referência detalhada para as entidades pode ser encontrada em documentação externa, como nas especificações de XML.</span><span class="sxs-lookup"><span data-stu-id="9cabf-114">This topic does not provide the complete list of these entities; a detailed reference for the entities can be found in external documentation, such as in XML specifications.</span></span> <span data-ttu-id="9cabf-115">No entanto, para sua conveniência, este tópico lista algumas das entidades de caractere XML específicas são geralmente usadas na marcação XAML.</span><span class="sxs-lookup"><span data-stu-id="9cabf-115">However, for convenience, this topic lists some of the specific XML character entities that are typically used in XAML markup.</span></span>  
  
|<span data-ttu-id="9cabf-116">Caractere</span><span class="sxs-lookup"><span data-stu-id="9cabf-116">Character</span></span>|<span data-ttu-id="9cabf-117">Entidade</span><span class="sxs-lookup"><span data-stu-id="9cabf-117">Entity</span></span>|<span data-ttu-id="9cabf-118">Observações</span><span class="sxs-lookup"><span data-stu-id="9cabf-118">Notes</span></span>|  
|---------------|------------|-----------|  
|<span data-ttu-id="9cabf-119">& (E comercial)</span><span class="sxs-lookup"><span data-stu-id="9cabf-119">& (ampersand)</span></span>|&amp;|<span data-ttu-id="9cabf-120">Deve ser usado para valores de atributo e conteúdo de um elemento.</span><span class="sxs-lookup"><span data-stu-id="9cabf-120">Must be used both for attribute values and for content of an element.</span></span>|  
|<span data-ttu-id="9cabf-121">> (maior-de caractere)</span><span class="sxs-lookup"><span data-stu-id="9cabf-121">> (greater-than character)</span></span>|&gt;|<span data-ttu-id="9cabf-122">Deve ser usado para um valor de atributo, mas > é aceitável como o conteúdo de um elemento, contanto que < não precedê-lo.</span><span class="sxs-lookup"><span data-stu-id="9cabf-122">Must be used for an attribute value, but > is acceptable as the content of an element as long as < does not precede it.</span></span>|  
|<span data-ttu-id="9cabf-123">< (menor-de caractere)</span><span class="sxs-lookup"><span data-stu-id="9cabf-123">< (less-than character)</span></span>|&lt;|<span data-ttu-id="9cabf-124">Deve ser usado para um valor de atributo, mas \< é aceitável como o conteúdo de um elemento, contanto que > não segue.</span><span class="sxs-lookup"><span data-stu-id="9cabf-124">Must be used for an attribute value, but \< is acceptable as the content of an element as long as > does not follow it.</span></span>|  
|<span data-ttu-id="9cabf-125">"(aspas normais)</span><span class="sxs-lookup"><span data-stu-id="9cabf-125">" (straight quotation mark)</span></span>|&quot;|<span data-ttu-id="9cabf-126">Deve ser usado para um valor de atributo, mas uma aspa simples (') é aceitável como o conteúdo de um elemento.</span><span class="sxs-lookup"><span data-stu-id="9cabf-126">Must be used for an attribute value, but a straight quotation mark (") is acceptable as the content of an element.</span></span> <span data-ttu-id="9cabf-127">Observe que os valores de atributo podem ser delimitados por uma aspa simples simples (') ou por uma aspa simples ('); qualquer caractere que aparecer primeiro define o compartimento do valor de atributo e as aspas alternativa podem ser usada como um literal dentro do valor.</span><span class="sxs-lookup"><span data-stu-id="9cabf-127">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="9cabf-128">' (aspa simples reta)</span><span class="sxs-lookup"><span data-stu-id="9cabf-128">' (single straight quotation mark)</span></span>|&apos;|<span data-ttu-id="9cabf-129">Deve ser usado para um valor de atributo, mas uma reta aspas simples (') é aceitável como o conteúdo de um elemento.</span><span class="sxs-lookup"><span data-stu-id="9cabf-129">Must be used for an attribute value, but a single straight quotation mark (') is acceptable as the content of an element.</span></span> <span data-ttu-id="9cabf-130">Observe que os valores de atributo podem ser delimitados por uma aspa simples simples (') ou por uma aspa simples ('); qualquer caractere que aparecer primeiro define o compartimento do valor de atributo e as aspas alternativa podem ser usada como um literal dentro do valor.</span><span class="sxs-lookup"><span data-stu-id="9cabf-130">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="9cabf-131">(mapeamentos de caracteres numéricos)</span><span class="sxs-lookup"><span data-stu-id="9cabf-131">(numeric character mappings)</span></span>|<span data-ttu-id="9cabf-132">&#*[inteiro]* ; ou & #x*[hex]*;</span><span class="sxs-lookup"><span data-stu-id="9cabf-132">&#*[integer]*; or &#x*[hex]*;</span></span>|<span data-ttu-id="9cabf-133">XAML oferece suporte a mapeamentos de caracteres numéricos para a codificação ativa.</span><span class="sxs-lookup"><span data-stu-id="9cabf-133">XAML supports numeric character mappings into the encoding that is active.</span></span>|  
|<span data-ttu-id="9cabf-134">(espaço incondicional)</span><span class="sxs-lookup"><span data-stu-id="9cabf-134">(nonbreaking space)</span></span>|<span data-ttu-id="9cabf-135">&\#160; (supondo que a codificação UTF-8)</span><span class="sxs-lookup"><span data-stu-id="9cabf-135">&\#160; (assuming UTF-8 encoding)</span></span>|<span data-ttu-id="9cabf-136">Para elementos de fluxo de documento, ou elementos que recebem texto como o WPF <xref:System.Windows.Controls.TextBox>, espaços não separáveis são retirados da marcação, mesmo para `xml:space="default"`.</span><span class="sxs-lookup"><span data-stu-id="9cabf-136">For flow document elements, or elements that take text such as the WPF <xref:System.Windows.Controls.TextBox>, nonbreaking spaces are not normalized out of the markup, even for `xml:space="default"`.</span></span> <span data-ttu-id="9cabf-137">(Para obter mais informações, consulte [processamento de espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span><span class="sxs-lookup"><span data-stu-id="9cabf-137">(For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span></span>|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a><span data-ttu-id="9cabf-138">Formato de comentário XML</span><span class="sxs-lookup"><span data-stu-id="9cabf-138">XML Comment Format</span></span>  
 <span data-ttu-id="9cabf-139">XAML usa o formato de comentário XML: o início do comentário é `<!--`, é o fim do comentário `-->,` e a sequência `--` não deve ocorrer dentro do comentário.</span><span class="sxs-lookup"><span data-stu-id="9cabf-139">XAML uses the XML comment format: the start of the comment is `<!--`, the end of comment is `-->,` and the sequence `--` must not occur within the comment.</span></span>  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a><span data-ttu-id="9cabf-140">Instruções de processamento de XML</span><span class="sxs-lookup"><span data-stu-id="9cabf-140">XML Processing Instructions</span></span>  
 <span data-ttu-id="9cabf-141">XAML lida com as instruções de processamento de XML de acordo com as especificações de XML, que as instruções devem ser passadas do estado.</span><span class="sxs-lookup"><span data-stu-id="9cabf-141">XAML handles XML processing instructions according to XML specifications, which state that the instructions must be passed through.</span></span> <span data-ttu-id="9cabf-142">Serviços XAML do .NET Framework de processamento de XAML não usa nenhuma instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="9cabf-142">XAML processing in .NET Framework XAML Services  does not use any processing instructions.</span></span> <span data-ttu-id="9cabf-143">Outras estruturas existentes que usam XAML também não usar instruções de processamento de XAML.</span><span class="sxs-lookup"><span data-stu-id="9cabf-143">Other existing frameworks that use XAML also do not use processing instructions from XAML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cabf-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cabf-144">See Also</span></span>  
 [<span data-ttu-id="9cabf-145">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="9cabf-145">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="9cabf-146">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="9cabf-146">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="9cabf-147">Gramática XamlName</span><span class="sxs-lookup"><span data-stu-id="9cabf-147">XamlName Grammar</span></span>](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [<span data-ttu-id="9cabf-148">Processamento de Espaço em branco em XAML</span><span class="sxs-lookup"><span data-stu-id="9cabf-148">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
