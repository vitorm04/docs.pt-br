---
title: Coleções de esquema do Oracle
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: cb91a90ae7323283556954caa401646a2063a37e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783287"
---
# <a name="oracle-schema-collections"></a>Coleções de esquema do Oracle

O Microsoft .NET Framework Provedor de Dados para Oracle dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:

- Colunas

- Índices

- IndexColumns

- Procedimentos

- Sequências

- Sinônimos

- Tabelas

- Usuários

- Exibições

- Funções

- Pacotes

- PackageBodies

- Arguments

- UniqueKeys

- PrimaryKeys

- ForeignKeys

- ForeignKeyColumns

- Procedimentoparameters

## <a name="columns"></a>Colunas

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da tabela, exibição ou cluster.|
|TABLE_NAME|Cadeia de Caracteres|Tabela, exibição ou nome do cluster.|
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|
|id|Decimal|Número de sequência da coluna como criado.|
|TIPO DE DADOS|Cadeia de Caracteres|Tipo de dados da coluna.|
|MUITO|Decimal|Comprimento da coluna em bytes.|
|PRECISO|Decimal|Precisão decimal para tipo de dados de número; precisão binária para tipo de dados FLOAT, NULL para todos os outros tipos de dado.|
|ESCALONÁVE|Decimal|Dígitos à direita do ponto decimal em um número.|
|ANULA|Cadeia de Caracteres|Especifica se uma coluna permite nulos. O valor será N se houver uma restrição NOT NULL na coluna ou se a coluna fizer parte de uma chave primária.|

