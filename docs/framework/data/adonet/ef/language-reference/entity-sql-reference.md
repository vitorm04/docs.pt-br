---
title: Referência de Entity SQL
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 9b666b83674cb2374409e321a2b715e9910bdd0e
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826636"
---
# <a name="entity-sql-reference"></a>Referência de Entity SQL

Esta seção contém artigos de referência de Entity SQL. Este artigo resume e agrupa os operadores de Entity SQL por categoria.

## <a name="arithmetic-operators"></a>Operadores aritméticos

Os operadores aritméticos executam operações matemáticas em duas expressões de um ou mais tipos de dados numéricos. A tabela a seguir lista os operadores aritméticos de Entity SQL:

|Operador|Use|
|--------------|---------|
|[+ (Adição)](add.md)|Adição.|
|[/ (Divisão)](divide-entity-sql.md)|Divisão.|
|[% (Módulo)](modulo-entity-sql.md)|Retorna o restante de uma divisão.|
|[* (Multiplicação)](multiply-entity-sql.md)|Multiplicação.|
|[- (Negativo)](negative-entity-sql.md)|Negação.|
|[- (Subtração)](subtract-entity-sql.md)|Subtração.|

## <a name="canonical-functions"></a>Funções canônicas

As funções canônicas têm suporte por todos os provedores de dados e podem ser usadas por todas as tecnologias de consulta. A tabela a seguir lista as funções canônicas:

|Função|Tipo|
|--------------|----------|
|[Funções canônicas do agregação de Entity SQL](aggregate-canonical-functions.md)|Discute funções agregadas canônicas do Entity SQL.|
|[Funções canônicas matemáticas](math-canonical-functions.md)|Discute funções canônicas do Entity SQL matemáticas.|
|[Funções canônicas de cadeia de caracteres](string-canonical-functions.md)|Discute funções canônicas do Entity SQL de cadeia de caracteres.|
|[Funções canônicas de data e hora](date-and-time-canonical-functions.md)|Discute funções canônicas de data e hora Entity SQL.|
|[Funções canônicas bit a bit](bitwise-canonical-functions.md)|Discute funções canônicas bit a bit de Entity SQL.|
|[Outras funções canônicas](other-canonical-functions.md)|Discute as funções não classificadas como bit a bit, data/hora, cadeia de caracteres, matemática ou de agregação.|

## <a name="comparison-operators"></a>Operadores de comparação

