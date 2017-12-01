---
title: "Quantificadores em expressões regulares"
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
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab06aa0c331c8cbd4c8986cced29334046f30264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="quantifiers-in-regular-expressions"></a>Quantificadores em expressões regulares
Os quantificadores especificam quantas instâncias de um caractere, grupo ou classe de caracteres devem estar presentes na entrada para encontrar uma correspondência.  A tabela a seguir lista os quantificadores tem suporte no .NET.  
  
|Quantificador Greedy|Quantificador lento|Descrição|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Corresponder a zero ou mais vezes.|  
|`+`|`+?`|Corresponder a um ou mais vezes.|  
|`?`|`??`|Corresponder a zero ou uma vez.|  
|`{` *n* `}`|`{` *n* `}?`|Correspondência exata  *n*  vezes.|  
|`{` *n* `,}`|`{` *n* `,}?`|Corresponde a pelo menos  *n*  vezes.|  
|`{` *n*  `,` *m*`}`|`{` *n*  `,` *m*`}?`|Corresponde do  *n*  para *m* vezes.|  
  
 As quantidades `n` e `m` são constantes de inteiro. Normalmente, os quantificadores são Greedy; eles fazem com que o mecanismo de expressões regulares corresponda a quantas ocorrências de padrões determinados forem possíveis. Acrescentar o caractere `?` a um quantificador o torna lento; faz com que o mecanismo de expressões regulares corresponda ao mínimo de ocorrências possíveis. Para obter uma descrição completa da diferença entre quantificadores Greedy e lentos, consulte a seção [Quantificadores Greedy e lentos](#Greedy) mais adiante neste tópico.  
  
> [!IMPORTANT]
>  O aninhamento de quantificadores (por exemplo, como o padrão de expressão regular `(a*)*` faz) pode aumentar o número de comparações que o mecanismo de expressões regulares deve executar, como uma função exponencial do número de caracteres na cadeia de caracteres de entrada. Para obter mais informações sobre esse comportamento e suas soluções alternativas, consulte [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Quantificadores em expressões regulares  
 As seções a seguir listam os quantificadores com suporte nas expressões regulares no .NET.  
  
> [!NOTE]
>  Se o *, +,?, {, e} caracteres forem encontrados em um padrão de expressão regular, o mecanismo de expressão regular interpreta como quantificadores ou parte das construções de quantificador, a menos que estão incluídos em um [caractere classe](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Para interpretá-los como caracteres literais fora de uma classe de caracteres, você precisa fazer o escape, antecedendo-os com uma barra invertida. Por exemplo, a cadeia de caracteres `\*` em uma expressão regular padrão é interpretado como um asterisco literal ("\*") caracteres.  
  
### <a name="match-zero-or-more-times-"></a>Corresponder a zero ou mais vezes: *  
 O quantificador `*` corresponde ao elemento anterior zero ou mais vezes. É equivalente a `{0,}` quantificador. `*`é um quantificador greedy cujo equivalente lento é `*?`.  
  
 O exemplo a seguir ilustra essa expressão regular. Dentre os nove dígitos na cadeia de caracteres de entrada, cinco correspondem ao padrão e quatro (`95`, `929`, `9129` e `9919`) não.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`91*`|Corresponder a “9” seguido por zero ou mais caracteres “1”.|  
|`9*`|Corresponder a zero ou mais caracteres “9”.|  
|`\b`|Terminar em um limite de palavra.|  
  
### <a name="match-one-or-more-times-"></a>Corresponder a um ou mais vezes: +  
 O `+` quantificador coincide com o elemento anterior uma ou mais vezes. É equivalente a `{1,}`. `+`é um quantificador greedy cujo equivalente lento é `+?`.  
  
 Por exemplo, a expressão regular `\ban+\w*?\b` tenta corresponder a palavras inteiras que começam com a letra `a` seguidas por uma ou mais instâncias da letra `n`. O exemplo a seguir ilustra essa expressão regular. A expressão regular corresponde às palavras `an`, `annual`, `announcement` e `antique`, e não correspondem corretamente a `autumn` e `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`an+`|Corresponder a um “a” seguido por um ou mais caracteres “n”.|  
|`\w*?`|Corresponder a um caractere de palavra zero ou mais vezes, mas o menor número de vezes possível.|  
|`\b`|Terminar em um limite de palavra.|  
  
### <a name="match-zero-or-one-time-"></a>Corresponder a zero ou uma vez: ?  
 O `?` quantificador corresponde à hora de elemento zero ou anterior. É equivalente a `{0,1}`. `?`é um quantificador greedy cujo equivalente lento é `??`.  
  
 Por exemplo, a expressão regular `\ban?\b` tenta corresponder a palavras inteiras que começam com a letra `a` seguidas por zero ou uma instância da letra `n`. Em outras palavras, ele tenta corresponder às palavras `a` e `an`. O exemplo a seguir ilustra essa expressão regular.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`an?`|Corresponder a um “a” seguido por zero ou um caractere “n”.|  
|`\b`|Terminar em um limite de palavra.|  
  
### <a name="match-exactly-n-times-n"></a>Corresponder exatamente a n vezes: {n}  
 O `{`  *n*  `}` quantificador coincide com o elemento anterior exatamente  *n*  vezes, onde  *n* é qualquer inteiro. `{`*n*`}`é um quantificador greedy cujo equivalente lento é `{`  *n*  `}?`.  
  
 Por exemplo, a expressão regular `\b\d+\,\d{3}\b` tenta corresponder a um limite de palavra seguido por um ou mais dígitos decimais seguidos por três dígitos decimais seguidos por um limite de palavra. O exemplo a seguir ilustra essa expressão regular.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`\d+`|Corresponde a um ou mais dígitos decimais.|  
|`\,`|Corresponder a um caractere de vírgula.|  
|`\d{3}`|Corresponder a três dígitos decimais.|  
|`\b`|Terminar em um limite de palavra.|  
  
### <a name="match-at-least-n-times-n"></a>Corresponder a pelo menos n vezes: {n,}  
 O `{`  *n*  `,}` quantificador coincide com o elemento anterior pelo menos  *n*  vezes, onde  *n* é qualquer inteiro. `{`*n*`,}`é um quantificador greedy cujo equivalente lento é `{`  *n*  `}?`.  
  
 Por exemplo, a expressão regular `\b\d{2,}\b\D+` tenta corresponder a um limite de palavra seguido por pelo menos dois dígitos seguidos por um limite de palavra e um caractere não dígito. O exemplo a seguir ilustra essa expressão regular. A expressão regular não corresponde a frase `"7 days"` porque ele contém apenas um dígito decimal, mas ele corresponde com êxito as frases `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`\d{2,}`|Corresponder a pelo menos dois dígitos decimais.|  
|`\b`|Corresponder a um limite de palavra.|  
|`\D+`|Corresponder a pelo menos uma casa não decimal.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Corresponder entre n e m vezes: {n,m}  
 O `{`  *n*  `,` *m* `}` quantificador coincide com o elemento anterior pelo menos  *n*  vezes, mas não mais que *m* vezes, onde  *n*  e *m* são números inteiros. `{`*n*`,`*m* `}` é um quantificador greedy cujo equivalente lento é `{`  *n*  `,` *m*`}?`.  
  
 No exemplo a seguir, a expressão regular `(00\s){2,4}` tenta corresponder a entre duas e quatro ocorrências de dois dígitos zero seguidos por um espaço. Observe que a parte final da cadeia de caracteres de entrada inclui esse padrão de cinco vezes em vez de no máximo quatro. No entanto, apenas a parte inicial dessa subcadeia de caracteres (até o espaço e o quinto par de zeros) corresponde ao padrão de expressão regular.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Corresponder a zero ou mais vezes (correspondência lenta): *?  
 O `*?` quantificador coincide com o elemento anterior zero ou mais vezes, mas como algumas vezes possível. É a contraparte lenta de quantificador greedy `*`.  
  
 No exemplo a seguir, a expressão regular `\b\w*?oo\w*?\b` corresponde a todas as palavras que contêm a cadeia de caracteres `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`\w*?`|Corresponder a zero ou mais caracteres de palavra, mas o menor número de caracteres possível.|  
|`oo`|Corresponder à cadeia de caracteres “oo”.|  
|`\w*?`|Corresponder a zero ou mais caracteres de palavra, mas o menor número de caracteres possível.|  
|`\b`|Terminar em um limite de palavra.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Corresponder a uma ou mais vezes (correspondência lenta): +?  
 O `+?` quantificador coincide com o elemento anterior uma ou mais vezes, mas como algumas vezes possível. É a contraparte lenta de quantificador greedy `+`.  
  
 Por exemplo, a expressão regular `\b\w+?\b` corresponde a um ou mais caracteres separados por limites de palavra. O exemplo a seguir ilustra essa expressão regular.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Corresponder a zero ou uma vez (correspondência lenta): ??  
 O `??` quantificador corresponde à hora de elemento zero ou anterior, mas como algumas vezes possível. É a contraparte lenta de quantificador greedy `?`.  
  
 Por exemplo, a expressão regular `^\s*(System.)??Console.Write(Line)??\(??` tenta corresponder às cadeias de caracteres “Console.Write” ou “Console.WriteLine”. A cadeia de caracteres também pode incluir "System." antes de “Console” e pode ser seguida por um parêntese de abertura. A cadeia de caracteres deve estar no início de uma linha, embora possa ser antecedida por espaço em branco. O exemplo a seguir ilustra essa expressão regular.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`^`|Corresponder ao início do fluxo de entrada.|  
|`\s*`|Corresponder a zero ou mais caracteres de espaço em branco.|  
|`(System.)??`|Corresponde a zero ou uma ocorrência da cadeia de caracteres “System.”.|  
|`Console.Write`|Corresponder à cadeia de caracteres “Console.Write”.|  
|`(Line)??`|Corresponde a zero ou uma ocorrência da cadeia de caracteres “Line”.|  
|`\(??`|Corresponder a zero ou uma ocorrência do parêntese de abertura.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Corresponder exatamente a n vezes (correspondência lenta): {n}?  
 O `{`  *n*  `}?` quantificador coincide com o elemento anterior exatamente `n` vezes, onde  *n*  é qualquer inteiro. É a contraparte lenta de quantificador greedy `{`  *n*  `}+`.  
  
 No exemplo a seguir, a expressão regular `\b(\w{3,}?\.){2}?\w{3,}?\b` é usada para identificar um endereço de site. Observe que corresponde a “www.microsoft.com” e “msdn.microsoft.com”, mas não corresponde a “mywebsite” ou “mycompany.com”.  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`(\w{3,}?\.)`|Corresponder a pelo menos três caracteres de palavra, mas o menor número de caracteres possível, seguido por um caractere de ponto. Este é o primeiro grupo de captura.|  
|`(\w{3,}?\.){2}?`|Corresponder ao padrão no primeiro grupo duas vezes, mas o menor número de vezes possível.|  
|`\b`|Termina a correspondência em um limite de palavra.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Corresponder a pelo menos n vezes (correspondência lenta): {n,}?  
 O `{`  *n*  `,}?` quantificador coincide com o elemento anterior pelo menos `n` vezes, onde  *n*  é qualquer inteiro, mas como algumas vezes como é possível. É a contraparte lenta de quantificador greedy `{`  *n*  `,}`.  
  
 Consulte o exemplo para o `{`  *n*  `}?` quantificador na seção anterior para obter uma ilustração. A expressão regular esse exemplo usa o `{`  *n*  `,}` quantificador para corresponder uma cadeia de caracteres que tenha pelo menos três caracteres seguidos por um período.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Corresponder entre n e m vezes (correspondência lenta): {n,m}?  
 O `{`  *n*  `,` *m* `}?` quantificador coincide com o elemento anterior entre `n` e `m` vezes, onde  *n*  e *m* são inteiros, mas como algumas vezes possível. É a contraparte lenta de quantificador greedy `{`  *n*  `,` *m*`}`.  
  
 No exemplo a seguir, a expressão regular `\b[A-Z](\w*\s+){1,10}?[.!?]` corresponde a frases que contêm entre uma e dez palavras. Corresponde a todas as frases na cadeia de caracteres de entrada, exceto por uma frase que contém 18 palavras.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 O padrão de expressão regular é definido como mostra a tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`[A-Z]`|Corresponder a um caractere maiúscula de A a Z.|  
|`(\w*\s+)`|Corresponder a zero ou mais caracteres de palavra, seguidos por um ou mais caracteres de espaço em branco. Este é o primeiro grupo de captura.|  
|`{1,10}?`|Corresponder ao padrão anterior entre 1 e 10 vezes, mas o menor número de vezes possível.|  
|`[.!?]`|Corresponder a qualquer um dos caracteres de pontuação “.”, “!” ou “?”.|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Quantificadores Greedy e lentos  
 Alguns quantificadores têm duas versões:  
  
-   Uma versão Greedy.  
  
     Um quantificador Greedy tenta corresponder a um elemento tantas vezes quanto possível.  
  
-   Uma versão não greedy (ou lenta).  
  
     Um quantificador não Greedy tenta corresponder a um elemento o menor número de vezes possível. Você pode transformar um quantificador greedy em quantificador lazy simplesmente adicionando um `?`.  
  
 Considere uma expressão regular simples que se destina a extrair os últimos quatro dígitos de uma cadeia de caracteres de números, como um número de cartão de crédito. A versão da expressão regular que usa o `*` quantificador greedy é `\b.*([0-9]{4})\b`. No entanto, se uma cadeia de caracteres contiver dois números, essa expressão regular corresponde aos últimos quatro dígitos do segundo número, como mostra o exemplo a seguir.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 A expressão regular não coincidir com o primeiro número porque o `*` quantificador tenta corresponder o elemento anterior quantas vezes possível na cadeia de caracteres inteira e então encontrar sua correspondência no final da cadeia de caracteres.  
  
 Esse não é o comportamento desejado. Em vez disso, você pode usar o `*?`quantificador lento para extrair os dígitos de ambos os números, como mostra o exemplo a seguir.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Na maioria dos casos, expressões regulares com quantificadores Greedy e lentos retornam as mesmas correspondências. Mais comumente retornam resultados diferentes quando eles são usados com o caractere curinga (`.`) metacaractere, que corresponde a qualquer caractere.  
  
## <a name="quantifiers-and-empty-matches"></a>Quantificadores e correspondências vazias  
 Os quantificadores `*`, `+`, e `{`  *n*  `,` *m* `}` e suas contrapartes lentos nunca repetem depois vazio correspondência quando o número mínimo de captura foi encontrado. Essa regra impede que quantificadores entrem em loops infinitos em correspondências vazias de subexpressão quando o número máximo de capturas de grupo possíveis é infinito ou quase infinito.  
  
 Por exemplo, o código a seguir mostra o resultado de uma chamada para o <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> método com o padrão de expressão regular `(a?)*`, que corresponde a zero ou um "a" caractere zero ou mais vezes. Observe que o único grupo de captura captura cada "a" como bem como <xref:System.String.Empty?displayProperty=nameWithType>, mas que não há nenhuma correspondência vazia segundo, porque a primeira correspondência vazia faz com que o quantificador pare de repetir.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Para ver a diferença prática entre um grupo de captura que define um número mínimo e máximo de captura e um que define um número fixo de capturas, considere os padrões de expressão regular `(a\1|(?(1)\1)){0,2}` e `(a\1|(?(1)\1)){2}`. Ambas as expressões regulares consistem em um único grupo de captura, que é definido como mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`(a\1`|Faça qualquer correspondência a “a” juntamente com o valor do primeiro grupo capturado…|  
|`&#124;(?(1)`|… ou teste se o primeiro grupo capturado foi definido. (Observe que o `(?(1)` construção não define um grupo de captura.)|  
|`\1))`|Se o primeiro grupo capturado existir, faça uma correspondência ao valor. Se o grupo não existir, o grupo corresponderá <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 A primeira expressão regular tenta corresponder a esse padrão entre zero e duas vezes; a segunda, exatamente duas vezes. Como o primeiro padrão atinge o número mínimo de captura com sua primeira captura de <xref:System.String.Empty?displayProperty=nameWithType>, nunca se repete para tentar corresponder `a\1`; o `{0,2}` quantificador permite apenas correspondências vazias na última iteração. Por outro lado, a segunda expressão regular corresponde a “a” porque avalia `a\1` uma segunda vez; o número mínimo de iterações, 2, força o mecanismo a se repetir após uma correspondência vazia.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Linguagem de expressão regular – referência rápida](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Retrocesso](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