## <a name="indexes"></a>Índices

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do índice|
|INDEX_NAME|Cadeia de Caracteres|Nome do índice.|
|INDEX_TYPE|Cadeia de Caracteres|Tipo de índice (NORMAL, BITMAP, NORMAL baseado em função, BITMAP baseado em função ou domínio).|
|TABLE_OWNER|Cadeia de Caracteres|Proprietário do objeto indexado.|
|TABLE_NAME|Cadeia de Caracteres|Nome do objeto indexado.|
|TABLE_TYPE|Cadeia de Caracteres|Tipo do objeto indexado (por exemplo, tabela, CLUSTER).|
|EXCLUSIVIDADE|Cadeia de Caracteres|Se o índice é exclusivo ou não exclusivo.|
|ÇÃ|Cadeia de Caracteres|Se o índice está habilitado ou DESABILITAdo.|
|PREFIX_LENGTH|Decimal|Número de colunas no prefixo da chave de compactação.|
|TABLESPACE_NAME|Cadeia de Caracteres|Nome do espaço de tabela que contém o índice.|
|INI_TRANS|Decimal|Número inicial de transações.|
|MAX_TRANS|Decimal|Número máximo de transações.|
|INITIAL_EXTENT|Decimal|Tamanho da extensão inicial.|
|NEXT_EXTENT|Decimal|Tamanho das extensões secundárias.|
|MIN_EXTENTS|Decimal|Número mínimo de extensões permitidas no segmento.|
|MAX_EXTENTS|Decimal|Número máximo de extensões permitidas no segmento.|
|PCT_INCREASE|Decimal|Percentual de aumento no tamanho da extensão.|
|PCT_THRESHOLD|Decimal|Porcentagem de limite de espaço de bloco permitida por entrada de índice.|
|INCLUDE_COLUMN|Decimal|A ID da coluna da última coluna a ser incluída no índice de chave primária da tabela organizada de índice (sem estouro). Esta coluna é mapeada para a coluna COLUMN_ID das exibições do dicionário de dados * _TAB_COLUMNS.|
|LISTAS LIVRES|Decimal|Número de listas livres de processo alocadas para este segmento.|
|FREELIST_GROUPS|Decimal|Número de grupos de listas livres alocados para este segmento.|
|PCT_FREE|Decimal|Porcentagem mínima de espaço livre em um bloco.|
|LOGOUT|Cadeia de Caracteres|Registrando informações.|
|BLEVEL|Decimal|B *-nível de árvore: profundidade do índice de seu bloco raiz para seus blocos folha. Uma profundidade de 0 indica que o bloco raiz e o bloco folha são os mesmos.|
|LEAF_BLOCKS|Decimal|Número de blocos folha no índice|
|DISTINCT_KEYS|Decimal|Número de valores indexados distintos. Para índices que impõem restrições UNIQUE e PRIMARY KEY, esse valor é o mesmo que o número de linhas na tabela (USER_TABLES. NUM_ROWS).|
|AVG_LEAF_BLOCKS_PER_KEY|Decimal|Número médio de blocos folha nos quais cada valor distinto no índice aparece arredondado para o número inteiro mais próximo. Para índices que impõem restrições UNIQUE e PRIMARY KEY, esse valor é sempre 1.|
|AVG_DATA_BLOCKS_PER_KEY|Decimal|Número médio de blocos de dados na tabela que são apontados por um valor distinto no índice arredondado para o número inteiro mais próximo. Essa estatística é o número médio de blocos de dados que contêm linhas que contêm um determinado valor para as colunas indexadas.|
|CLUSTERING_FACTOR|Decimal|Indica a quantidade de ordem das linhas na tabela com base nos valores do índice.|
|ESTADO|Cadeia de Caracteres|Se um índice não particionado é válido ou não pode ser usado.|
|NUM_ROWS|Decimal|Número de linhas no índice.|
|SAMPLE_SIZE|Decimal|Tamanho do exemplo usado para analisar o índice.|
|LAST_ANALYZED|DateTime|Data em que esse índice foi analisado mais recentemente.|
|DETERMINADO|Cadeia de Caracteres|Número de threads por instância para verificação do índice.|
|OCASIÕES|Cadeia de Caracteres|Número de instâncias em que os índices serão examinados.|
|PARTICIONADA|Cadeia de Caracteres|Se esse índice está particionado (Sim &#124; não).|
|TEMPORARY|Cadeia de Caracteres|Se o índice está em uma tabela temporária.|
|CRIADO|Cadeia de Caracteres|Se o nome do índice é gerado pelo sistema (Y&#124;N).|
|SECUNDÁRIO|Cadeia de Caracteres|Se o índice é um objeto secundário criado pelo método ODCIIndexCreate do cartucho de dados Oracle9i (Y&#124;N).|
|BUFFER_POOL|Cadeia de Caracteres|Nome do pool de buffers padrão a ser usado para os blocos de índice.|
|USER_STATS|Cadeia de Caracteres|Se as estatísticas foram inseridas diretamente pelo usuário.|
|PERMANÊNCIA|Cadeia de Caracteres|Indica a duração de uma tabela temporária: 1) SYS $ SESSION: as linhas são preservadas durante a sessão, 2) SYS $ TRANSACTION: as linhas são excluídas após COMMIT, 3) NULL para a tabela permanente.|
|PCT_DIRECT_ACCESS|Decimal|Para um índice secundário em uma tabela organizada por índice, a porcentagem de linhas com uma estimativa válida|
|ITYP_OWNER|Cadeia de Caracteres|Para um índice de domínio, o proprietário do indextype.|
|ITYP_NAME|Cadeia de Caracteres|Para um índice de domínio, o nome do indextype.|
|PARÂMETRO|Cadeia de Caracteres|Para um índice de domínio, a cadeia de caracteres do parâmetro.|
|GLOBAL_STATS|Cadeia de Caracteres|Para índices particionados, indica se as estatísticas foram coletadas analisando o índice como um todo (Sim) ou se foram estimadas de estatísticas em partições e subpartições de índice subjacentes (não).|
|DOMIDX_STATUS|Cadeia de Caracteres|Reflete o status do índice de domínio. NULL: o índice especificado não é um índice de domínio. VÁLIDO: o índice é um índice de domínio válido. IDXTYP_INVLD: o tipo de índice deste índice de domínio é inválido.|
|DOMIDX_OPSTATUS|Cadeia de Caracteres|Reflete o status de uma operação que foi executada em um índice de domínio: NULL: o índice especificado não é um índice de domínio. VÁLIDO: a operação executada sem erros. FALHA: a operação falhou com um erro.|
|FUNCIDX_STATUS|Cadeia de Caracteres|Indica o status de um índice baseado em função: NULL: este não é um índice baseado em função, habilitado: o índice baseado em função está habilitado, DESABILITAdo: o índice baseado em função está desabilitado.|
|JOIN_INDEX|Cadeia de Caracteres|Indica se este é um índice de junção ou não.|

