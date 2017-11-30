---
title: "Construtores de referência inversa em expressões regulares"
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
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a884e70f542c2ed7ff63e39cb7eadedf0ef7b4d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a>Construtores de referência inversa em expressões regulares
As referências inversas fornecem uma maneira conveniente de identificar um caractere ou subcadeia de caracteres repetida em uma cadeia de caracteres. Por exemplo, se a cadeia de caracteres de entrada contiver várias ocorrências de uma subcadeia de caracteres arbitrária, você poderá corresponder a primeira ocorrência a um grupo de captura e, em seguida, usar uma referência inversa para corresponder às ocorrências subsequentes da subcadeia de caracteres.  
  
> [!NOTE]
>  Uma sintaxe separada é usada para se referir a grupos de captura nomeados e numerados em cadeias de caracteres de substituição. Para obter mais informações, consulte [substituições](substitutions-in-regular-expressions.md).  
  
 O .NET define elementos de linguagem separados para se referir a grupos de captura nomeados e numerados. Para obter mais informações sobre grupos de captura, consulte [construções de agrupamento](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="numbered-backreferences"></a>Referências inversas numeradas  
 Uma referência inversa numerada usa a seguinte sintaxe:  
  
 `\`*número*  
  
 em que *number* é a posição ordinal do grupo de captura na expressão regular. Por exemplo, `\4` corresponde ao conteúdo do quarto grupo de captura. Se *número* não é definido no padrão de expressão regular, um erro de análise ocorre e o mecanismo de expressão regular gera um <xref:System.ArgumentException>. Por exemplo, a expressão regular `\b(\w+)\s\1` é válida porque `(\w+)` é o primeiro e único grupo de captura na expressão. Por outro lado, `\b(\w+)\s\2` é inválida e gera uma exceção de argumento porque não há nenhum grupo de captura com o número `\2`.  
  
 Observe a ambiguidade entre códigos de escape octal (como `\16`) e `\` *número* referências inversas que usam a mesma notação. Essa ambiguidade é resolvida da seguinte maneira:  
  
-   As expressões `\1` a `\9` sempre são interpretadas como referências inversas e não como códigos octais.  
  
-   Se o primeiro dígito de uma expressão de diversos for 8 ou 9 (como `\80` ou `\91`), a expressão será interpretada como uma literal.  
  
-   Expressões de `\10` e maiores serão consideradas referências inversas se houver uma referência inversa correspondente àquele número, caso contrário, elas serão interpretadas como códigos octais.  
  
-   Se uma expressão regular contém uma referência anterior para um número de grupo indefinido, ocorre um erro de análise e o mecanismo de expressão regular gera um <xref:System.ArgumentException>.  
  
 Se a ambiguidade for um problema, você pode usar o `\k<` *nome* `>` notação, que é ambíguo e não pode ser confundido com códigos de caracteres octal. Da mesma forma, os códigos hexadecimais como `\xdd` são não ambíguos e não podem ser confundidos com referências inversas.  
  
 O exemplo a seguir localiza caracteres de palavra duplicados em uma cadeia de caracteres. Ele define uma expressão regular, `(\w)\1`, que consiste nos elementos a seguir.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`(\w)`|Corresponde a um caractere de palavra e o atribui ao primeiro grupo de captura.|  
|`\1`|Corresponde ao próximo caractere que é o mesmo que o valor do primeiro grupo de captura.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a>Referências inversas nomeadas  
 Uma referência inversa nomeada é definida usando a sintaxe a seguir:  
  
 `\k<`*nome*`>`  
  
 ou:  
  
 `\k'`*nome*`'`  
  
 em que *name* é o nome de um grupo de captura definido no padrão da expressão regular. Se *nome* não é definido no padrão de expressão regular, um erro de análise ocorre e o mecanismo de expressão regular gera um <xref:System.ArgumentException>.  
  
 O exemplo a seguir localiza caracteres de palavra duplicados em uma cadeia de caracteres. Ele define uma expressão regular, `(?<char>\w)\k<char>`, que consiste nos elementos a seguir.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`(?<char>\w)`|Corresponder um caractere de palavra e atribuí-la a um grupo de captura nomeado `char`.|  
|`\k<char>`|Corresponde o próximo caractere é o mesmo que o valor da `char` grupo de captura.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 Observe que *name* também pode ser a representação da cadeia de caracteres de um número. Por exemplo, o exemplo a seguir usa a expressão regular `(?<2>\w)\k<2>` para localizar caracteres de palavra duplicados em uma cadeia de caracteres.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a>A que as referências inversas correspondem  
 Uma referência inversa refere-se à definição mais recente de um grupo (a definição mais imediatamente à esquerda, ao fazer a correspondência da esquerda para a direita). Quando um grupo faz várias capturas, uma referência inversa refere-se à captura mais recente.  
  
 O exemplo a seguir inclui um padrão de expressão regular, `(?<1>a)(?<1>\1b)*`, que redefine o grupo nomeado \1. A tabela a seguir descreve cada padrão na expressão regular.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`(?<1>a)`|Associar o caractere "a" e atribuir o resultado para o grupo de captura nomeado `1`.|  
|`(?<1>\1b)*`|Ocorrência de correspondência 0 ou 1 do grupo denominado `1` juntamente com um "b" e atribui o resultado para o grupo de captura nomeado `1`.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 Comparando a expressão regular com a cadeia de caracteres de entrada ("aababb"), o mecanismo de expressões regulares realiza as seguintes operações:  
  
1.  Ele começa no início da cadeia de caracteres e corresponde com êxito o “a” com a expressão `(?<1>a)`. O valor de `1` grupo agora é "a".  
  
2.  Ele avança para o segundo caractere e corresponde com êxito a cadeia de caracteres "ab" com a expressão `\1b`, ou "ab". Em seguida, atribui o resultado, "ab", a `\1`.  
  
3.  Ele avança para o quarto caractere. A expressão `(?<1>\1b)` deve ser correspondida zero ou mais vezes, de forma que corresponda com êxito a cadeia de caracteres “abb” à expressão `\1b`. Ela atribui o resultado, “abb”, a `\1`.  
  
 Neste exemplo, `*` é um quantificador looping – ele é avaliado repetidamente até que o mecanismo de expressões regulares não corresponda ao padrão definido. Os quantificadores de looping não limpam definições de grupo.  
  
 Se um grupo não capturou nenhuma subcadeia de caracteres, uma referência inversa a esse grupo é indefinida e nunca corresponde. Isso é ilustrado pelo padrão de expressão regular `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, que é definida da seguinte maneira:  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Começa a correspondência em um limite de palavra.|  
|`(\p{Lu}{2})`|Corresponde a duas letras maiúsculas. Este é o primeiro grupo de captura.|  
|`(\d{2})?`|Corresponde a zero ou uma ocorrência de dois dígitos decimais. Este é o segundo grupo de captura.|  
|`(\p{Lu}{2})`|Corresponde a duas letras maiúsculas. Este é o terceiro grupo de captura.|  
|`\b`|Termina a correspondência em um limite de palavra.|  
  
 Uma cadeia de caracteres de entrada pode corresponder a essa expressão regular, mesmo se os dois dígitos decimais que são definidos pelo segundo grupo de captura não estiverem presentes. O exemplo a seguir mostra que, embora a correspondência seja bem-sucedida, um grupo de captura vazio foi encontrado entre dois grupos de captura com êxito.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Linguagem de expressão regular – referência rápida](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
