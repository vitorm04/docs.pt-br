---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: fbe27f6e25c9d69f092a060fa2c3fbf0abc93318
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250509"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
Determina se um elemento `String` de caracteres corresponde a um padrão especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  
 `match`  
 Uma [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão que é avaliada como `String`um.  
  
 `pattern`  
 Um padrão para correspondência com o elemento `String` especificado.  
  
 `escape`  
 Um caractere de escape.  
  
 NOT  
 Especifica que o resultado de LIKE seja negado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se `string` corresponde ao padrão; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]as expressões que usam o operador LIKE são avaliadas quase da mesma forma que as expressões que usam igualdade como os critérios de filtro. No entanto, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as expressões que usam o operador Like podem incluir literais e caracteres curinga.  
  
 A tabela a seguir descreve a sintaxe de `string` do padrão.  
  
|Caractere curinga|Descrição|Exemplo|  
|------------------------|-----------------|-------------|  
|%|Qualquer `string` entre zero ou mais caracteres.|`title like '%computer%'`localiza todos os títulos com a `"computer"` palavra em qualquer lugar no título.|  
|_ (sublinhado)|Qualquer caractere único.|`firstname like '_ean'`localiza todos os nomes de quatro letras que terminam `"ean`com, "como o nome do atendimento ou Sílvio.|  
|[ ]|Qualquer caractere único no intervalo ([a-f]) ou no conjunto ([abcdef]) especificado.|`lastname like '[C-P]arsen'`localiza os últimos nomes que terminam com "grosseiran" e começando com qualquer caractere único entre C e P, como carros ou Larsen.|  
|[^]|Qualquer caractere único que não esteja no intervalo ([^a-f]) nem no conjunto ([^abcdef]) especificado.|`lastname like 'de[^l]%'`localiza todos os sobrenomes que começam com "de" e não incluem "l" como a letra a seguir.|  
  
> [!NOTE]
> O operador [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE e a cláusula ESCAPE não podem ser aplicados a valores de `System.DateTime` ou `System.Guid`.  
  
 LIKE dá suporte à correspondência de padrões ASCII e à correspondência de padrões Unicode. Quando todos os parâmetros são caracteres ASCII, a correspondência de padrões ASCII é executada. Se um ou mais dos argumentos são Unicode, todos os argumentos são convertidos em Unicode e a correspondência de padrões Unicode é executada. Quando você usa Unicode com LIKE, espaços em branco à direita são significativos; no entanto, para não Unicode, os espaços em branco à direita não são significativos. A sintaxe da cadeia de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] caracteres de padrão é a mesma do Transact-SQL.  
  
 Um padrão pode incluir caracteres regulares e caracteres curinga. Durante a correspondência de padrões, os caracteres regulares devem corresponder exatamente aos caracteres especificados no caractere `string`. No entanto, os caracteres curinga podem ser correspondentes com fragmentos arbitrários da cadeia de caracteres. Quando usado com caracteres curinga, o operador LIKE é mais flexível do que os operadores de comparação de cadeia de caracteres = e! =.  
  
> [!NOTE]
> Você pode usar extensões específicas ao provedor se o destino for um provedor específico. No entanto, esses construtores podem ser tratados de maneira diferente por outros provedores, por exemplo. O SqlServer dá suporte aos padrões [first-last] e [^first-last], onde o primeiro padrão corresponde exatamente a um caractere entre o primeiro e o último, e o segundo padrão corresponde exatamente a um caractere que não esteja entre o primeiro e o último.  
  
### <a name="escape"></a>Escape  
 Ao usar a cláusula ESCAPE, você pode pesquisar cadeias de caracteres que incluam um ou mais dos caracteres curinga especiais descritos na tabela da seção anterior. Por exemplo, suponha que vários documentos incluam o literal "100%" no título e que você deseje pesquisar em todos esses documentos. Porque a porcentagem (%) caractere é um caractere curinga, você deve escapar dele usando a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cláusula escape para executar a pesquisa com êxito. Veja a seguir um exemplo desse filtro.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 Nesta expressão de pesquisa, o caractere curinga de porcentagem (%) que segue imediatamente o caractere de ponto de exclamação (!) é tratado como um literal, não como um caractere curinga. Você pode usar qualquer caractere como um caractere de escape, exceto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] os caracteres curinga e os caracteres de`[ ]`colchete (). No exemplo anterior, o caractere de ponto de exclamação (!) é o caractere de escape.  
  
## <a name="example"></a>Exemplo  
 As duas [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consultas a seguir usam os operadores like e escape para determinar se uma cadeia de caracteres específica corresponde a um padrão especificado. A primeira consulta procura o `Name` que começa com os caracteres. `Down_` Essa consulta usa a opção ESCAPE porque o sublinhado (`_`) é um caractere curinga. Sem especificar a opção de escape, a consulta pesquisaria quaisquer `Name` valores que comecem com a `Down` palavra seguida por qualquer caractere único que não seja o caractere de sublinhado. As consultas são baseadas no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna os resultados](../how-to-execute-a-query-that-returns-primitivetype-results.md)de primitivatype.  
  
2. Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