## <a name="indexcolumns"></a>IndexColumns

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|INDEX_OWNER|Cadeia de Caracteres|Proprietário do índice.|
|INDEX_NAME|Cadeia de Caracteres|Nome do índice.|
|TABLE_OWNER|Cadeia de Caracteres|Proprietário da tabela ou cluster.|
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela ou cluster.|
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna ou atributo da coluna de tipo de objeto.|
|COLUMN_POSITION|Decimal|Posição da coluna ou atributo dentro do índice.|
|COLUMN_LENGTH|Decimal|Comprimento indexado da coluna.|
|CHAR_LENGTH|Decimal|Comprimento máximo de ponto da coluna.|
|ASCENDE|Cadeia de Caracteres|Se a coluna está classificada em ordem decrescente.|

## <a name="procedures"></a>Procedimentos

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|
|OBJECT_NAME|Cadeia de Caracteres|Nome do objeto.|
|SUBOBJECT_NAME|Cadeia de Caracteres|Nome do subobjeto (por exemplo, partição).|
|OBJECT_ID|Decimal|O número do objeto Dictionary do objeto.|
|DATA_OBJECT_ID|Decimal|O número do objeto Dictionary do segmento que contém o objeto.|
|LAST_DDL_TIME|DateTime|Carimbo de data/hora para a última modificação do objeto resultante de um comando DDL (incluindo concessões e revogações).|
|TIMESTAMP|Cadeia de Caracteres|Carimbo de data/hora para a especificação do objeto (dados de caractere).|
|ESTADO|Cadeia de Caracteres|Status do objeto (válido, inválido ou N/A).|
|TEMPORARY|Cadeia de Caracteres|Se o objeto é temporário (a sessão atual pode ver apenas os dados colocados nesse objeto).|
|CRIADO|Cadeia de Caracteres|O nome deste sistema de objetos foi gerado? (Y &#124; N).|
|SECUNDÁRIO|Cadeia de Caracteres|Se este é um objeto secundário criado pelo método ODCIIndexCreate do cartucho de dados Oracle9i (Y &#124; N).|
|CRIAÇÃO|DateTime|A data em que o objeto foi criado.|

## <a name="sequences"></a>Sequências

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|SEQUENCE_OWNER|Cadeia de Caracteres|Nome do proprietário da sequência.|
|SEQUENCE_NAME|Cadeia de Caracteres|Nome da sequência.|
|MIN_VALUE|Decimal|Valor mínimo da sequência.|
|MAX_VALUE|Decimal|Valor máximo da sequência.|
|INCREMENT_BY|Decimal|Valor pelo qual a sequência é incrementada.|
|CYCLE_FLAG|Cadeia de Caracteres|A sequência é encapsulada ao longo do limite de alcance.|
|ORDER_FLAG|Cadeia de Caracteres|São números de sequência gerados na ordem.|
|CACHE_SIZE|Decimal|Número de números de sequência para armazenar em cache.|
|LAST_NUMBER|Decimal|Último número de sequência gravado no disco. Se uma sequência usar o Caching, o número gravado em disco será o último número colocado no cache de sequência. Esse número provavelmente será maior que o último número de sequência usado.|

## <a name="synonyms"></a>Sinônimos

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do sinônimo.|
|SYNONYM_NAME|Cadeia de Caracteres|Nome do sinônimo.|
|TABLE_OWNER|Cadeia de Caracteres|Proprietário do objeto referenciado pelo sinônimo.|
|TABLE_NAME|Cadeia de Caracteres|Nome do objeto referenciado pelo sinônimo.|
|DB_LINK|Cadeia de Caracteres|Nome do link de banco de dados referenciado, se houver.|

## <a name="tables"></a>Tabelas

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da tabela.|
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|
|ESCREVA|Cadeia de Caracteres|Tipo de tabela.|

## <a name="users"></a>Usuários

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|NAME|Cadeia de Caracteres|Nome do usuário.|
|id|Decimal|Número de identificação do usuário.|
|CREATEDATE|DateTime|Data de criação do usuário.|

## <a name="views"></a>Exibições

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da exibição.|
|VIEW_NAME|Cadeia de Caracteres|Nome da exibição.|
|TEXT_LENGTH|Decimal|Comprimento do texto da exibição.|
|TEXTO|Cadeia de Caracteres|Exibir texto.|
|TYPE_TEXT_LENGTH|Decimal|Comprimento da cláusula de tipo da exibição tipada.|
|TIPO_TEXTO|Cadeia de Caracteres|Cláusula Type da exibição tipada.|
|OID_TEXT_LENGTH|Decimal|Comprimento da cláusula WITH OID da exibição tipada.|
|OID_TEXT|Cadeia de Caracteres|COM a cláusula OID da exibição tipada.|
|VIEW_TYPE_OWNER|Cadeia de Caracteres|Proprietário do tipo de exibição se a exibição for uma exibição tipada.|
|VIEW_TYPE|Cadeia de Caracteres|Tipo de exibição se a exibição for uma exibição tipada.|
|SUPERVIEW_NAME|Cadeia de Caracteres|Nome da superexibição.|

## <a name="functions"></a>Funções

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|
|OBJECT_NAME|Cadeia de Caracteres|Nome do objeto.|
|SUBOBJECT_NAME|Cadeia de Caracteres|Nome do subobjeto (por exemplo, partição).|
|OBJECT_ID|Decimal|O número do objeto Dictionary do objeto.|
|DATA_OBJECT_ID|Decimal|O número do objeto Dictionary do segmento que contém o objeto.|
|OBJECT_TYPE|Cadeia de Caracteres|Tipo do objeto.|
|CRIAÇÃO|DateTime|A data em que o objeto foi criado.|
|LAST_DDL_TIME|DateTime|Carimbo de data/hora para a última modificação do objeto resultante de um comando DDL (incluindo concessões e revogações).|
|TIMESTAMP|Cadeia de Caracteres|Carimbo de data/hora para a especificação do objeto (dados de caractere)|
|ESTADO|Cadeia de Caracteres|Status do objeto (válido, inválido ou N/A).|
|TEMPORARY|Cadeia de Caracteres|Se o objeto é temporário (a sessão atual pode ver apenas os dados colocados nesse objeto).|
|CRIADO|Cadeia de Caracteres|O nome deste sistema de objetos foi gerado? (Y &#124; N).|
|SECUNDÁRIO|Cadeia de Caracteres|Se este é um objeto secundário criado pelo método ODCIIndexCreate do cartucho de dados Oracle9i (Y &#124; N).|

## <a name="packages"></a>Pacotes

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|
|OBJECT_NAME|Cadeia de Caracteres|Nome do objeto.|
|SUBOBJECT_NAME|Cadeia de Caracteres|Nome do subobjeto (por exemplo, partição).|
|OBJECT_ID|Decimal|O número do objeto Dictionary do objeto.|
|DATA_OBJECT_ID|Decimal|O número do objeto Dictionary do segmento que contém o objeto.|
|LAST_DDL_TIME|DateTime|Carimbo de data/hora para a última modificação do objeto resultante de um comando DDL (incluindo concessões e revogações).|
|TIMESTAMP|Cadeia de Caracteres|Carimbo de data/hora para a especificação do objeto (dados de caractere).|
|ESTADO|Cadeia de Caracteres|Status do objeto (válido, inválido ou N/A).|
|TEMPORARY|Cadeia de Caracteres|Se o objeto é temporário (a sessão atual pode ver apenas os dados colocados nesse objeto).|
|CRIADO|Cadeia de Caracteres|O nome deste sistema de objetos foi gerado? (Y &#124; N).|
|SECUNDÁRIO|Cadeia de Caracteres|Se este é um objeto secundário criado pelo método ODCIIndexCreate do cartucho de dados Oracle9i (Y &#124; N).|
|CRIAÇÃO|DateTime|A data em que o objeto foi criado.|

## <a name="packagebodies"></a>PackageBodies

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|
|OBJECT_NAME|Cadeia de Caracteres|Nome do objeto.|
|SUBOBJECT_NAME|Cadeia de Caracteres|Nome do subobjeto (por exemplo, partição).|
|OBJECT_ID|Decimal|O número do objeto Dictionary do objeto.|
|DATA_OBJECT_ID|Decimal|O número do objeto Dictionary do segmento que contém o objeto.|
|LAST_DDL_TIME|DateTime|Carimbo de data/hora para a última modificação do objeto resultante de um comando DDL (incluindo concessões e revogações).|
|TIMESTAMP|Cadeia de Caracteres|Carimbo de data/hora para a especificação do objeto (dados de caractere).|
|ESTADO|Cadeia de Caracteres|Status do objeto (válido, inválido ou N/A).|
|TEMPORARY|Cadeia de Caracteres|Se o objeto é temporário (a sessão atual pode ver apenas os dados colocados nesse objeto).|
|CRIADO|Cadeia de Caracteres|O nome deste sistema de objetos foi gerado? (Y &#124; N).|
|SECUNDÁRIO|Cadeia de Caracteres|Se este é um objeto secundário criado pelo método ODCIIndexCreate do cartucho de dados Oracle9i (Y &#124; N).|
|CRIAÇÃO|DateTime|A data em que o objeto foi criado.|

## <a name="arguments"></a>Arguments

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Nome do proprietário do objeto.|
|PACKAGE_NAME|Cadeia de Caracteres|Nome do pacote.|
|OBJECT_NAME|Cadeia de Caracteres|Nome do procedimento ou da função.|
|ARGUMENT_NAME|Cadeia de Caracteres|Nome do argumento.|
|PROPOSTAS|Decimal|Posição na lista de argumentos ou NULL para o valor de retorno da função.|
|ORDEM|Decimal|Sequência de argumentos, incluindo todos os níveis de aninhamento.|
|DEFAULT_VALUE|Cadeia de Caracteres|Valor padrão para o argumento.|
|DEFAULT_LENGTH|Decimal|Comprimento do valor padrão para o argumento.|
|IN_OUT|Cadeia de Caracteres|Direção do argumento (IN, OUT ou IN/OUT).|
|DATA_LENGTH|Decimal|Comprimento da coluna em bytes.|
|DATA_PRECISION|Decimal|Comprimento em dígitos decimais (número) ou dígitos binários (FLOAT).|
|DATA_SCALE|Decimal|Dígitos à direita do ponto decimal em um número.|
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados do argumento.|

## <a name="uniquekeys"></a>UniqueKeys

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da definição de restrição.|
|CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição.|
|TABLE_NAME|Cadeia de Caracteres|Nome associado à tabela (ou exibição) com definição de restrição.|
|SEARCH_CONDITION|Cadeia de Caracteres|Texto da condição de pesquisa para uma restrição de verificação.|
|R_OWNER|Cadeia de Caracteres|Proprietário da tabela referenciada em uma restrição referencial.|
|R_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição exclusiva para a tabela referenciada.|
|DELETE_RULE|Cadeia de Caracteres|Excluir regra para uma restrição referencial (em cascata ou nenhuma ação).|
|ESTADO|Cadeia de Caracteres|Status de imposição da restrição (habilitado ou DESABILITAdo).|
|NÃO REFERENCIABLE|Cadeia de Caracteres|Se a restrição é adiada.|
|VALID|Cadeia de Caracteres|Se todos os dados obedecem à restrição (VALIDAdo ou não VALIDAdo).|
|CRIADO|Cadeia de Caracteres|Se o nome da restrição é gerado pelo usuário ou pelo sistema.|
|SATISFATÓRIO|Cadeia de Caracteres|Um valor Sim indica que essa restrição especifica um século de maneira ambígua. Para evitar erros resultantes dessa ambiguidade, reescreva a restrição usando a função TO_DATE com um ano de quatro dígitos.|
|UTILIZE|Cadeia de Caracteres|Se uma restrição habilitada é imposta ou não imposta.|
|LAST_CHANGE|DateTime|Quando a restrição foi habilitada ou desabilitada pela última vez|
|INDEX_OWNER|Cadeia de Caracteres|Nome do usuário que possui o índice|
|INDEX_NAME|Cadeia de Caracteres|Nome do índice|

## <a name="primarykeys"></a>PrimaryKeys

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da definição de restrição.|
|CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição.|
|TABLE_NAME|Cadeia de Caracteres|Nome associado à tabela (ou exibição) com definição de restrição.|
|SEARCH_CONDITION|Cadeia de Caracteres|Texto da condição de pesquisa para uma restrição de verificação.|
|R_OWNER|Cadeia de Caracteres|Proprietário da tabela referenciada em uma restrição referencial.|
|R_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição exclusiva para a tabela referenciada.|
|DELETE_RULE|Cadeia de Caracteres|Excluir regra para uma restrição referencial (em cascata ou nenhuma ação).|
|ESTADO|Cadeia de Caracteres|Status de imposição da restrição (habilitado ou DESABILITAdo).|
|NÃO REFERENCIABLE|Cadeia de Caracteres|Se a restrição é adiada.|
|VALID|Cadeia de Caracteres|Se todos os dados obedecem à restrição (VALIDAdo ou não VALIDAdo).|
|CRIADO|Cadeia de Caracteres|Se o nome da restrição é gerado pelo usuário ou pelo sistema.|
|SATISFATÓRIO|Cadeia de Caracteres|Um valor Sim indica que essa restrição especifica um século de maneira ambígua. Para evitar erros resultantes dessa ambiguidade, reescreva a restrição usando a função TO_DATE com um ano de quatro dígitos.|
|UTILIZE|Cadeia de Caracteres|Se uma restrição habilitada é imposta ou não imposta.|
|LAST_CHANGE|DateTime|Quando a restrição foi habilitada ou desabilitada pela última vez.|
|INDEX_OWNER|Cadeia de Caracteres|Nome do usuário que possui o índice.|
|INDEX_NAME|Cadeia de Caracteres|Nome do índice.|

## <a name="foreignkeys"></a>ForeignKeys

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PRIMARY_KEY_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição.|
|PRIMARY_KEY_OWNER|Cadeia de Caracteres|Proprietário da definição de restrição.|
|PRIMARY_KEY_TABLE_NAME|Cadeia de Caracteres|Nome associado à tabela (ou exibição) com definição de restrição|
|FOREIGN_KEY_OWNER|Cadeia de Caracteres|Proprietário da definição de restrição.|
|FOREIGN_KEY_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição.|
|FOREIGN_KEY_TABLE_NAME|Cadeia de Caracteres|Nome associado à tabela (ou exibição) com definição de restrição.|
|SEARCH_CONDITION|Cadeia de Caracteres|Texto da condição de pesquisa para uma restrição de verificação|
|R_OWNER|Cadeia de Caracteres|Proprietário da tabela referenciada em uma restrição referencial.|
|R_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição exclusiva para a tabela referenciada.|
|DELETE_RULE|Cadeia de Caracteres|Excluir regra para uma restrição referencial (em cascata ou nenhuma ação).|
|ESTADO|Cadeia de Caracteres|Status de imposição da restrição (habilitado ou DESABILITAdo).|
|VALID|Cadeia de Caracteres|Se todos os dados obedecem à restrição (VALIDAdo ou não VALIDAdo).|
|CRIADO|Cadeia de Caracteres|Se o nome da restrição é gerado pelo usuário ou pelo sistema.|
|UTILIZE|Cadeia de Caracteres|Se uma restrição habilitada é imposta ou não imposta.|
|LAST_CHANGE|DateTime|Quando a restrição foi habilitada ou desabilitada pela última vez.|
|INDEX_OWNER|Cadeia de Caracteres|Nome do usuário que possui o índice.|
|INDEX_NAME|Cadeia de Caracteres|Nome do índice.|

## <a name="foreignkeycolumns"></a>ForeignKeyColumns

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da definição de restrição.|
|CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição.|
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela com definição de restrição.|
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna ou atributo da coluna de tipo de objeto especificada na definição de restrição.|
|PROPOSTAS|Decimal|Posição original da coluna ou do atributo na definição do objeto.|

## <a name="procedureparameters"></a>Procedimentoparameters

|ColumnName|DataType|Descrição|
|----------------|--------------|-----------------|
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|
|OBJECT_NAME|Cadeia de Caracteres|Nome do procedimento ou da função.|
|PACKAGE_NAME|Cadeia de Caracteres|Nome do procedimento ou da função.|
|OBJECT_ID|Decimal|Número de objeto do objeto.|
|SOBRECARGA|Cadeia de Caracteres|Identificador exclusivo de sobrecarga.|
|ARGUMENT_NAME|Cadeia de Caracteres|Nome do argumento.|
|PROPOSTAS|Decimal|Posição na lista de argumentos ou NULL para um valor de retorno de função.|
|ORDEM|Decimal|Sequência de argumentos, incluindo todos os níveis de aninhamento.|
|DATA_LEVEL|Decimal|Profundidade de aninhamento do argumento para tipos compostos.|
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados do argumento.|
|DEFAULT_VALUE|Cadeia de Caracteres|Valor padrão para o argumento.|
|DEFAULT_LENGTH|Decimal|Comprimento do valor padrão para o argumento.|
|IN_OUT|Cadeia de Caracteres|Direção do argumento (IN, OUT ou IN/OUT).|
|DATA_LENGTH|Decimal|Comprimento da coluna (em bytes).|
|DATA_PRECISION|Decimal|Comprimento em dígitos decimais (número) ou dígitos binários (FLOAT).|
|DATA_SCALE|Decimal|Dígitos à direita do ponto decimal em um número.|
|RADIX|Decimal|Base do argumento de um número.|
|CHARACTER_SET_NAME|Cadeia de Caracteres|Nome do conjunto de caracteres do argumento.|
|TYPE_OWNER|Cadeia de Caracteres|Proprietário do tipo do argumento.|
|TYPE_NAME|Cadeia de Caracteres|Nome do tipo do argumento. Se o tipo for um tipo local de pacote (ou seja, for declarado em uma especificação de pacote), essa coluna exibirá o nome do pacote.|
|TYPE_SUBNAME|Cadeia de Caracteres|Relevante apenas para tipos locais de pacote. Exibe o nome do tipo declarado no pacote identificado na coluna TYPE_NAME.|
|TYPE_LINK|Cadeia de Caracteres|Relevante apenas para tipos de pacote local quando o pacote identificado na coluna TYPE_NAME é um pacote remoto. Esta coluna exibe o link de banco de dados usado para fazer referência ao pacote remoto.|
|PLS_TYPE|Cadeia de Caracteres|Para argumentos numéricos, o nome do tipo PL/SQL do argumento. Do contrário, nulo.|
|CHAR_LENGTH|Decimal|Limite de caracteres para tipos de dados de cadeia de caracteres.|
|CHAR_USED|Cadeia de Caracteres|Indica se o limite de bytes (B) ou o limite de caracteres (C) é oficial para a cadeia de caracteres.|

## <a name="see-also"></a>Consulte também

- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
