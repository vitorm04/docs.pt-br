---
title: "Linguagem de expressão regular – referência rápida"
description: "Linguagem de expressão regular – referência rápida"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8c5dee8c-7bc7-4e6e-aff1-986965c4d98e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: a6644fc2431beafa2128287eeac73bd598ee304a
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expression-language---quick-reference"></a>Linguagem de expressão regular – referência rápida

Uma expressão regular é um padrão ao qual o mecanismo de expressões regulares tenta corresponder no texto de entrada. Um padrão consiste em um ou mais literais de caracteres, operadores ou constructos. Para ver uma breve introdução, consulte [Expressões regulares no .NET](regular-expressions.md). 

Cada seção desta referência rápida lista uma categoria específica de caracteres, operadores e constructos que você pode usar para definir expressões regulares: 

* [Escapes de caracteres](#character-escapes)

* [Classes de caracteres](#character-classes)
      
* [Âncoras](#anchors)
    
* [Constructos de agrupamento](#grouping-constructs)
      
* [Quantificadores](#quantifiers)
    
* [Constructos de referência inversa](#backreference-constructs)
      
* [Constructos de alternância](#alternation-constructs)
     
* [Substituições](#substitutions)
      
* [Opções de expressões regulares](#regular-expression-options)
      
* [Constructos diversos](#miscellaneous-constructs)

Também fornecemos essas informações em dois formatos, que podem ser baixados e impressos para uma consulta simplificada: 

* [Baixar no formato Word (.docx)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
    
* [Baixar no formato PDF (.pdf)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
    
## <a name="character-escapes"></a>Escapes de caracteres

O caractere de barra invertida (\) em uma expressão regular indica que o próximo caractere é um caractere especial (conforme mostrado na tabela a seguir) ou se deve ser interpretado literalmente. Para obter mais informações, consulte [Escapes de caracteres em expressões regulares](escapes.md). 

Caractere com escape | Descrição | Padrão | Correspondências
----------------- | ----------- | ------- | -------
**\a** | Corresponde a um caractere de sino, \u0007. | `\a` | “\u0007” em “Error!” + ‘\u0007’
**\b** | Em uma classe de caractere, corresponde a um backspace, \ u0008. | `[\b]{3,}` | “\b\b\b\b” em “\b\b\b\b”
**\t** | Corresponde a uma tabulação, \u0009. | `(\w+)\t` | “item1\t”, “item2\t” em “item1\titem2\t”
**\r** | Corresponde a um retorno de carro, \u000D. (**\r** não é equivalente ao caractere de nova linha, **\n**.) | `\r\n(\w+)` | “\r\nThese” em “\r\nThese are\ntwo lines.”
**\v** | Corresponde a uma tabulação vertical, \u000B. | `[\v]{2,}` | “\v\v\v” em “\v\v\v”
**\f** | Corresponde a um avanço de página, \u000C. | `[\f]{2,}` | “\f\f\f” em “\f\f\f” 
**\n** | Corresponde a uma nova linha, \u000A. | `\r\n(\w+)` | “\r\nThese” em “\r\nThese are\ntwo lines.”
**\e** | Corresponde a um escape, \u001B. | `\e` | “\x001B” em “\x001B”
**\**_nnn_ | Usa representação octal para especificar um caractere (*nnn* consiste em dois ou três dígitos). | `\w\040\w` | “a b”, “c d” em “a bc d”
**\x**_nn_ | Usa representação hexadecimal para especificar um caractere (*nn* consiste exatamente em dois dígitos). | `\w\x20\w` | “a b”, “c d” em “a bc d”
**\c**_X_ ou **\c**_x_ | Corresponde ao caractere de controle ASCII especificado por *X* ou *x*, em que *X* ou *x* é a letra do caractere de controle. | `\cC` | “\x0003” em “\x0003” (Ctrl-C) 
**\u**_nnnn_ | Corresponde a um caractere Unicode usando representação hexadecimal (exatamente quatro dígitos, como representado por *nnnn*). | `\w\u0020\w` | “a b”, “c d” em “a bc d”
**\\** | Quando seguido por um caractere que não é reconhecido como um caractere de escape nesta e em outras tabelas deste tópico, corresponde a esse caractere. Por exemplo, __\*__ é o mesmo que **\x2A** e **\.** é o mesmo que **\x2E**. Isso permite que o mecanismo de expressões regulares remova ambiguidades de elementos da linguagem (como `*` ou `?`) e caracteres literais (representados por `\*` ou `\?)`). | `\d+[\+-x\*]\d+` | “2+2” e “3*9” em “(2+2) * 3*9”
 
## <a name="character-classes"></a>Classes de caracteres

Uma classe de caractere corresponde a qualquer um dos conjuntos de caracteres. As classes de caracteres incluem os elementos de linguagem listados na tabela a seguir. Para obter mais informações, consulte [Classes de caracteres em expressões regulares](classes.md).

Classe de caractere | Descrição | Padrão | Correspondências
--------------- | ----------- | ------- | ------- 
__[__*character_group*__]__ | Corresponde a qualquer caractere único em character_group. Por padrão, a correspondência diferencia maiúsculas de minúsculas. | `[ae]` | “a” em “gray”, “a”, “e” em “lane”
__[^__*character_group*__]__ | Negação: corresponde a qualquer caractere único que não esteja em *character_group*. Por padrão, caracteres em *character_group* diferenciam maiúsculas de minúsculas. | `[^aei]` |  “r”, “g”, “n” em “reign”
__[__*first-last*__]__ | Intervalo de caracteres: corresponde a qualquer caractere único no intervalo entre *first* e *last*. | `[A-Z]` | “A”, “B” em “AB123”
**.** | Curinga: corresponde a qualquer caractere único, exceto \n. Para corresponder a um caractere literal de ponto (. ou \u002E), deve ser antecedido pelo caractere de escape (\.). | `a.e` |  “ave” em “nave”, “ate” em “water”
__\p{__*name*__}__ | Corresponde a qualquer caractere único na categoria geral Unicode ou no bloco nomeado especificado por *name*. | `\p{Lu}`, `\p{IsCyrillic}` | “C”, “L” em “City Lights”, “?”, “?” em “??em”
__\P{__*name*__}__ | Corresponde a qualquer caractere único que não esteja na categoria geral Unicode ou no bloco nomeado especificado por *name*. | `\P{Lu}`, `\P{IsCyrillic}` |` “i”, “t”, “y” em “City”, “e”, “m” em “??em”
**\w** | Corresponde a qualquer caractere de palavra. | `\w` | “I”, “D”, “A”, “1”, “3” em “ID A1.3” 
**\W** | Corresponde a qualquer caractere que não seja uma palavra. | `\W` | “ ”, “.” em “ID A1.3”
**\s** | Corresponde a qualquer caractere de espaço em branco. | `\w\s` | “D “ em “ID A1.3”
**\S** | Corresponde a qualquer caractere que não seja um caractere de espaço em branco. | `\s\S` | “ _” em “int __ctr” 
**\d** | Corresponde a qualquer dígito decimal. | `\d` | “4” em “4 = IV” 
**\D** | Corresponde a qualquer caractere que não seja uma dígito decimal | `\D` | “ ”, “=”, “ ”, “I”, “V” em “4 = IV” 

## <a name="anchors"></a>Âncoras

Âncoras ou asserções atômicas de largura zero, fazem com que uma correspondência tenha êxito ou falha dependendo da posição atual na cadeia de caracteres, mas não fazem com que o mecanismo avance na cadeia de caracteres ou consuma caracteres. Os metacaracteres listados na tabela a seguir são âncoras. Para obter mais informações, consulte [Âncoras em expressões regulares](anchors.md).

Asserção | Descrição | Padrão | Correspondências
--------- | ----------- | ------- | ------- 
**^** | A correspondência deve começar no início da cadeia de caracteres ou da linha. | `^\d{3}` | “901” em “901-333-”
**$** | A correspondência deve ocorrer no final da cadeia de caracteres ou antes de **\n** no final da linha ou da cadeia de caracteres. | `-\d{3}$` | “-333” em “-901-333”
**\A** | A correspondência deve ocorrer no início da cadeia de caracteres. | `\A\d{3}` | “901” em “901-333-”
**\Z** | A correspondência deve ocorrer no final da cadeia de caracteres ou antes de **\n** no final da cadeia de caracteres. | `-\d{3}\Z` | “-333” em “-901-333”
**\z** | A correspondência deve ocorrer no final da cadeia de caracteres. | `-\d{3}\z` | “-333” em “-901-333”
**\G** | A correspondência deve ocorrer no ponto em que a correspondência anterior foi encerrada. | `\G\(\d\)` | “(1)”, “(3)”, “(5)” em “(1)(3)(5)[7]&#40;9)”
**\b** | A correspondência deve ocorrer em um limite entre um caractere **\w** (alfanumérico) e um caractere **\W** (não alfanumérico). | `\b\w+\s\w+\b` | “them theme”, “them them” em “them theme them them” 
**\B** | A correspondência não deve ocorrer em um limite **\b**. | `\Bend\w*\b` | “ends”, “ender” em “end sends endure lender”

## <a name="grouping-constructs"></a>Agrupando construtores

Os constructos de agrupamento delineiam subexpressões de uma expressão regular e, em geral, capturam subcadeias de caracteres de uma cadeia de caracteres de entrada. Os constructos de agrupamento incluem os elementos de linguagem listados na tabela a seguir. Para obter mais informações, consulte [Constructos de agrupamento em expressões regulares](grouping.md).

Constructo de agrupamento | Descrição | Padrão | Correspondências
------------------ | ----------- | ------- | ------- 
**(**_subexpression_**)** | Captura a subexpressão correspondente e atribui a ela um número ordinal com base um. | `(\w)\1` | “ee” em “deep”
**(?**<name> _subexpression_**)** | Captura a subexpressão correspondente em um grupo nomeado. | `(?<double>\w)\k<double>` | “ee” em “deep”
**(?**<name1-name2> _subexpression_**)** | Especifica uma definição de grupo de balanceamento. Para obter mais informações, consulte a seção [Definição de grupo de balanceamento](grouping.md#balancing-group-definitions) em [Constructos de agrupamento em expressões regulares](grouping.md). | `(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$` | “((1-3)*(3-1))” em “3+2^((1-3)*(3-1))”
**(?**: subexpression**)** | Define um grupo de não captura. | `Write(?:Line)?` | “WriteLine” em “Console.WriteLine()”, “Write” em “Console.Write(value)”
**(?imnsx-imnsx**: _subexpression_**)** | Aplica ou desabilita as opções especificadas em _subexpressão_. Para obter mais informações, consulte [Opções de expressões regulares](options.md). | `A\d{2}(?i:\w+)\b` | “A12xl”, “A12XL” em “A12xl A12XL a12xl”
**(?**= _subexpression_**)** | Asserções lookahead positivas de largura zero. | `\w+(?=\.)` | “is”, “ran” e “out” em “He is. The dog ran. The sun is out.”
**(?!** _subexpression_**)** | Asserções lookahead negativas de largura zero. | `\b(?!un)\w+\b` | “sure”, “used” em “unsure sure unity used”
**(?**<= _subexpression_**)** | Asserção lookbehind positiva de largura zero. | `(?<=19)\d{2}\b` | “99”, “50”, “05” em “1851 1999 1950 1905 2003”
**(?**<! _subexpression_**)** | Asserção lookbehind negativa de largura zero. | `(?<!19)\d{2}\b` | “51”, “03” em “1851 1999 1950 1905 2003”
**(?**> _subexpression_**)** | Subexpressão sem retrocesso (ou “Greedy”). | `[13579](?>A+B+)` | “1ABB”, “3ABB” e “5AB” em “1ABB 3ABBC 5AB 5AC”

## <a name="quantifiers"></a>Quantificadores

Um quantificador especifica quantas instâncias do elemento anterior (que pode ser um caractere, um grupo ou uma classe de caracteres) devem estar presentes na cadeia de caracteres de entrada para que uma correspondência ocorra. Os quantificadores incluem os elementos de linguagem listados na tabela a seguir. Para obter mais informações, consulte [Quantificadores em expressões regulares](quantifiers.md).

Quantificador | Descrição | Padrão | Correspondências
---------- | ----------- | ------- | -------
__*__ | Corresponde ao elemento anterior zero ou mais vezes. | `\d*\.\d` | “.0”, “19.9”, “219.9”
**+** | Corresponde ao elemento anterior uma ou mais vezes. | `"be+"` | “bee” em “been”, “be” em “bent”
**?** | Corresponde ao elemento anterior zero ou uma vez. | `"rai?n"` | “ran”, “rain”
**{**_n_**}** | Corresponde ao elemento anterior exatamente *n* vezes. | `",\d{3}"` | “.043” em “1.043.6”, “.876”, “.543” e “.210” em “9.876.543.210”
**{**_n_,**}** | Corresponde ao elemento anterior pelo menos *n* vezes. | `"\d{2,}"` | “166”, “29”, “1930”
**{**_n_,_m_**}** | Corresponde ao elemento anterior pelo menos *n* vezes, mas não mais do que *m* vezes. | `"\d{3,5}"` | “166”, “17668”; “19302” em “193024”
__*?__ | Corresponde ao elemento anterior zero ou mais vezes, mas o menor número de vezes possível. | `\d*?\.\d` | “.0”, “19.9”, “219.9”
**+?** | Corresponde ao elemento anterior uma ou mais vezes, mas o menor número de vezes possível. | `"be+?"` | “be” em “been”, “be” em “bent”
**??** | Corresponde ao elemento anterior zero ou uma vez, mas o menor número de vezes possível. | `"rai??n"` | “ran”, “rain”
**{**_n_**}?** | Corresponde ao elemento anterior exatamente *n* vezes. | `",\d{3}?"` | “.043” em “1.043.6”, “.876”, “.543” e “.210” em “9.876.543.210”
**{**_n_,**}?** | Corresponde ao elemento anterior pelo menos *n* vezes, mas o menor número de vezes possível. | `"\d{2,}?"` | “166”, “29”, “1930”
**{**_n_,_m_**}?** | Corresponde ao elemento anterior entre *n* e *m* vezes, mas o menor número de vezes possível. | `"\d{3,5}?"` | “166”, “17668”; “193”, “024” em “193024”

## <a name="backreference-constructs"></a>Construtores de referência inversa

Um referência inversa permite que uma subexpressão correspondida anteriormente seja identificada posteriormente na mesma expressão regular. A tabela a seguir lista os constructos de referência inversa tem suporte nas expressões regulares do .NET Framework. Para obter mais informações, consulte [Constructos de referência inversa em expressões regulares](backreference.md).

Constructo de referência inversa | Descrição | Padrão | Correspondências
----------------------- | ----------- | ------- | -------
**\**_number_ | Referência inversa. Corresponde ao valor de uma subexpressão numerada. | `(\w)\1    ` | “ee” em “seek”
**\k<**_name_**>** | Referência inversa nomeada. Corresponde ao valor de uma expressão nomeada. | `(?<char>\w)\k<char>` | “ee” em “seek”

## <a name="alternation-constructs"></a>Construtores de alternância

Os constructos de alternância modificam uma expressão regular para habilitar uma correspondência do tipo um/ou outro. Esses constructos incluem os elementos de linguagem listados na tabela a seguir. Para obter mais informações, consulte [Constructos de alternância em expressões regulares](alternation.md).

Constructo de alternância | Descrição | Padrão | Correspondências
--------------------- | ----------- | ------- | ------- 
**&#124;** | Corresponde a qualquer elemento separado pelo caractere de barra vertical (*&#124;). | `th(e*&#124;is*&#124;at)` | “the”, “this” em “this is the day. "
__(?(__*expression*__)__*yes*__&#124;__*no*__)__ | Corresponde a *yes* se o padrão de expressão regular designado por *expression* for correspondente. Do contrário, corresponde à parte *no* opcional. *expression* é interpretado como uma asserção de largura zero. | `(?(A)A\d{2}\b*&#124;\b\d{3}\b)` | “A10”, “910” em “A10 C103 910”
**(?(**_name_**)**_yes_&#124;_no_**)** | Corresponde a *yes* se *name*, um grupo de captura nomeado ou numerado, apresenta uma correspondência. Do contrário, corresponde a *no* opcional. | `(?<quoted>")?(?,(quoted).+?"*&#124;\S+\s)` | Dogs.jpg, “Yiska playing.jpg” em “Dogs.jpg “Yiska playing.jpg””

## <a name="substitutions"></a>Substituições

As substituições são elementos de linguagem de expressões regulares com suporte em padrões de substituição. Para obter mais informações, consulte [Substituições em expressões regulares](substitutions.md). Os metacaracteres listados na tabela a seguir são asserções atômicas de largura zero.

Caractere | Descrição | Padrão | Padrão de substituição | Cadeia de caracteres de entrada | Cadeia de caracteres de resultado
--------- | ----------- | ------- | ------------------- | ------------ | ------------- 
**$**_number_ | Substitui a subcadeia de caracteres correspondida pelo grupo *number*. | `\b(\w+)(\s)(\w+)\b` | `$3$2$1` | “one two” | “two one”
**${**_name_**}** | Substitui a subcadeia de caracteres correspondida pelo grupo chamado *name*. | `\b(?<word1>\w+)(\s)(?<word2>\w+)\b` | `${word2} ${word1}` | “one two” | “two one”
**$$** | Substitui um literal “$”. | `\b(\d+)\s?USD` | `$$$1` | “103 USD” | "$103"
**$&** | Substitui uma cópia da correspondência inteira. | `\$?\d*\.?\d+` | `**$&**` | "$1.30" | "**$1.30**"
**$`** | Substitui todo o texto da cadeia de caracteres de entrada antes da correspondência. | `B+` | `$`` | “AABBCC” | “AAAACC”
**$'** | Substitui todo o texto da cadeia de caracteres de entrada após a correspondência. | `B+` | `$'` | “AABBCC” | “AACCCC”
**$+** | Substitui o último grupo que foi capturado. | `B+(C+)` | `$+` | “AABBCCDD” | “AACCDD”
**$_** | Substitui a cadeia de caracteres de entrada inteira. | `B+` | `$_` | “AABBCC” | “AAAABBCCCC”

## <a name="regular-expression-options"></a>Opções de expressões regulares

Você pode especificar opções que controlam como o mecanismo de expressões regulares interpreta uma expressão regular padrão. Muitas dessas opções podem ser especificadas de maneira embutida (no padrão da expressão regular) ou como uma ou mais constantes `RegexOptions`. Essa referência rápida lista somente as opções embutidas. Para obter mais informações sobre opções embutidas e opções de `RegexOptions`, consulte o artigo [Opções de expressões regulares](options.md). 

É possível especificar uma opção embutida de duas formas:

* Usando o constructo diverso **(?imnsx-imnsx)**, em que um sinal de subtração (-) antes de uma opção ou um conjunto de opções desativa essas opções. Por exemplo, **(?i-mn)** ativa a correspondência sem diferenciação de maiúsculas e minúsculas (i), desativa o modo multilinha (**m**) e desativa capturas de grupo sem nome (**n**). A opção se aplica ao padrão de expressão regular no ponto em que a opção é definida e entra em vigor no final do padrão ou no ponto em que outro constructo inverte a opção.

* Usando o constructo de agrupamento **(?imnsx-imnsx:**_subexpression_**)**, que define opções somente para o grupo especificado.

O mecanismo de expressões regulares do .NET dá suporte às opções embutidas a seguir.

Opção | Descrição | Padrão | Correspondências
------ | ----------- | ------- | ------- 
**i** | Use correspondência sem diferenciação de maiúsculas e minúsculas. | **\b(?i)a(?-i)a\w+\b** | “aardvark”, “aaaAuto” em “aardvark AAAuto aaaAuto Adam breakfast” 
**m** | Use o modo multilinha. **^** e **$** correspondem ao início e ao fim de uma linha, em vez do início e fim de uma cadeia de caracteres. | Para ver um exemplo, consulte a seção “Modo multilinha” em [Opções de expressões regulares](options.md). | 
**n*** | Não capture grupos sem nome. | Para ver um exemplo, consulte a seção “Apenas capturas explícitas” em [Opções de expressões regulares](options.md). | 
**s** | Use o modo de linha única. | Para ver um exemplo, consulte a seção “Modo de linha única” em [Opções de expressões regulares](options.md). | 
**x** | Ignore espaços em branco sem escape no padrão da expressão regular. | **\b(?x) \d+ \s \w+** | “1 aardvark”, “2 cats” em “1 aardvark 2 cats IV centurions” 

##<a name="miscellaneous-constructs"></a>Diversos construtores

Os constructos diversos modificam um expressão regular padrão ou fornecem informações sobre ela. A tabela a seguir lista os constructos diversos que têm suporte no .NET. Para obter mais informações, consulte [Constructos diversos em expressões regulares](miscellaneous.md).

Constructo | Definição | Exemplo
--------- | ---------- | ------- 
**(?imnsx-imnsx)** | Define ou desabilita opções, como a diferenciação entre maiúsculas e minúsculas no meio de um padrão. Para obter mais informações, consulte [Opções de expressões regulares](options.md). | `\bA(?i)b\w+\b` corresponde a "ABA", "Able" em "ABA Able Act"
**(?#** _comment_**)** | Comentário embutido. O comentário é encerrado no primeiro caractere de fechar parênteses. | `\bA(?#` corresponde a palavras que começam com `A)\w+\b`
**#** [até o final da linha] | Comentário do modo X. O comentário começa em um # sem escape e continua até o final da linha. | `(?x)\bA\w+\b#` corresponde a palavras que começam com `A`

## <a name="see-also"></a>Consulte também




[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[Regex](xref:System.Text.RegularExpressions.Regex)

[Expressões regulares no .NET](regular-expressions.md)

[O modelo de objeto de expressão regular](object-model.md)

[Exemplos de expressões regulares](regex-examples.md)

[Baixar no formato Word (.docx)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
    
[Baixar no formato PDF (.pdf)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

