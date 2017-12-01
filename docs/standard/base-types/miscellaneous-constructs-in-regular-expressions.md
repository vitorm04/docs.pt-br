---
title: "Construtores diversos em expressões regulares"
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
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9b33d196a7af9bc5a1f81c1624bbd98fea074319
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Construtores diversos em expressões regulares
As expressões regulares em .NET incluem três constructos diversos de linguagem. Um deles permite habilitar ou desabilitar opções específicas de correspondência no meio de um padrão de expressão regular. Os dois restantes permitem incluir comentários em uma expressão regular.  
  
## <a name="inline-options"></a>Opções embutidas  
 É possível definir ou desabilitar opções específicas de correspondência de padrão para parte de uma expressão regular mediante uso da sintaxe  
  
```  
(?imnsx-imnsx)  
```  
  
 Você lista as opções que deseja habilitar após o ponto de interrogação e as opções que deseja desabilitar após o sinal de subtração. A tabela a seguir descreve cada opção. Para obter mais informações sobre cada opção, consulte [Opções de expressões regulares](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Opção|Descrição|  
|------------|-----------------|  
|`i`|Correspondência sem diferenciação entre maiúsculas e minúsculas.|  
|`m`|Modo multilinha.|  
|`n`|Apenas capturas explícitas. (Parênteses não funcionam como grupos de captura.)|  
|`s`|Modo de linha única.|  
|`x`|Ignorar espaço em branco sem escape e permitir comentários no modo x.|  
  
 Qualquer alteração nas opções de expressão regular definida pelo `(?imnsx-imnsx)` construir permanece em vigor até o fim do grupo delimitador.  
  
> [!NOTE]
>  O `(?imnsx-imnsx:` *subexpressão* `)` agrupamento fornece uma funcionalidade idêntica de uma subexpressão. Para obter mais informações, consulte [construções de agrupamento](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 O exemplo a seguir usa o `i`, `n`, e `x` opções para habilitar a diferenciação de maiusculas e captura explícita e ignorar espaço em branco no padrão de expressão regular no meio de uma expressão regular.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 O exemplo define duas expressões regulares. A primeira, `\b(D\w+)\s(d\w+)\b`, corresponde a duas palavras consecutivas que começam com um “D” maiúsculo e um “d” minúsculo. A segunda expressão regular, `\b(D\w+)(?ixn) \s (d\w+) \b`, usa opções embutidas para modificar esse padrão, conforme descrito na tabela a seguir. Uma comparação dos resultados confirma o efeito do constructo `(?ixn)`.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`(D\w+)`|Corresponder a um “D” maiúsculo seguido por um ou mais caracteres de palavra. Este é o primeiro grupo de captura.|  
|`(?ixn)`|Desse ponto em diante, faça comparações sem distinção de maiúsculas e minúsculas, faça apenas capturas explícitas e ignore o espaço em branco no padrão de expressão regular.|  
|`\s`|Corresponde a um caractere de espaço em branco.|  
|`(d\w+)`|Corresponder a um “d” maiúsculo ou minúsculo seguido por um ou mais caracteres de palavra. Esse grupo não é capturado porque o `n` (captura explícita) opção foi habilitada.|  
|`\b`|Corresponder a um limite de palavra.|  
  
## <a name="inline-comment"></a>Comentário embutido  
 O `(?#` *comentário* `)` construção permite que você inclua um comentário embutido em uma expressão regular. O mecanismo de expressão regular não usa qualquer parte do comentário na correspondência de padrões, embora o comentário é incluído na cadeia de caracteres que é retornada pelo <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> método. O comentário é encerrado no primeiro caractere de fechar parênteses.  
  
 O exemplo a seguir repete o primeiro padrão de expressão regular do exemplo na seção anterior. Ele adiciona dois comentários embutidos na expressão regular para indicar se a comparação diferencia maiúsculas de minúsculas. O padrão de expressão regular, `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, é definido da seguinte forma.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`(?# case-sensitive comparison)`|Um comentário. Não afeta o comportamento de correspondência.|  
|`(D\w+)`|Corresponder a um “D” maiúsculo seguido por um ou mais caracteres de palavra. Este é o primeiro grupo de captura.|  
|`\s`|Corresponde a um caractere de espaço em branco.|  
|`(?ixn)`|Desse ponto em diante, faça comparações sem distinção de maiúsculas e minúsculas, faça apenas capturas explícitas e ignore o espaço em branco no padrão de expressão regular.|  
|`(?#case-insensitive comparison)`|Um comentário. Não afeta o comportamento de correspondência.|  
|`(d\w+)`|Corresponder a um “d” maiúsculo ou minúsculo seguido por um ou mais caracteres de palavra. Este é o segundo grupo de captura.|  
|`\b`|Corresponder a um limite de palavra.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Comentário de final de linha  
 Um sinal de número (`#`) marca um modo de comentário x, que começa com o caractere # sem escape no final do padrão de expressão regular e continua até o final da linha. Para usar esta construção, você deve ativar o `x` opção (por meio de opções de embutidos) ou fornecer o <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> o valor para o `option` parâmetro ao instanciar o <xref:System.Text.RegularExpressions.Regex> objeto ou chamar estático <xref:System.Text.RegularExpressions.Regex> método.  
  
 O exemplo a seguir ilustra o constructo do comentário de final de linha. Ele determina se uma cadeia de caracteres é uma cadeia de caracteres de formato de composição que inclui pelo menos um item de formato. A tabela a seguir descreve os constructos no padrão de expressão regular:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\{`|Corresponder a uma chave de abertura.|  
|`\d+`|Corresponde a um ou mais dígitos decimais.|  
|`(,-*\d+)*`|Corresponder a zero ou a uma ocorrência de vírgula, seguida por um sinal de subtração opcional, seguido por um ou mais dígitos decimais.|  
|`(\:\w{1,4}?)*`|Corresponder a zero ou a uma ocorrência de dois-pontos, seguido de um a quatro caracteres em branco, mas o mínimo possível.|  
|`(?#case insensitive comparison)`|Um comentário embutido. Não tem nenhum efeito no comportamento de correspondência de padrão.|  
|`\}`|Corresponder a uma chave de fechamento.|  
|`(?x)`|Habilitar a opção de ignorar espaço em branco no padrão para o comentário de final de linha ser reconhecido.|  
|`# Looks for a composite format item.`|Um comentário de final de linha.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Observe que, em vez de fornecer o `(?x)` construir na expressão regular, o comentário pode também foram reconhecido chamando o <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> método e passá-lo a <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> valor de enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [Linguagem de expressão regular – referência rápida](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
