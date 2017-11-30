---
title: "Exemplo de expressão regular: Verificação de HREFs"
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
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bc9db7317c7a73f70a2cb83322b8b3a4c3771b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Exemplo de expressão regular: Verificação de HREFs
O exemplo a seguir procura uma cadeia de caracteres de entrada e exibe todos os valores href="…" e suas localizações na cadeia de caracteres.  
  
## <a name="the-regex-object"></a>O objeto Regex  
 Porque o `DumpHRefs` método pode ser chamado várias vezes do código do usuário, ele usa o `static` (`Shared` no Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> método. Isso permite que o mecanismo de expressão regular para armazenar em cache a expressão regular e evita a sobrecarga da instanciação de um novo <xref:System.Text.RegularExpressions.Regex> objeto cada vez que o método é chamado. Um <xref:System.Text.RegularExpressions.Match> objeto é usado para iterar por todas as correspondências na cadeia de caracteres.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 O exemplo a seguir mostra uma chamada para o método `DumpHRefs`.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 O padrão da expressão regular `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` é interpretado conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`href`|Corresponder à cadeia de caracteres literal “href”. A correspondência não diferencia maiúsculas de minúsculas.|  
|`\s*`|Corresponder a zero ou mais caracteres de espaço em branco.|  
|`=`|Coincide com o sinal de igual.|  
|`\s*`|Corresponder a zero ou mais caracteres de espaço em branco.|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|Corresponde a um dos seguintes sem atribuir o resultado a um grupo capturado:<br /><br /> -Um sinal de aspas ou apóstrofo, seguido por zero ou mais ocorrências de qualquer caractere que não seja um sinal de aspas ou apóstrofo, seguido por um sinal de aspas ou apóstrofo. O grupo chamado `1` está incluído nesse padrão.<br />-Um ou mais caracteres de espaço não em branco. O grupo chamado `1` está incluído nesse padrão.|  
|`(?<1>[^"']*)`|Atribuir zero ou mais ocorrências de qualquer caractere diferente de aspas simples ou apóstrofe ao grupo de captura chamado `1`.|  
|`"(?<1>\S+)`|Atribuir um ou mais caracteres diferentes de espaço em branco ao grupo de captura chamado `1`.|  
  
## <a name="match-result-class"></a>Classe de resultado de correspondência  
 Os resultados de uma pesquisa são armazenados no <xref:System.Text.RegularExpressions.Match> classe, que fornece acesso a todas as subcadeias de caracteres extraídas pela pesquisa. Ela também lembra a cadeia de caracteres que está sendo pesquisada e a expressão regular que está sendo usada, para que ele pode chamar o <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> método para executar outra pesquisa iniciando onde a última terminou.  
  
## <a name="explicitly-named-captures"></a>Capturas nomeadas explicitamente  
 Em expressões regulares tradicionais, os parênteses de captura são numerados sequencialmente de forma automática. Isso causa dois problemas. Primeiro, se uma expressão regular for modificada pela inserção ou remoção de um conjunto de parênteses, todo o código que se refere às captura numeradas deverá ser reescrito para refletir a nova numeração. Em segundo lugar, como diferentes conjuntos de parênteses geralmente são usados para fornecer duas expressões alternativas para uma correspondência aceitável, pode ser difícil determinar qual das duas expressões realmente retornou um resultado.  
  
 Para resolver esses problemas, o <xref:System.Text.RegularExpressions.Regex> classe oferece suporte à sintaxe `(?<name>…)` para capturar uma correspondência em um slot especificado (o slot pode ser nomeado usando uma cadeia de caracteres ou um inteiro; inteiros podem ser recuperados mais rapidamente). Assim, todas as correspondências alternativas para a mesma cadeia de caracteres podem ser direcionadas para o mesmo local. Em caso de conflito, a última correspondência solta em um slot é a correspondência com êxito. (No entanto, está disponível uma lista completa de diversas correspondências para um único slot. Consulte o <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> coleção para obter detalhes.)  
  
## <a name="see-also"></a>Consulte também  
 [Expressões regulares do .NET](../../../docs/standard/base-types/regular-expressions.md)
