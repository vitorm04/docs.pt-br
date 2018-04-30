---
title: Linguagem de expressões regulares - referência rápida
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.RegularExpressionBuilder
helpviewer_keywords:
- regex cheat sheet
- parsing text with regular expressions, language elements
- searching with regular expressions, language elements
- pattern-matching with regular expressions, language elements
- regular expressions, language elements
- regular expressions [.NET Framework]
- cheat sheet
- .NET Framework regular expressions, language elements
ms.assetid: 930653a6-95d2-4697-9d5a-52d11bb6fd4c
caps.latest.revision: 56
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b8e43264619158ed9325875d9843e322e08872a4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="regular-expression-language---quick-reference"></a>Linguagem de expressões regulares - referência rápida
<a name="top"></a> Uma expressão regular é um padrão ao qual o mecanismo de expressões regulares tenta corresponder no texto de entrada. Um padrão consiste em um ou mais literais de caracteres, operadores ou constructos.  Para ver uma breve introdução, confira [Expressões regulares no .NET](../../../docs/standard/base-types/regular-expressions.md).  
  
 Cada seção desta referência rápida lista uma categoria específica de caracteres, operadores e constructos que você pode usar para definir expressões regulares:  
  
 [Escapes de caracteres](#character_escapes)  
 [Classes de caracteres](#character_classes)  
 [Âncoras](#atomic_zerowidth_assertions)  
 [Constructos de agrupamento](#grouping_constructs)  
 [Quantificadores](#quantifiers)  
 [Constructos de referência inversa](#backreference_constructs)  
 [Constructos de alternância](#alternation_constructs)  
 [Substituições](#substitutions)  
 [Opções de expressões regulares](#options)  
 [Constructos diversos](#miscellaneous_constructs)  
  
 Também fornecemos essas informações em dois formatos, que podem ser baixados e impressos para uma consulta simplificada:  
  
 [Baixar no formato Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Baixar no formato PDF (.pdf)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
<a name="character_escapes"></a>   
## <a name="character-escapes"></a>Escapes de caracteres  
 O caractere de barra invertida (\\) em uma expressão regular indica que o próximo caractere é um caractere especial (conforme mostrado na tabela a seguir) ou se deve ser interpretado literalmente. Para obter mais informações, consulte [Escapes de Caracteres](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md).  
  
|Caractere com escape|Descrição|Padrão|Correspondências|  
|-----------------------|-----------------|-------------|-------------|  
|`\a`|Corresponde a um caractere de campainha, \u0007.|`\a`|“\u0007” em “Error!” + "\u0007"|  
|`\b`|Em uma classe de caractere, corresponde a um backspace, \ u0008.|`[\b]{3,}`|"\b\b\b\b" em "\b\b\b\b"|  
|`\t`|Corresponde a uma tabulação, \u0009.|`(\w+)\t`|“item1\t”, “item2\t” em “item1\titem2\t”|  
|`\r`|Corresponde a um retorno de carro, \u000D. (`\r` não é equivalente ao caractere newline, `\n`.)|`\r\n(\w+)`|“\r\nThese” em “\r\nThese are\ntwo lines.”|  
|`\v`|Corresponde a uma tabulação vertical, \u000B.|`[\v]{2,}`|"\v\v\v" em "\v\v\v"|  
|`\f`|Corresponde a um avanço de página, \u000C.|`[\f]{2,}`|“\f\f\f” em “\f\f\f”|  
|`\n`|Corresponde a uma nova linha, \u000A.|`\r\n(\w+)`|“\r\nThese” em “\r\nThese are\ntwo lines.”|  
|`\e`|Corresponde a um escape, \u001B.|`\e`|“\x001B” em “\x001B”|  
|`\` *nnn*|Usa representação octal para especificar um caractere (*nnn* consiste em dois ou três dígitos).|`\w\040\w`|"a b", "c d" em<br /><br /> "a bc d"|  
|`\x` *nn*|Usa representação hexadecimal para especificar um caractere (*nn* consiste exatamente em dois dígitos).|`\w\x20\w`|"a b", "c d" em<br /><br /> "a bc d"|  
|`\c` *X*<br /><br /> `\c` *x*|Corresponde ao caractere de controle ASCII especificado por *X* ou *x*, em que *X* ou *x* é a letra do caractere de controle.|`\cC`|“\x0003” em “\x0003” (Ctrl-C)|  
|`\u` *nnnn*|Corresponde a um caractere Unicode usando representação hexadecimal (exatamente quatro dígitos, como representado por *nnnn*).|`\w\u0020\w`|"a b", "c d" em<br /><br /> "a bc d"|  
|`\`|Quando seguido por um caractere que não é reconhecido como um caractere de escape nesta e em outras tabelas deste tópico, corresponde a esse caractere. Por exemplo, `\*` é igual a `\x2A`, e `\.` é igual a `\x2E`. Isso permite que o mecanismo de expressões regulares remova ambiguidades de elementos da linguagem (como \* ou ?) e caracteres literais (representados por `\*` ou `\?`).|`\d+[\+-x\*]\d+`|"2+2" e "3\*9" em "(2+2) \* 3\*9"|  
  
 [Voltar ao início](#top)  
  
<a name="character_classes"></a>   
## <a name="character-classes"></a>Classes de caracteres  
 Uma classe de caractere corresponde a qualquer um dos conjuntos de caracteres. As classes de caracteres incluem os elementos de linguagem listados na tabela a seguir. Para saber mais, confira [Classes de caracteres](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
|Classe de caractere|Descrição|Padrão|Correspondências|  
|---------------------|-----------------|-------------|-------------|  
|`[` *character_group* `]`|Corresponde a qualquer caractere único em *character_group*. Por padrão, a correspondência diferencia maiúsculas de minúsculas.|`[ae]`|“a” em “gray”<br /><br /> “a”, “e” em “lane”|  
|`[^` *character_group* `]`|Negação: corresponde a qualquer caractere único que não esteja em *character_group*. Por padrão, caracteres em *character_group* diferenciam maiúsculas de minúsculas.|`[^aei]`|“r”, “g”, “n” em “reign”|  
|`[` *first* `-` *last* `]`|Intervalo de caracteres: corresponde a qualquer caractere único no intervalo entre *first* e *last*.|`[A-Z]`|“A”, “B” em “AB123”|  
|`.`|Curinga: corresponde a qualquer caractere único, exceto \n.<br /><br /> Para corresponder a um caractere literal de ponto (. ou `\u002E`), você deve precedê-lo com o caractere de escape (`\.`).|`a.e`|"ave" em "nave"<br /><br /> "ate" em "water"|  
|`\p{` *name* `}`|Corresponde a qualquer caractere único na categoria geral Unicode ou no bloco nomeado especificado por *name*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|"C", "L" em "City Lights"<br /><br /> "Д", "Ж" em "ДЖem"|  
|`\P{` *name* `}`|Corresponde a qualquer caractere único que não esteja na categoria geral Unicode ou no bloco nomeado especificado por *name*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|"i", "t", "y" em "City"<br /><br /> "e", "m" em "ДЖem"|  
|`\w`|Corresponde a qualquer caractere de palavra.|`\w`|“I”, “D”, “A”, “1”, “3” em “ID A1.3”|  
|`\W`|Corresponde a qualquer caractere que não seja uma palavra.|`\W`|“ ”, “.” em “ID A1.3”|  
|`\s`|Corresponde a qualquer caractere de espaço em branco.|`\w\s`|“D “ em “ID A1.3”|  
|`\S`|Corresponde a qualquer caractere que não seja um caractere de espaço em branco.|`\s\S`|" _" em "int \__ctr"|  
|`\d`|Corresponde a qualquer dígito decimal.|`\d`|“4” em “4 = IV”|  
|`\D`|Corresponde a qualquer caractere que não seja um dígito decimal.|`\D`|“ ”, “=”, “ ”, “I”, “V” em “4 = IV”|  
  
 [Voltar ao início](#top)  
  
<a name="atomic_zerowidth_assertions"></a>   
## <a name="anchors"></a>Âncoras  
 Âncoras ou asserções atômicas de largura zero, fazem com que uma correspondência tenha êxito ou falha dependendo da posição atual na cadeia de caracteres, mas não fazem com que o mecanismo avance na cadeia de caracteres ou consuma caracteres. Os metacaracteres listados na tabela a seguir são âncoras. Para saber mais, confira [Âncoras](../../../docs/standard/base-types/anchors-in-regular-expressions.md).  
  
|Asserção|Descrição|Padrão|Correspondências|  
|---------------|-----------------|-------------|-------------|  
|`^`|A correspondência deve começar no início da cadeia de caracteres ou da linha.|`^\d{3}`|"901" em<br /><br /> "901-333-"|  
|`$`|A correspondência deve ocorrer no final da cadeia de caracteres ou antes de `\n` no final da linha ou da cadeia de caracteres.|`-\d{3}$`|"-333" em<br /><br /> "-901-333"|  
|`\A`|A correspondência deve ocorrer no início da cadeia de caracteres.|`\A\d{3}`|"901" em<br /><br /> "901-333-"|  
|`\Z`|A correspondência deve ocorrer no final da cadeia de caracteres ou antes de `\n` no final da cadeia de caracteres.|`-\d{3}\Z`|"-333" em<br /><br /> "-901-333"|  
|`\z`|A correspondência deve ocorrer no final da cadeia de caracteres.|`-\d{3}\z`|"-333" em<br /><br /> "-901-333"|  
|`\G`|A correspondência deve ocorrer no ponto em que a correspondência anterior foi encerrada.|`\G\(\d\)`|"(1)", "(3)", "(5)" in "(1)(3)(5)[7](9\)"|  
|`\b`|A correspondência deve ocorrer em um limite entre um caractere `\w` (alfanumérico) e um caractere `\W` (não alfanumérico).|`\b\w+\s\w+\b`|“them theme”, “them them” em “them theme them them”|  
|`\B`|A correspondência não deve ocorrer em um limite `\b`.|`\Bend\w*\b`|“ends”, “ender” em “end sends endure lender”|  
  
 [Voltar ao início](#top)  
  
<a name="grouping_constructs"></a>   
## <a name="grouping-constructs"></a>Agrupando construtores  
 Os constructos de agrupamento delineiam subexpressões de uma expressão regular e, em geral, capturam subcadeias de caracteres de uma cadeia de caracteres de entrada. Os constructos de agrupamento incluem os elementos de linguagem listados na tabela a seguir. Para saber mais, confira [Constructos de agrupamento](grouping-constructs-in-regular-expressions.md).  
  
|Constructo de agrupamento|Descrição|Padrão|Correspondências|  
|------------------------|-----------------|-------------|-------------|  
|`(` *subexpression* `)`|Captura a subexpressão correspondente e atribui a ela um número ordinal com base um.|`(\w)\1`|“ee” em “deep”|  
|`(?<` *nome* `>` *subexpressão* `)`|Captura a subexpressão correspondente em um grupo nomeado.|`(?<double>\w)\k<double>`|“ee” em “deep”|  
|`(?<` *nome1* `-` *nome2* `>` *subexpressão* `)`|Especifica uma definição de grupo de balanceamento. Para saber mais, confira a seção "Definição de grupo de balanceamento" em [Constructos de agrupamento](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|“((1-3)\*(3-1))” em “3+2^((1-3)\*(3-1))”|  
|`(?:` *subexpression* `)`|Define um grupo de não captura.|`Write(?:Line)?`|"WriteLine" em "Console.WriteLine()"<br /><br /> "Write" em "Console.Write(value)"|  
|`(?imnsx-imnsx:` *subexpression* `)`|Aplica ou desabilita as opções especificadas em *subexpressão*. Para obter mais informações, consulte [Opções de expressões regulares](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|“A12xl”, “A12XL” em “A12xl A12XL a12xl”|  
|`(?=` *subexpression* `)`|Asserções lookahead positivas de largura zero.|`\w+(?=\.)`|“is”, “ran” e “out” em “He is. The dog ran. The sun is out.”|  
|`(?!` *subexpression* `)`|Asserções lookahead negativas de largura zero.|`\b(?!un)\w+\b`|“sure”, “used” em “unsure sure unity used”|  
|`(?<=` *subexpression* `)`|Asserção lookbehind positiva de largura zero.|`(?<=19)\d{2}\b`|“99”, “50”, “05” em “1851 1999 1950 1905 2003”|  
|`(?<!` *subexpression* `)`|Asserção lookbehind negativa de largura zero.|`(?<!19)\d{2}\b`|“51”, “03” em “1851 1999 1950 1905 2003”|  
|`(?>` *subexpression* `)`|Subexpressão sem retrocesso (ou “Greedy”).|`[13579](?>A+B+)`|“1ABB”, “3ABB” e “5AB” em “1ABB 3ABBC 5AB 5AC”|  
  
 [Voltar ao início](#top)  
  
<a name="quantifiers"></a>   
## <a name="quantifiers"></a>Quantificadores  
 Um quantificador especifica quantas instâncias do elemento anterior (que pode ser um caractere, um grupo ou uma classe de caracteres) devem estar presentes na cadeia de caracteres de entrada para que uma correspondência ocorra. Os quantificadores incluem os elementos de linguagem listados na tabela a seguir. Para saber mais, confira [Quantificadores](quantifiers-in-regular-expressions.md).  
  
|Quantificador|Descrição|Padrão|Correspondências|  
|----------------|-----------------|-------------|-------------|  
|`*`|Corresponde ao elemento anterior zero ou mais vezes.|`\d*\.\d`|“.0”, “19.9”, “219.9”|  
|`+`|Corresponde ao elemento anterior uma ou mais vezes.|`"be+"`|“bee” em “been”, “be” em “bent”|  
|`?`|Corresponde ao elemento anterior zero vezes ou uma vez.|`"rai?n"`|“ran”, “rain”|  
|`{` *n* `}`|Corresponde ao elemento anterior exatamente *n* vezes.|`",\d{3}"`|“.043” em “1.043.6”, “.876”, “.543” e “.210” em “9.876.543.210”|  
|`{` *n* `,}`|Corresponde ao elemento anterior pelo menos *n* vezes.|`"\d{2,}"`|“166”, “29”, “1930”|  
|`{` *n* `,` *m* `}`|Corresponde ao elemento anterior pelo menos *n* vezes, mas não mais do que *m* vezes.|`"\d{3,5}"`|"166", "17668"<br /><br /> "19302" em "193024"|  
|`*?`|Corresponde ao elemento anterior zero vezes ou mais, mas o menor número de vezes possível.|`\d*?\.\d`|“.0”, “19.9”, “219.9”|  
|`+?`|Corresponde ao elemento anterior uma ou mais vezes, mas o menor número de vezes possível.|`"be+?"`|"be" em "been", "be" em "bent"|  
|`??`|Corresponde ao elemento anterior zero vezes ou uma vez, mas o menor número de vezes possível.|`"rai??n"`|“ran”, “rain”|  
|`{` *n* `}?`|Corresponde ao elemento anterior exatamente *n* vezes.|`",\d{3}?"`|“.043” em “1.043.6”, “.876”, “.543” e “.210” em “9.876.543.210”|  
|`{` *n* `,}?`|Corresponde ao elemento anterior pelo menos *n* vezes, mas o menor número de vezes possível.|`"\d{2,}?"`|“166”, “29”, “1930”|  
|`{` *n* `,` *m* `}?`|Corresponde ao elemento anterior entre *n* e *m* vezes, mas o menor número de vezes possível.|`"\d{3,5}?"`|"166", "17668"<br /><br /> "193", "024" em "193024"|  
  
 [Voltar ao início](#top)  
  
<a name="backreference_constructs"></a>   
## <a name="backreference-constructs"></a>Construtores de referência inversa  
 Um referência inversa permite que uma subexpressão correspondida anteriormente seja identificada posteriormente na mesma expressão regular. A tabela a seguir lista os constructos de referência inversa tem suporte nas expressões regulares do .NET. Para saber mais, confira [Constructos de referência inversa](backreference-constructs-in-regular-expressions.md).  
  
|Constructo de referência inversa|Descrição|Padrão|Correspondências|  
|-----------------------------|-----------------|-------------|-------------|  
|`\` *number*|Referência inversa. Corresponde ao valor de uma subexpressão numerada.|`(\w)\1`|“ee” em “seek”|  
|`\k<` *name* `>`|Referência inversa nomeada. Corresponde ao valor de uma expressão nomeada.|`(?<char>\w)\k<char>`|“ee” em “seek”|  
  
 [Voltar ao início](#top)  
  
<a name="alternation_constructs"></a>   
## <a name="alternation-constructs"></a>Construtores de alternância  
 Os constructos de alternância modificam uma expressão regular para habilitar uma correspondência do tipo um/ou outro. Esses constructos incluem os elementos de linguagem listados na tabela a seguir. Para saber mais, confira [Constructos de alternância](alternation-constructs-in-regular-expressions.md).  
  
|Constructo de alternância|Descrição|Padrão|Correspondências|  
|---------------------------|-----------------|-------------|-------------|  
|<code>&#124;</code>|Corresponde a qualquer elemento separado pelo caractere de barra vertical (&#124;).|<code>th(e&#124;is&#124;at)</code>|“the”, “this” em “this is the day. "|  
|`(?(` *expression* `)` *yes* <code>&#124;</code> *no* `)`|Corresponde a *yes* se o padrão de expressão regular designado por *expression* for correspondente. Do contrário, corresponde à parte *no* opcional. *expression* é interpretado como uma asserção de largura zero.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|“A10”, “910” em “A10 C103 910”|  
|`(?(` *name* `)` *yes* <code>&#124;</code> *no* `)`|Corresponde a *yes* se *name*, um grupo de captura nomeado ou numerado, apresenta uma correspondência. Do contrário, corresponde a *no* opcional.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|Dogs.jpg, “Yiska playing.jpg” em “Dogs.jpg “Yiska playing.jpg””|  
  
 [Voltar ao início](#top)  
  
<a name="substitutions"></a>   
## <a name="substitutions"></a>Substituições  
 As substituições são elementos de linguagem de expressões regulares com suporte em padrões de substituição. Para saber mais, confira [Substituições](substitutions-in-regular-expressions.md). Os metacaracteres listados na tabela a seguir são asserções atômicas de largura zero.  
  
|Caractere|Descrição|Padrão|Padrão de substituição|Cadeia de caracteres de entrada|Cadeia de caracteres de resultado|  
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|  
|`$` *number*|Substitui a subcadeia de caracteres correspondida pelo grupo *number*.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|“one two”|“two one”|  
|`${` *name* `}`|Substitui a subcadeia de caracteres correspondida pelo grupo chamado *name*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|“one two”|“two one”|  
|`$$`|Substitui um literal “$”.|`\b(\d+)\s?USD`|`$$$1`|“103 USD”|"$103"|  
|`$&`|Substitui uma cópia da correspondência inteira.|`\$?\d*\.?\d+`|`**$&**`|"$1.30"|"\*\*$1.30\*\*"|  
|<code>$`</code>|Substitui todo o texto da cadeia de caracteres de entrada antes da correspondência.|`B+`|<code>$`</code>|“AABBCC”|“AAAACC”|  
|`$'`|Substitui todo o texto da cadeia de caracteres de entrada após a correspondência.|`B+`|`$'`|“AABBCC”|“AACCCC”|  
|`$+`|Substitui o último grupo que foi capturado.|`B+(C+)`|`$+`|“AABBCCDD”|AACCDD|  
|`$_`|Substitui a cadeia de caracteres de entrada inteira.|`B+`|`$_`|“AABBCC”|“AAAABBCCCC”|  
  
 [Voltar ao início](#top)  
  
<a name="options"></a>   
## <a name="regular-expression-options"></a>Opções de expressões regulares  
 Você pode especificar opções que controlam como o mecanismo de expressões regulares interpreta uma expressão regular padrão. Muitas dessas opções podem ser especificadas de maneira embutida (no padrão da expressão regular) ou como uma ou mais constantes <xref:System.Text.RegularExpressions.RegexOptions>. Essa referência rápida lista somente as opções embutidas. Para obter mais informações sobre opções embutidas e <xref:System.Text.RegularExpressions.RegexOptions>, consulte o artigo [Opções de expressões regulares](regular-expression-options.md).  
  
 É possível especificar uma opção embutida de duas formas:  
  
-   Usando o [constructo diverso](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, em que um sinal de subtração (-) antes de uma opção ou um conjunto de opções desativa essas opções. Por exemplo, `(?i-mn)` ativa a correspondência sem diferenciação de maiúsculas e minúsculas (`i`), desativa o modo de várias linhas (`m`) e desativa capturas de grupo sem nome (`n`). A opção se aplica ao padrão de expressão regular no ponto em que a opção é definida e entra em vigor no final do padrão ou no ponto em que outro constructo inverte a opção.  
  
-   Usando o [construtor de agrupamento](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*subexpression*`)`, que define opções somente para o grupo especificado.  
  
 O mecanismo de expressões regulares do .NET dá suporte às opções embutidas a seguir.  
  
|Opção|Descrição|Padrão|Correspondências|  
|------------|-----------------|-------------|-------------|  
|`i`|Use correspondência sem diferenciação de maiúsculas e minúsculas.|`\b(?i)a(?-i)a\w+\b`|“aardvark”, “aaaAuto” em “aardvark AAAuto aaaAuto Adam breakfast”|  
|`m`|Use o modo multilinha. `^` e `$` correspondem ao início e ao fim de uma linha, em vez do início e fim de uma cadeia de caracteres.|Para um exemplo, consulte a seção “Modo multilinha” em [Opções de expressões regulares](regular-expression-options.md).||  
|`n`|Não capture grupos sem nome.|Para ver um exemplo, consulte a seção “Apenas capturas explícitas” em [Opções de expressões regulares](regular-expression-options.md).||  
|`s`|Use o modo de linha única.|Para ver um exemplo, consulte a seção “Modo de linha única” em [Opções de expressões regulares](regular-expression-options.md).||  
|`x`|Ignore espaços em branco sem escape no padrão da expressão regular.|`\b(?x) \d+ \s \w+`|“1 aardvark”, “2 cats” em “1 aardvark 2 cats IV centurions”|  
  
 [Voltar ao início](#top)  
  
<a name="miscellaneous_constructs"></a>   
## <a name="miscellaneous-constructs"></a>Diversos construtores  
 Os constructos diversos modificam um expressão regular padrão ou fornecem informações sobre ela. A tabela a seguir lista os constructos diversos que têm suporte no .NET. Para saber mais, confira [Constructos diversos](miscellaneous-constructs-in-regular-expressions.md).  
  
|Constructo|Definição|Exemplo|  
|---------------|----------------|-------------|  
|`(?imnsx-imnsx)`|Define ou desabilita opções como não diferenciação de maiúsculas e minúsculas no meio de um padrão. Para saber mais, confira [Opções de expressão regular](regular-expression-options.md).|`\bA(?i)b\w+\b` corresponde a "ABA", "Able" em "ABA Able Act"|  
|`(?#` *comment* `)`|Comentário embutido. O comentário é encerrado no primeiro caractere de fechar parênteses.|`\bA(?#Matches words starting with A)\w+\b`|  
|`#` [até o final da linha]|Comentário do modo X. O comentário começa em um `#` sem escape e continua até o final da linha.|`(?x)\bA\w+\b#Matches words starting with A`|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex>  
 [Expressões regulares](regular-expressions.md)  
 [Classes de expressões regulares](the-regular-expression-object-model.md)  
 [Exemplos de expressões regulares](regular-expression-examples.md)  
 [Expressões regulares - referência rápida (fazer download no formato Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Expressões regulares - referência rápida (fazer download no formato PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
