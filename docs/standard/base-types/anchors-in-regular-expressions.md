---
title: "Âncoras em expressões regulares"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- atomic zero-width assertions
- regular expressions, anchors
- regular expressions, atomic zero-width assertions
- anchors, in regular expressions
- metacharacters, atomic zero-width assertions
- metacharacters, anchors
- .NET Framework regular expressions, anchors
- .NET Framework regular expressions, atomic zero-width assertions
ms.assetid: 336391f6-2614-499b-8b1b-07a6837108a7
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 453776c97ec0531cea94ecf44c31216cf5b17a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="anchors-in-regular-expressions"></a>Âncoras em expressões regulares
<a name="top"></a>Âncoras ou asserções atômicas de largura zero, especificam uma posição na cadeia de caracteres em que uma correspondência deve ocorrer. Quando você usa uma âncora na sua expressão de pesquisa, o mecanismo de expressões regulares não avança pela cadeia de caracteres ou consome caracteres, ele procura uma correspondência apenas na posição especificada. Por exemplo, `^` Especifica que a correspondência deve começar do início de uma linha ou uma cadeia de caracteres. Portanto, a expressão regular `^http:` corresponde a "http:" apenas quando ele ocorre no início de uma linha. A tabela a seguir lista as âncoras com suporte pelas expressões regulares no .NET.  
  
