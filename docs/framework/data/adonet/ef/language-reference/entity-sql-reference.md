---
title: Referência de Entity SQL
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: a114bf9b58da255f560564d3fedfee598adb22b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766729"
---
# <a name="entity-sql-reference"></a>Referência de Entity SQL
Esta seção contém [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tópicos de referência. Este tópico resume e agrupa os [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores por categoria.  
  
## <a name="arithmetic-operators"></a>Operadores aritméticos  
 Os operadores aritméticos executam operações matemáticas em duas expressões de um ou mais tipos de dados numéricos. A tabela a seguir lista os operadores aritméticos do [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Operador|Use|  
|--------------|---------|  
|[+ (Adição)](../../../../../../docs/framework/data/adonet/ef/language-reference/add.md)|Adição.|  
|"/ (Divisão)"|Divisão.|  
|[% (Módulo)](../../../../../../docs/framework/data/adonet/ef/language-reference/modulo-entity-sql.md)|Retorna o restante de uma divisão.|  
|[* (Multiplicação)](../../../../../../docs/framework/data/adonet/ef/language-reference/multiply-entity-sql.md)|Multiplicação.|  
|[- (Negativo)](../../../../../../docs/framework/data/adonet/ef/language-reference/negative-entity-sql.md)|Negação.|  
|[- (Subtração)](../../../../../../docs/framework/data/adonet/ef/language-reference/subtract-entity-sql.md)|Subtração.|  
  
## <a name="canonical-functions"></a>Funções canônicas  
 As funções canônicas têm suporte por todos os provedores de dados e podem ser usadas por todas as tecnologias de consulta. A tabela a seguir lista as funções canônicas.  
  
|Função|Tipo|  
|--------------|----------|  
|[Funções canônicas de SQL de agregação de entidade](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|Discute funções canônicas de agregação de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Funções canônicas matemáticas](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|Discute funções canônicas matemáticas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Funções canônicas de cadeia de caracteres](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|Discute funções canônicas de cadeias de caracteres de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Funções canônicas de data e hora](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Discute funções canônicas de data e hora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Funções canônicas bit a bit](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Discute funções canônicas bit a bit de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Outras funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)|Discute as funções não classificadas como bit a bit, data/hora, cadeia de caracteres, matemática ou de agregação.|  
  
## <a name="comparison-operators"></a>Operadores de comparação  
 Os operadores de comparação são definidos para os seguintes tipos: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time`, `DateTimeOffset`. A promoção de tipos implícito ocorre para os operandos antes de o operador de comparação ser aplicado. Os operadores de comparação sempre produzem valores boolianos. Quando pelo menos um dos operandos for `null`, o resultado será `null`.  
  
 Igualdade e desigualdade são definidas para qualquer tipo de objeto que tem identidade, como o tipo `Boolean`. Objetos não primitivos com identidade são considerados iguais se compartilham a mesma identidade. A tabela a seguir lista os operadores de comparação do [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Operador|Descrição|  
|--------------|-----------------|  
|[= (É igual a)](../../../../../../docs/framework/data/adonet/ef/language-reference/equals-entity-sql.md)|Compara a igualdade de duas expressões.|  
|[> (Maior que)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que a expressão da direita.|  
|[>= (Maior ou igual a)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-or-equal-to-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que ou igual à expressão da direita.|  
|[É &AMP;#91;NÃO&AMP;#93; NULO](../../../../../../docs/framework/data/adonet/ef/language-reference/isnull-entity-sql.md)|Determina se uma expressão de consulta é nula.|  
|[< (Menor que)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda tem um valor menor que a expressão da direita.|  
|[<= (Menor ou igual a)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-or-equal-to-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda tem um valor menor que ou igual à expressão da direita.|  
|[&AMP;#91;NÃO&AMP;#93; BETWEEN](../../../../../../docs/framework/data/adonet/ef/language-reference/between-entity-sql.md)|Determina se uma expressão resulta em um valor em um intervalo especificado.|  
|[!= (Não é igual a)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-equal-to-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda não é igual a expressão da direita.|  
|[&#91;NOT&#93; LIKE](../../../../../../docs/framework/data/adonet/ef/language-reference/like-entity-sql.md)|Determina se uma cadeia de caracteres específica corresponde a um padrão especificado.|  
  
## <a name="logical-and-case-expression-operators"></a>Operadores lógicos e de expressão CASE  
 Os operadores lógicos testam a verdade de uma condição. A expressão CASE avalia um conjunto de expressões boolianas para determinar o resultado. A tabela a seguir lista os operadores lógicos e de expressão CASE.  
  
|Operador|Descrição|  
|--------------|-----------------|  
|[& & (AND lógico)](../../../../../../docs/framework/data/adonet/ef/language-reference/and-entity-sql.md)|AND lógico.|  
|[Operador (Não lógico)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-entity-sql.md)|NOT lógico.|  
|[&#124;&#124;(OR lógico)](../../../../../../docs/framework/data/adonet/ef/language-reference/or-entity-sql.md)|OR lógico.|  
|[CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)|Avalia um conjunto de expressões boolianas para determinar o resultado.|  
|[THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)|O resultado de uma [quando](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998) cláusula quando ela é avaliada como true.|  
  
## <a name="query-operators"></a>Operadores de Consulta  
 Os operadores de consulta são usados para definir as expressões de consulta que retornam dados de entidade. A tabela a seguir lista os operadores de consulta.  
  
|Operador|Use|  
|--------------|---------|  
|[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)|Especifica a coleção que é usada em [selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instruções.|  
|[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)|Especifica os grupos no qual os objetos que são retornados por uma consulta ([selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expressão devem ser colocados.|  
|[GroupPartition](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)|Retorna uma coleção de valores de argumento, projetada fora da partição do grupo para o qual a agregação está relacionada.|  
|[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)|Especifica um critério de pesquisa para um grupo ou uma agregação.|  
|[LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)|Usado com o [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula de paginação física executada.|  
|[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)|Especifica a ordem de classificação que é usada em objetos retornados em uma [selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrução.|  
|[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)|Especifica os elementos na projeção que são retornados por uma consulta.|  
|[SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)|Usado com o [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula de paginação física executada.|  
|[TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)|Especifica que apenas o primeiro conjunto de linhas será retornado do resultado da consulta.|  
|[WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)|Filtra condicionalmente os dados que são retornados por uma consulta.|  
  
## <a name="reference-operators"></a>Operadores de referência  
 Uma referência é um ponteiro lógico (chave estrangeira) para uma entidade específica em um conjunto de entidades específico. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suporta os seguintes operadores para construir, decompor e navegar por meio de referências.  
  
|Operador|Use|  
|--------------|---------|  
|[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)|Cria referências para uma entidade em um conjunto de entidades.|  
|[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)|Desreferencia um valor de referência e gera o resultado dessa desreferência.|  
|[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)|Extraia a chave de uma referência ou uma expressão de entidade.|  
|[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)|Permite que você navegue na relação de um tipo de objeto para outro|  
|[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)|Retorna uma referência a uma instância de entidade.|  
  
## <a name="set-operators"></a>Operador de conjunto  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece várias operações de conjunto avançadas. Isso inclui o conjunto de operadores semelhantes a operadores de Transact-SQL, como UNION, INTERSECT, EXCEPT e EXISTS. O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também dá suporte a operadores para eliminação duplicada (SET), testes de associação (IN) e junções (JOIN). A tabela a seguir lista os operadores de conjunto do [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Operador|Use|  
|--------------|---------|  
|[ANYELEMENT](../../../../../../docs/framework/data/adonet/ef/language-reference/anyelement-entity-sql.md)|Extrai um elemento de uma coleção multivalorada.|  
|[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)|Retorna uma coleção de todos os valores distintos da expressão de consulta para a esquerda do operando EXCEPT que também não são retornados da expressão de consulta à direita do operando EXCEPT.|  
|[&#91;NOT&#93; EXISTS](../../../../../../docs/framework/data/adonet/ef/language-reference/exists-entity-sql.md)|Determina se uma coleção está vazia.|  
|[FLATTEN](../../../../../../docs/framework/data/adonet/ef/language-reference/flatten-entity-sql.md)|Converte uma coleção de coleções em uma coleção combinada.|  
|[&#91;NOT&#93; IN](../../../../../../docs/framework/data/adonet/ef/language-reference/in-entity-sql.md)|Determina se um valor corresponde a qualquer valor em uma coleção.|  
|[INTERSECT](../../../../../../docs/framework/data/adonet/ef/language-reference/intersect-entity-sql.md)|Retorna uma coleção de todos os valores diferentes que são retornados pelas expressões de consulta nos lados esquerdo e direito do operando INTERSECT.|  
|[OVERLAPS](../../../../../../docs/framework/data/adonet/ef/language-reference/overlaps-entity-sql.md)|Determina se duas coleções têm elementos comuns.|  
|[SET](../../../../../../docs/framework/data/adonet/ef/language-reference/set-entity-sql.md)|Usado para converter uma coleção de objetos em um conjunto gerando uma nova coleção com todos os elementos duplicados removidos.|  
|[UNION](../../../../../../docs/framework/data/adonet/ef/language-reference/union-entity-sql.md)|Combina os resultados de duas ou mais consultas em uma única coleção.|  
  
## <a name="type-operators"></a>Operadores de tipo  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Fornece operações que permitem que o tipo de uma expressão (valor) a ser construído, consultados e manipulados. A tabela a seguir lista os operadores que são usados para trabalhar com tipos.  
  
|Operador|Use|  
|--------------|---------|  
|[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)|Converte uma expressão de um tipo de dados para outro.|  
|[COLLECTION](../../../../../../docs/framework/data/adonet/ef/language-reference/collection-entity-sql.md)|Usado em uma [função](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operação para declarar uma coleção de tipos de entidade ou tipos complexos.|  
|[É &AMP;#91;NÃO&AMP;#93; OF](../../../../../../docs/framework/data/adonet/ef/language-reference/isof-entity-sql.md)|Determina se o tipo de uma expressão é do tipo especificado ou um de seus subtipos.|  
|[OFTYPE](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)|Retorna uma coleção de objetos de uma expressão de consulta que é de um tipo específico.|  
|[Construtor de tipo nomeado](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)|Usado para criar instâncias de tipos de entidade ou tipos complexos.|  
|[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)|Cria uma instância de um multiset de uma lista de valores.|  
|[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)|Constrói registros anônimos e tipados estruturalmente de um ou mais valores.|  
|[TREAT](../../../../../../docs/framework/data/adonet/ef/language-reference/treat-entity-sql.md)|Trata um objeto de um tipo base específico como um objeto do tipo derivado especificado.|  
  
## <a name="other-operators"></a>Outros operadores  
 A tabela a seguir lista outros [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores.  
  
|Operador|Use|  
|--------------|---------|  
|[+ (Concatenação de cadeia de caracteres)](../../../../../../docs/framework/data/adonet/ef/language-reference/string-concatenation-entity-sql.md)|Usado para concatenar cadeias de caracteres no [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[. (Acesso a Membro)](../../../../../../docs/framework/data/adonet/ef/language-reference/member-access-entity-sql.md)|Usado para acessar o valor de uma propriedade ou campo de uma instância do tipo estrutural de modelo conceitual.|  
|[-- (Comentário)](../../../../../../docs/framework/data/adonet/ef/language-reference/comment-entity-sql.md)|Inclui comentários de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)|Define uma função embutida que pode ser executada em uma consulta Entity SQL.|  
  
## <a name="see-also"></a>Consulte também  
 [Entity SQL Language](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)
