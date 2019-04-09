---
title: COMO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 8f210c83a8220f11a5e0a461c8b72466f00a4e37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197705"
---
# <a name="like-entity-sql"></a>COMO (Entity SQL)
Determina se um elemento `String` de caracteres corresponde a um padrão especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  
 `match`  
 Uma [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão que é avaliada como um `String`.  
  
 `pattern`  
 Um padrão para correspondência com o elemento `String` especificado.  
  
 `escape`  
 Um caractere de escape.  
  
 NOT  
 Especifica que o resultado de LIKE seja negado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Se o `string` corresponde ao padrão; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressões que usam o operador LIKE são avaliadas basicamente da mesma maneira que expressões que usam igualdade como critérios de filtro. No entanto, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressões que usam o operador LIKE podem incluir literais e caracteres curinga.  
  
 A tabela a seguir descreve a sintaxe de `string` do padrão.  
  
|Caractere curinga|Descrição|Exemplo|  
|------------------------|-----------------|-------------|  
|%|Qualquer `string` entre zero ou mais caracteres.|`title like '%computer%'` Localiza todos os títulos com a palavra `"computer"` em qualquer lugar no título.|  
|_ (sublinhado)|Qualquer caractere único.|`firstname like '_ean'` Localiza todos os nomes de primeiro de quatro letras que terminam com `"ean`, ", como Dean ou Sean.|  
|[ ]|Qualquer caractere único no intervalo ([a-f]) ou no conjunto ([abcdef]) especificado.|`lastname like '[C-P]arsen'` Localiza os sobrenomes terminam com "arsen" e que começam com qualquer caractere único entre C e P, como Carsen ou Larsen.|  
|[^]|Qualquer caractere único que não esteja no intervalo ([^a-f]) nem no conjunto ([^abcdef]) especificado.|`lastname like 'de[^l]%'` Localiza todos os sobrenomes que começam com "de" e não incluem "l" como letra seguinte.|  
  
> [!NOTE]
>  O operador [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE e a cláusula ESCAPE não podem ser aplicados a valores de `System.DateTime` ou `System.Guid`.  
  
 LIKE dá suporte à correspondência de padrões ASCII e à correspondência de padrões Unicode. Quando todos os parâmetros são caracteres ASCII, a correspondência de padrões ASCII é executada. Se um ou mais dos argumentos são Unicode, todos os argumentos são convertidos em Unicode e a correspondência de padrões Unicode é executada. Quando você usa Unicode com LIKE, espaços em branco à direita são significativos; no entanto, para não Unicode, os espaços em branco à direita não são significativos. A sintaxe de cadeia de caracteres de padrão de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é o mesmo da [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
 Um padrão pode incluir caracteres regulares e caracteres curinga. Durante a correspondência de padrões, os caracteres regulares devem corresponder exatamente aos caracteres especificados no caractere `string`. No entanto, os caracteres curinga podem ser correspondentes com fragmentos arbitrários da cadeia de caracteres. Quando usado com caracteres curinga, o operador LIKE é mais flexível do que os operadores de comparação de cadeia de caracteres = e! =.  
  
> [!NOTE]
>  Você pode usar extensões específicas ao provedor se o destino for um provedor específico. No entanto, esses construtores podem ser tratados de maneira diferente por outros provedores, por exemplo. O SqlServer dá suporte aos padrões [first-last] e [^first-last], onde o primeiro padrão corresponde exatamente a um caractere entre o primeiro e o último, e o segundo padrão corresponde exatamente a um caractere que não esteja entre o primeiro e o último.  
  
### <a name="escape"></a>Escape  
 Ao usar a cláusula ESCAPE, você pode pesquisar cadeias de caracteres que incluam um ou mais dos caracteres curinga especiais descritos na tabela da seção anterior. Por exemplo, suponha que vários documentos incluam o literal "100%" no título e que você deseje pesquisar em todos esses documentos. Porque a porcentagem (%)) é um caractere curinga, você deve escapá-la usando o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cláusula de ESCAPE para executar com êxito a pesquisa. Veja a seguir um exemplo desse filtro.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 Nesta expressão de pesquisa, o caractere curinga de porcentagem (%) que segue imediatamente o caractere de ponto de exclamação (!) é tratado como um literal, não como um caractere curinga. Você pode usar qualquer caractere como um caractere de escape, exceto para o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] caracteres curinga e o quadrado de colchete (`[ ]`) caracteres. No exemplo anterior, o caractere de ponto de exclamação (!) é o caractere de escape.  
  
## <a name="example"></a>Exemplo  
 Os dois seguintes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consultas usam SIMILARES e operadores ESCAPE para determinar se uma cadeia de caracteres específica corresponde a um padrão especificado. A primeira consulta procura o `Name` que começa com os caracteres `Down_`. Essa consulta usa a opção ESCAPE porque o sublinhado (`_`) é um caractere curinga. Sem especificar a opção ESCAPE, a consulta pesquisaria todos `Name` valores que começam com a palavra `Down` seguido por qualquer caractere único que não seja o caractere de sublinhado. As consultas são com base no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento em [como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