|Âncora|Descrição|  
|------------|-----------------|  
|`^`|A correspondência deve ocorrer no início da cadeia de caracteres ou da linha. Para obter mais informações, consulte [início da cadeia de caracteres ou linha](#Start).|  
|`$`|A correspondência deve ocorrer no final da cadeia de caracteres ou da linha ou antes de `\n` no final da cadeia de caracteres ou da linha. Para obter mais informações, consulte [final da cadeia de caracteres ou linha](#End).|  
|`\A`|A correspondência deve ocorrer no início da cadeia de caracteres somente (sem suporte a várias linhas). Para obter mais informações, consulte [iniciar somente de cadeia de caracteres](#StartOnly).|  
|`\Z`|A correspondência deve ocorrer no final da cadeia de caracteres ou antes de `\n` no final da cadeia de caracteres. Para obter mais informações, consulte [final da cadeia de caracteres ou antes terminando nova linha](#EndOrNOnly).|  
|`\z`|A correspondência deve ocorrer apenas no final da cadeia de caracteres. Para obter mais informações, consulte [final da cadeia de caracteres somente](#EndOnly).|  
|`\G`|A correspondência deve começar na posição em que a correspondência anterior foi encerrada. Para obter mais informações, consulte [correspondências de contígua](#Contiguous).|  
|`\b`|A correspondência deve ocorrer em um limite de palavra. Para obter mais informações, consulte [limite de palavra](#WordBoundary).|  
|`\B`|A correspondência não deve ocorrer em um limite de palavra. Para obter mais informações, consulte [limites de palavras não](#NonwordBoundary).|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>Início da Cadeia de Caracteres ou Linha: ^  
 O `^` âncora Especifica que o seguinte padrão deve começar na posição do primeiro caractere da cadeia de caracteres. Se você usar `^` com o <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opção (consulte [opções de expressão Regular](../../../docs/standard/base-types/regular-expression-options.md)), a correspondência deve ocorrer no início de cada linha.  
  
 O exemplo a seguir usa o `^` âncora em uma expressão regular que extrai informações sobre os anos durante o qual alguns basquete professional existia. O exemplo chama duas sobrecargas do método <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>:  
  
-   A chamada para o <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> sobrecarga localiza apenas a primeira subcadeia de caracteres na cadeia de caracteres de entrada que corresponde ao padrão de expressão regular.  
  
-   A chamada para o <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> sobrecarga com a `options` parâmetro definido como <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> localiza todas as cinco subcadeias de caracteres.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 O padrão de expressão regular `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` é definido conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`^`|Começa a correspondência no início da cadeia de caracteres de entrada (ou o início da linha se o método for chamado com a opção <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>).|  
|`((\w+(\s?)){2,}`|Corresponde a um ou mais caracteres de palavra seguidos por zero ou um espaço exatamente duas vezes. Este é o primeiro grupo de captura. Essa expressão também define um segundo e um terceiro grupos de captura: o segundo consiste na palavra capturada e o terceiro consiste nos espaços capturados.|  
|`,\s`|Corresponde a uma vírgula seguida por um caractere de espaço em branco.|  
|`(\w+\s\w+)`|Corresponde a um ou mais caracteres de palavra seguidos por um espaço, seguido por um ou mais caracteres de palavra. Este é o quarto grupo de captura.|  
|`,`|Corresponde a uma vírgula.|  
|`\s\d{4}`|Corresponde a um espaço seguido por quatro dígitos decimais.|  
|(-`(\d{4}&#124;present))?`|Corresponde a zero ou uma ocorrência de um hífen seguido por quatro dígitos decimais ou a cadeia de caracteres "present". Este é o sexto grupo de captura. Ele também inclui um sétimo grupo de captura.|  
|`,?`|Corresponde a zero ou uma ocorrência de uma vírgula.|  
|`(\s\d{4}(-(\d{4}&#124;present))?,?)+`|Corresponde a uma ou mais ocorrências do seguinte: um espaço, quatro dígitos decimais, zero ou uma ocorrência de um hífen seguido por quatro dígitos decimais ou a cadeia de caracteres "present" e zero ou uma vírgula. Este é o quinto grupo de captura.|  
  
 [Voltar ao início](#top)  
  
<a name="End"></a>   
## <a name="end-of-string-or-line-"></a>Final da Cadeia de Caracteres ou da Linha: $  
 O `$` âncora Especifica que o padrão anterior deve ocorrer no final da cadeia de caracteres de entrada ou antes de `\n` no final da cadeia de caracteres de entrada.  
  
 Se você usar `$` com o <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opção, a correspondência também pode ocorrer no final de uma linha. Observe que `$` corresponde `\n` , mas não coincide com `\r\n` (a combinação de caracteres de nova linha e de retorno de carro ou CR/LF). De acordo com a combinação de caracteres CR/LF, incluir `\r?$` no padrão de expressão regular.  
  
 O exemplo a seguir adiciona o `$` âncora para o padrão de expressão regular usada no exemplo de [início da cadeia de caracteres ou linha](#Start) seção. Quando usado com a cadeia de entrada original, que inclui cinco linhas de texto, o <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> método é não é possível localizar uma correspondência, pois o final da primeira linha não corresponde a `$` padrão. Quando a cadeia de caracteres de entrada original é dividida em uma matriz de cadeia de caracteres, o método <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> obtém sucesso na correspondência de cada uma das cinco linhas. Quando o <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> método for chamado com o `options` parâmetro definido como <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, nenhuma correspondência for encontrada porque o padrão de expressão regular não leva em consideração para o elemento de retorno de carro (\u+000D). No entanto, quando o padrão de expressão regular é modificado, substituindo `$` com `\r?$`, chamar o <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> método com o `options` parâmetro definido como <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> novamente encontrar cinco correspondências.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [Voltar ao início](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>Apenas Início da Cadeia de Caracteres: \A  
 O `\A` âncora Especifica que uma correspondência deve ocorrer no início da cadeia de caracteres de entrada. Ele é idêntico de `^` de ancoragem, exceto que `\A` ignora o <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opção. Portanto, ela pode corresponder apenas ao início da primeira linha em uma cadeia de caracteres de entrada multilinhas.  
  
 O exemplo a seguir é semelhante aos exemplos para o `^` e `$` âncoras. Ele usa o `\A` âncora em uma expressão regular que extrai informações sobre os anos durante o qual alguns basquete professional existia. A cadeia de caracteres de entrada inclui cinco linhas. A chamada para o <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> método localiza apenas a primeira subcadeia de caracteres na cadeia de caracteres de entrada que corresponde ao padrão de expressão regular. Como o exemplo mostra, a opção <xref:System.Text.RegularExpressions.RegexOptions.Multiline> não tem efeito.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [Voltar ao início](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>Final da Cadeia de Caracteres ou Antes de Terminar Nova Linha: \ Z  
 O `\Z` âncora Especifica que uma correspondência deve ocorrer no final da cadeia de caracteres de entrada ou antes de `\n` no final da cadeia de caracteres de entrada. Ele é idêntico de `$` de ancoragem, exceto que `\Z` ignora o <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opção. Portanto, em uma cadeia de caracteres de várias linhas, ele só pode corresponder a final da última linha ou a última linha antes de `\n`.  
  
 Observe que `\Z` corresponde `\n` , mas não coincide com `\r\n` (a combinação de caracteres CR/LF). Para combinar CR/LF, incluir `\r?\Z` no padrão de expressão regular.  
  
 O exemplo a seguir usa o `\Z` âncora em uma expressão regular que é semelhante ao exemplo do [início da cadeia de caracteres ou linha](#Start) seção, que extrai informações sobre os anos durante os quais alguns bola professional as equipes existiam. A subexpressão `\r?\Z` na expressão regular `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` corresponde ao final de uma cadeia de caracteres e também corresponda uma cadeia de caracteres que termina com `\n` ou `\r\n`. Como resultado, cada elemento da matriz corresponde ao padrão da expressão regular.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [Voltar ao início](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>Apenas Final da Cadeia de Caracteres: \ z  
 O `\z` âncora Especifica que uma correspondência deve ocorrer no final da cadeia de caracteres de entrada. Como o `$` elemento de linguagem `\z` ignora o <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opção. Ao contrário de `\Z` elemento de linguagem, `\z` não coincide com um `\n` caractere no final de uma cadeia de caracteres. Portanto, ele pode corresponder somente à última linha da cadeia de caracteres de entrada.  
  
 O exemplo a seguir usa o `\z` âncora em uma expressão regular, caso contrário é idêntica ao exemplo na seção anterior, que extrai informações sobre os anos durante o qual alguns basquete professional existia. O exemplo tenta corresponder cada um dos cinco elementos em uma matriz de cadeia de caracteres com um padrão de expressão regular `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Duas das cadeias de caracteres terminam com os caracteres de alimentação de linha e retorno de carro, uma termina com um caractere de alimentação de linha e duas terminam sem um caractere de retorno de carro nem um caractere de alimentação de linha. Como a saída mostra, apenas as cadeias de caracteres sem um caractere de retorno de carro ou de alimentação de linha correspondem ao padrão.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [Voltar ao início](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>Correspondências Contíguas: \ G  
 O `\G` âncora Especifica que uma correspondência deve ocorrer no ponto onde a correspondência anterior terminou. Quando você usa essa âncora com o <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> método, ele garante que todas as correspondências são contíguas.  
  
 O exemplo a seguir usa uma expressão regular para extrair os nomes de espécies de roedores de uma cadeia de caracteres delimitada por vírgulas.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 A expressão regular `\G(\w+\s?\w*),?` é interpretada conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\G`|Começa onde a última correspondência terminou.|  
|`\w+`|Fazer a correspondência a um ou mais caracteres de palavra.|  
|`\s?`|Corresponde a zero ou um espaço.|  
|`\w*`|Corresponder a zero ou mais caracteres de palavra.|  
|`(\w+\s?\w*)`|Corresponde a um ou mais caracteres de palavra seguidos por zero ou um espaço, seguido por zero ou mais caracteres de palavra. Este é o primeiro grupo de captura.|  
|`,?`|Corresponde a zero ou uma ocorrência de um caractere de vírgula literal.|  
  
 [Voltar ao início](#top)  
  
<a name="WordBoundary"></a>   
## <a name="word-boundary-b"></a>Limite de Palavra: \b  
 O `\b` âncora Especifica que a correspondência deve ocorrer em um limite entre um caractere de palavra (o `\w` elemento de linguagem) e um caractere de palavra (o `\W` elemento de linguagem). Os caracteres de palavra consistem em caracteres alfanuméricos e sublinhados. Um caractere não pertencente a palavras é qualquer caractere que não seja alfanumérico ou um sublinhado. (Para obter mais informações, consulte [Classes de caracteres](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) A correspondência também pode ocorrer em um limite de palavra no início ou no final da cadeia de caracteres.  
  
 O `\b` âncora é usada com frequência para garantir que uma subexpressão corresponda a uma palavra inteira em vez de apenas o início ou término de uma palavra. A expressão regular `\bare\w*\b` no exemplo a seguir ilustra esse uso. Ela corresponde a qualquer palavra que comece com a subcadeia de caracteres "are". A saída do exemplo também ilustra que `\b` coincide com o início e fim da cadeia de caracteres de entrada.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 O padrão da expressão regular é interpretado conforme a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Começar a correspondência em um limite de palavra.|  
|`are`|Corresponde à subcadeia de caracteres “are”.|  
|`\w*`|Corresponder a zero ou mais caracteres de palavra.|  
|`\b`|Termina a correspondência em um limite de palavra.|  
  
 [Voltar ao início](#top)  
  
<a name="NonwordBoundary"></a>   
## <a name="non-word-boundary-b"></a>Limite de Não Palavra: \B  
 O `\B` âncora Especifica que a correspondência não deve ocorrer em um limite de palavra. É o oposto do `\b` âncora.  
  
 O exemplo a seguir usa o `\B` âncora para localizar as ocorrências da subcadeia de caracteres "ou" em uma palavra. O padrão de expressão regular `\Bqu\w+` corresponde a uma subcadeia de caracteres que começa com um "qu" que não inicia uma palavra e que continua até o final da palavra.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 O padrão da expressão regular é interpretado conforme a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\B`|Não começa a correspondência em um limite de palavra.|  
|`qu`|Corresponde à subcadeia de caracteres “qu”.|  
|`\w+`|Fazer a correspondência a um ou mais caracteres de palavra.|  
  
## <a name="see-also"></a>Consulte também  
 [Linguagem de expressão regular – referência rápida](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Opções de expressões regulares](../../../docs/standard/base-types/regular-expression-options.md)