Os operadores de comparação são definidos para os seguintes tipos: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time`, `DateTimeOffset`. A promoção de tipos implícito ocorre para os operandos antes de o operador de comparação ser aplicado. Os operadores de comparação sempre produzem valores boolianos. Quando pelo menos um dos operandos for `null`, o resultado será `null`.

Igualdade e desigualdade são definidas para qualquer tipo de objeto que tem identidade, como o tipo `Boolean`. Objetos não primitivos com identidade são considerados iguais se compartilham a mesma identidade. A tabela a seguir lista os operadores de comparação de Entity SQL:

|Operador|Descrição|
|--------------|-----------------|
|[= (É igual a)](equals-entity-sql.md)|Compara a igualdade de duas expressões.|
|[> (Maior que)](greater-than-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que a expressão da direita.|
|[>= (Maior ou igual a)](greater-than-or-equal-to-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que ou igual à expressão da direita.|
|[ESTÁ \[NÃO\] NULO](isnull-entity-sql.md)|Determina se uma expressão de consulta é nula.|
|[< (Menor que)](less-than-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda tem um valor menor que a expressão da direita.|
|[<= (Menor ou igual a)](less-than-or-equal-to-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda tem um valor menor que ou igual à expressão da direita.|
|[\[NÃO\] BETWEEN](between-entity-sql.md)|Determina se uma expressão resulta em um valor em um intervalo especificado.|
|[\!= (Igual a)](not-equal-to-entity-sql.md)|Compara duas expressões para determinar se a expressão da esquerda não é igual à expressão da direita.|
|[\[NOT\] LIKE](like-entity-sql.md)|Determina se uma cadeia de caracteres específica corresponde a um padrão especificado.|

## <a name="logical-and-case-expression-operators"></a>Operadores lógicos e de expressão case

Os operadores lógicos testam a verdade de uma condição. A expressão CASE avalia um conjunto de expressões boolianas para determinar o resultado. A tabela a seguir lista os operadores lógicos e de expressão CASE:

|Operador|Descrição|
|--------------|-----------------|
|[& & (AND lógico)](and-entity-sql.md)|AND lógico.|
|[\! (Não lógico)](not-entity-sql.md)|NOT lógico.|
|[&#124;&#124;(OR lógico)](or-entity-sql.md)|OR lógico.|
|[CASE](case-entity-sql.md)|Avalia um conjunto de expressões boolianas para determinar o resultado.|
|[THEN](then-entity-sql.md)|O resultado de uma [quando](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387119(v=vs.100)) cláusula quando avaliar como true.|

## <a name="query-operators"></a>Operadores de consulta

Os operadores de consulta são usados para definir as expressões de consulta que retornam dados de entidade. A tabela a seguir lista os operadores de consulta:

|Operador|Use|
|--------------|---------|
|[FROM](from-entity-sql.md)|Especifica a coleção que é usada na [selecionar](select-entity-sql.md) instruções.|
|[GROUP BY](group-by-entity-sql.md)|Especifica os grupos nos quais os objetos que são retornados por uma consulta ([selecionar](select-entity-sql.md)) expressão devem ser colocados.|
|[GroupPartition](grouppartition-entity-sql.md)|Retorna uma coleção de valores de argumento, projetada fora da partição do grupo para o qual a agregação está relacionada.|
|[HAVING](having-entity-sql.md)|Especifica um critério de pesquisa para um grupo ou uma agregação.|
|[LIMIT](limit-entity-sql.md)|Usado com o [ORDER BY](order-by-entity-sql.md) cláusula para paginação física executada.|
|[ORDER BY](order-by-entity-sql.md)|Especifica a ordem de classificação que é usada em objetos retornados em uma [selecionar](select-entity-sql.md) instrução.|
|[SELECT](select-entity-sql.md)|Especifica os elementos na projeção que são retornados por uma consulta.|
|[SKIP](skip-entity-sql.md)|Usado com o [ORDER BY](order-by-entity-sql.md) cláusula para paginação física executada.|
|[TOP](top-entity-sql.md)|Especifica que apenas o primeiro conjunto de linhas será retornado do resultado da consulta.|
|[WHERE](where-entity-sql.md)|Filtra condicionalmente os dados que são retornados por uma consulta.|

## <a name="reference-operators"></a>Operadores de referência

Uma referência é um ponteiro lógico (chave estrangeira) para uma entidade específica em um conjunto de entidades específico. Entity SQL dá suporte aos seguintes operadores para construir, desconstruir e navegar pelas referências:

|Operador|Use|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Cria referências para uma entidade em um conjunto de entidades.|
|[DEREF](deref-entity-sql.md)|Desreferencia um valor de referência e gera o resultado dessa desreferência.|
|[KEY](key-entity-sql.md)|Extraia a chave de uma referência ou uma expressão de entidade.|
|[NAVIGATE](navigate-entity-sql.md)|Permite que você navegue na relação de um tipo de objeto para outro|
|[REF](ref-entity-sql.md)|Retorna uma referência a uma instância de entidade.|

## <a name="set-operators"></a>Operador de conjunto

Entity SQL fornece várias operações de conjunto avançadas. Isso inclui os operadores de conjunto semelhantes aos operadores Transact-SQL como UNION, INTERSECT, EXCEPT e EXISTS. Entity SQL também oferece suporte a operadores para eliminação duplicada (SET), testes (em) de associação e junções (JOIN). A tabela a seguir lista os operadores de conjunto de Entity SQL:

|Operador|Use|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Extrai um elemento de uma coleção multivalorada.|
|[EXCEPT](except-entity-sql.md)|Retorna uma coleção de valores distintos da expressão de consulta à esquerda do operando EXCEPT que também não são retornados da expressão de consulta à direita do operando EXCEPT.|
|[\[NÃO\] EXISTS](exists-entity-sql.md)|Determina se uma coleção está vazia.|
|[FLATTEN](flatten-entity-sql.md)|Converte uma coleção de coleções em uma coleção combinada.|
|[\[NOT\] IN](in-entity-sql.md)|Determina se um valor corresponde a qualquer valor em uma coleção.|
|[INTERSECT](intersect-entity-sql.md)|Retorna uma coleção de todos os valores diferentes que são retornados pelas expressões de consulta nos lados esquerdo e direito do operando INTERSECT.|
|[OVERLAPS](overlaps-entity-sql.md)|Determina se duas coleções têm elementos comuns.|
|[SET](set-entity-sql.md)|Usado para converter uma coleção de objetos em um conjunto gerando uma nova coleção com todos os elementos duplicados removidos.|
|[UNION](union-entity-sql.md)|Combina os resultados de duas ou mais consultas em uma única coleção.|

## <a name="type-operators"></a>Operadores de tipo

Entity SQL fornece operações que permitem que o tipo de uma expressão (valor) a ser construído, consultado e manipulado. A tabela a seguir lista os operadores que são usados para trabalhar com tipos:

|Operador|Use|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Converte uma expressão de um tipo de dados para outro.|
|[COLLECTION](collection-entity-sql.md)|Usado em uma [função](function-entity-sql.md) operação para declarar uma coleção de tipos de entidade ou tipos complexos.|
|[ESTÁ \[NÃO\] OF](isof-entity-sql.md)|Determina se o tipo de uma expressão é do tipo especificado ou um de seus subtipos.|
|[OFTYPE](oftype-entity-sql.md)|Retorna uma coleção de objetos de uma expressão de consulta que é de um tipo específico.|
|[Construtor de tipo nomeado](named-type-constructor-entity-sql.md)|Usado para criar instâncias de tipos de entidade ou tipos complexos.|
|[MULTISET](multiset-entity-sql.md)|Cria uma instância de um multiset de uma lista de valores.|
|[ROW](row-entity-sql.md)|Constrói registros anônimos e tipados estruturalmente de um ou mais valores.|
|[TREAT](treat-entity-sql.md)|Trata um objeto de um tipo base específico como um objeto do tipo derivado especificado.|

## <a name="other-operators"></a>Outros operadores

A tabela a seguir lista outros operadores de Entity SQL:

|Operador|Use|
|--------------|---------|
|[+ (Concatenação de cadeia de caracteres)](string-concatenation-entity-sql.md)|Usado para concatenar cadeias de caracteres em Entity SQL.|
|[. (Acesso a Membro)](member-access-entity-sql.md)|Usado para acessar o valor de uma propriedade ou campo de uma instância do tipo estrutural de modelo conceitual.|
|[-- (Comentário)](comment-entity-sql.md)|Inclua comentários de Entity SQL.|
|[FUNCTION](function-entity-sql.md)|Define uma função embutida que pode ser executada em uma consulta Entity SQL.|

## <a name="see-also"></a>Consulte também

- [Entity SQL Language](entity-sql-language.md) (Linguagem SQL de entidade)
