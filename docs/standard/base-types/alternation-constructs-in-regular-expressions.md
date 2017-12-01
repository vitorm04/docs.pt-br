---
title: "Construtores de alternância em expressões regulares"
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
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6ad632130b6f111ff863648b8b1a3b2835c27660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="alternation-constructs-in-regular-expressions"></a>Construtores de alternância em expressões regulares
<a name="top"></a>Construtores de alternância modificam uma expressão regular para habilitar o / ou ou correspondência condicional. O .NET dá suporte a três constructos de alternância:  
  
-   [Correspondência de padrões com &#124;](#Either_Or)  
  
-   [Correspondendo condicional (? ( Sim de expressão) &#124; não)](#Conditional_Expr)  
  
-   [Correspondência condicional baseado em um grupo capturado válido](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>Correspondência de padrão com &#124;  
 Você pode usar a barra vertical (`|`) caracteres para corresponder a qualquer um de uma série de padrões, onde o `|` caractere que separa cada padrão.  
  
 Como a classe de caractere positivo, o `|` caractere pode ser usado para corresponder a qualquer um de um número de caracteres único. O exemplo a seguir usa uma classe de caractere positivo e um / ou correspondência de padrão com o `|` caractere para localizar as ocorrências das palavras "cinza" ou "cinza" em uma cadeia de caracteres. Nesse caso, o `|` caractere produz uma expressão regular é mais detalhada.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 A expressão regular que usa o `|` caractere, `\bgr(a|e)y\b`, é interpretado conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`gr`|Corresponder aos caracteres "gr".|  
|<code>(a&#124;e)</code>|Corresponder a um "a" ou "e".|  
|`y\b`|Corresponder a um “y” em um limite de palavra.|  
  
 O `|` caractere também pode ser usado para realizar uma / ou corresponder a vários caracteres ou subexpressões, que podem incluir qualquer combinação de literais de caracteres e elementos de linguagem de expressão regular. (A classe de caracteres não fornece essa funcionalidade.) O exemplo a seguir usa o `|` caractere para extrair a qualquer dos EUA Número de seguro social (SSN), que é um número de 9 dígitos com o formato *ddd*-*dd*-*dddd*, ou dos EUA Número de identificação de empregador (EIN), que é um número de 9 dígitos com o formato *dd*-*ddddddd*.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 A expressão regular `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretada conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Corresponde a uma das seguintes opções: dois dígitos decimais seguidos por um hífen seguido por sete dígitos decimais ou três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.|  
|`\d`|Termina a correspondência em um limite de palavra.|  
  
 [Voltar ao início](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>Correspondência condicional com uma expressão  
 Este elemento de linguagem tenta corresponder a um dos dois padrões dependendo de se ele pode corresponder a um padrão inicial. A sintaxe é:  
  
 `(?(`*expressão* `)` *Sim* `|` *sem*`)`  
  
 onde *expressão* é o padrão inicial para fazer a correspondência, *Sim* é o padrão para correspondência se *expressão* é correspondido e *sem* é opcional padrão para correspondência se *expressão* não corresponde. O mecanismo de expressões regulares trata a *expressão* como uma asserção de largura zero, isto é, o mecanismo de expressões regulares não avança no fluxo de entrada após avaliar a *expressão*. Portanto, esse constructo é equivalente ao seguinte:  
  
 `(?(?=`*expressão* `)` *Sim* `|` *sem*`)`  
  
 onde `(?=` *expressão* `)` é uma construção de declaração de largura zero. (Para obter mais informações, consulte [construções de agrupamento](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Porque o mecanismo de expressão regular interpreta *expressão* como uma âncora (uma declaração de largura zero), *expressão* deve ser uma declaração de largura zero (para obter mais informações, consulte [ Ancora](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) ou uma subexpressão que também está contida no *Sim*. Caso contrário, o padrão *sim* não pode ser correspondido.  
  
> [!NOTE]
>  Se *expressão*é um grupo de captura nomeado ou numerado, a construção de alternância é interpretada como um teste de captura; para obter mais informações, consulte a próxima seção, [condicional correspondência com base em um grupo de captura válido](#Conditional_Group). Em outras palavras, o mecanismo de expressões regulares não tenta corresponder a subcadeia de caracteres capturada, mas em vez disso, testa a presença ou ausência do grupo.  
  
 O exemplo a seguir é uma variação do exemplo que aparece no [tanto / ou correspondência de padrões com &#124;](#Either_Or) seção. Ele usa a correspondência condicional para determinar se os três primeiros caracteres após um limite de palavra são dois dígitos seguidos por um hífen. Se forem, ele tenta corresponder a um EIN (Número de Identificação de Empregador) dos EUA. Se não, ele tenta corresponder a um SSN (cadastro de pessoas físicas).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 O padrão da expressão regular `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretado conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`(?(\d{2}-)`|Determinar se os próximos três caracteres são compostos por dois dígitos seguidos por um hífen.|  
|`\d{2}-\d{7}`|Se o padrão anterior corresponder, corresponder a dois dígitos seguidos por um hífen seguido por sete dígitos.|  
|`\d{3}-\d{2}-\d{4}`|Se o padrão anterior não corresponder, corresponder a três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.|  
|`\b`|Corresponder a um limite de palavra.|  
  
 [Voltar ao início](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Correspondência condicional com base em um grupo capturado válido  
 Este elemento de linguagem tenta corresponder a um dos dois padrões dependendo de se ele correspondeu a um grupo de captura especificado. A sintaxe é:  
  
 `(?(`*nome* `)` *Sim* `|` *sem*`)`  
  
 ou  
  
 `(?(`*número* `)` *Sim* `|` *sem*`)`  
  
 onde *nome* é o nome e *número* é o número de um grupo de captura, *Sim* é a expressão para correspondência se *nome* ou *número* tiver uma correspondência, e *sem* é a expressão opcional para correspondência se não existir.  
  
 Se *name* não corresponder ao nome de um grupo de captura que é usado no padrão de expressão regular, o constructo de alternância será interpretado como teste de expressão, conforme explicado na seção anterior. Normalmente, isso significa que *expressão* é avaliada como `false`. Se *número* não corresponde a um grupo de captura numerado que é usado no padrão de expressão regular, a expressão regular mecanismo lança um <xref:System.ArgumentException>.  
  
 O exemplo a seguir é uma variação do exemplo que aparece no [tanto / ou correspondência de padrões com &#124;](#Either_Or) seção. Ele usa um grupo de captura chamado `n2` que consiste em dois dígitos seguidos por um hífen. O constructo de alternância testa se este grupo de captura foi correspondido na cadeia de caracteres de entrada. Em caso afirmativo, o constructo de alternância tenta corresponder aos sete últimos dígitos de um EIN (Número de Identificação de Empregador) dos EUA. Se não tiver, ele tenta corresponder a um SSN (cadastro de pessoas físicas).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 O padrão da expressão regular `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretado conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Iniciar em um limite de palavra.|  
|`(?<n2>\d{2}-)*`|Corresponder a zero ou uma ocorrência de dois dígitos seguidos por um hífen. Atribua um nome ao grupo de captura `n2`.|  
|`(?(n2)`|Testar se `n2` foi correspondido na cadeia de caracteres de entrada.|  
|`)\d{7}`|Se `n2` tiver sido correspondido, corresponder a sete dígitos decimais.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Se `n2` não tiver sido correspondido, corresponder a três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.|  
|`\b`|Corresponder a um limite de palavra.|  
  
 Uma variação desse exemplo que usa um grupo numerado em vez de um grupo nomeado é mostrada no exemplo a seguir. O padrão da expressão regular é `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Linguagem de expressão regular – referência rápida](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
