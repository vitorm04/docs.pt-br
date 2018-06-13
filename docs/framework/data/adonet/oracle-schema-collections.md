---
title: Coleções de esquema do Oracle
ms.date: 03/30/2017
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
ms.openlocfilehash: b86de542e425d6fdc56f238f90063988bee95ffa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766849"
---
# <a name="oracle-schema-collections"></a>Coleções de esquema do Oracle
O provedor de dados do Microsoft .NET Framework para Oracle oferece suporte aos seguintes coleções de esquema específico além das coleções de esquema comuns:  
  
-   Colunas  
  
-   Índices  
  
-   IndexColumns  
  
-   Procedimentos  
  
-   Sequências  
  
-   Sinônimos  
  
-   Tabelas  
  
-   Usuários  
  
-   Exibições  
  
-   Funções  
  
-   Pacotes  
  
-   PackageBodies  
  
-   Arguments  
  
-   UniqueKeys  
  
-   PrimaryKeys  
  
-   Chaves externas  
  
-   ForeignKeyColumns  
  
-   ProcedureParameters  
  
## <a name="columns"></a>Colunas  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da tabela, exibição ou cluster.|  
|TABLE_NAME|Cadeia de Caracteres|Tabela, exibição ou nome do cluster.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
|ID|Decimal|Número de sequência da coluna conforme criado.|  
|TIPO DE DADOS|Cadeia de Caracteres|Tipo de dados da coluna.|  
|COMPRIMENTO|Decimal|Comprimento da coluna em bytes.|  
|PRECISÃO|Decimal|Precisão decimal para o tipo de dados número; precisão binário para o tipo de dados FLOAT, nulo para todos os outros tipos de dados.|  
|ESCALA|Decimal|Dígitos à direita do ponto decimal em um número.|  
|PERMITE VALOR NULO|Cadeia de Caracteres|Especifica se uma coluna permite valores nulos. O valor é N se houver uma restrição NOT NULL na coluna ou se a coluna faz parte de uma chave primária.|  
  
## <a name="indexes"></a>Índices  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do índice|  
|INDEX_NAME|Cadeia de Caracteres|Nome do índice.|  
|INDEX_TYPE|Cadeia de Caracteres|Tipo de índice (NORMAL, BITMAP, NORMAL com base em função, com base em função BITMAP ou domínio).|  
|TABLE_OWNER|Cadeia de Caracteres|Proprietário do objeto indexado.|  
|TABLE_NAME|Cadeia de Caracteres|Nome do objeto indexado.|  
|TABLE_TYPE|Cadeia de Caracteres|Tipo do objeto indexado (por exemplo, a tabela, o CLUSTER).|  
|EXCLUSIVIDADE|Cadeia de Caracteres|Se o índice é exclusivo ou NONUNIQUE.|  
|COMPACTAÇÃO|Cadeia de Caracteres|Se o índice está habilitado ou desabilitado.|  
|PREFIX_LENGTH|Decimal|Número de colunas no prefixo da chave de compactação.|  
|TABLESPACE_NAME|Cadeia de Caracteres|Nome do espaço de tabela que contém o índice.|  
|INI_TRANS|Decimal|Número inicial de transações.|  
|MAX_TRANS|Decimal|Número máximo de transações.|  
|INITIAL_EXTENT|Decimal|Tamanho da extensão inicial.|  
|NEXT_EXTENT|Decimal|Tamanho da extensão do secundário.|  
|MIN_EXTENTS|Decimal|Número mínimo de extensões permitidas no segmento.|  
|MAX_EXTENTS|Decimal|Número máximo de extensões permitidas no segmento.|  
|PCT_INCREASE|Decimal|Porcentagem aumento no tamanho da extensão.|  
|PCT_THRESHOLD|Decimal|Porcentagem de limite de espaço de bloco permitido por entrada de índice.|  
|INCLUDE_COLUMN|Decimal|ID da coluna da última coluna a ser incluído no índice de chave primária (não estouro) da tabela organizada por índice. Esta coluna é mapeada para a coluna do COLUMN_ID do * modos de exibição de dicionário de dados _TAB_COLUMNS.|  
|LISTAS LIVRES|Decimal|Número de listas livres de processo alocado para este segmento.|  
|FREELIST_GROUPS|Decimal|Número de grupos de freelist alocado para este segmento.|  
|PCT_FREE|Decimal|Porcentagem mínima de espaço livre em um bloco.|  
|REGISTRO EM LOG|Cadeia de Caracteres|Informações de registro em log.|  
|BLEVEL|Decimal|B *-nível de árvore: profundidade do índice de seu bloco de raiz para seus blocos de folha. Uma profundidade de 0 indica que o bloco de raiz e folha são os mesmos.|  
|LEAF_BLOCKS|Decimal|Número de blocos de folha no índice|  
|DISTINCT_KEYS|Decimal|Número de valores distintos de indexada. Para índices que impõem restrições UNIQUE e PRIMARY KEY, esse valor é igual ao número de linhas na tabela (USER_TABLES. NUM_ROWS).|  
|AVG_LEAF_BLOCKS_PER_KEY|Decimal|Número médio de blocos de folha, na qual cada valor distinto no índice aparece arredondado para o inteiro mais próximo. Para índices que impõem restrições UNIQUE e PRIMARY KEY, esse valor é sempre 1.|  
|AVG_DATA_BLOCKS_PER_KEY|Decimal|Bloqueia o número médio de dados na tabela que está apontada por um valor distinto no índice, arredondado para o inteiro mais próximo. Essa estatística é o número médio de blocos de dados que contêm linhas que contêm um valor específico para as colunas indexadas.|  
|CLUSTERING_FACTOR|Decimal|Indica a quantidade da ordem das linhas na tabela com base nos valores de índice.|  
|STATUS|Cadeia de Caracteres|Se um índice não particionado é válido ou UNUSABLE.|  
|NUM_ROWS|Decimal|Número de linhas no índice.|  
|SAMPLE_SIZE|Decimal|Tamanho da amostra usado para analisar o índice.|  
|LAST_ANALYZED|DateTime|Data em que esse índice mais recentemente foi analisado.|  
|GRAU|Cadeia de Caracteres|Número de threads por instância, para verificar o índice.|  
|INSTÂNCIAS|Cadeia de Caracteres|Número de instâncias em que os índices a serem examinados.|  
|PARTICIONADO|Cadeia de Caracteres|Se esse índice é particionado (Sim &#124; não).|  
|TEMPORÁRIO|Cadeia de Caracteres|Se o índice está em uma tabela temporária.|  
|GERADO|Cadeia de Caracteres|Se o nome do índice é gerada pelo sistema (Y&#124;N).|  
|SECUNDÁRIO|Cadeia de Caracteres|Se o índice é um objeto secundário criado pelo método ODCIIndexCreate de cartucho de dados Oracle9i (Y&#124;N).|  
|BUFFER_POOL|Cadeia de Caracteres|Nome do pool de buffer padrão a ser usado para os blocos de índice.|  
|USER_STATS|Cadeia de Caracteres|Se as estatísticas foram inseridas diretamente pelo usuário.|  
|DURAÇÃO|Cadeia de Caracteres|Indica a duração de uma tabela temporária: 1) SYS$ sessão: as linhas são preservadas para a duração da sessão, 2) SYS$ transação: as linhas são excluídas após a confirmação, 3) Null para tabelas permanentes.|  
|PCT_DIRECT_ACCESS|Decimal|Para um índice secundário em uma tabela organizadas por índice, a porcentagem de linhas por estimativa válida|  
|ITYP_OWNER|Cadeia de Caracteres|Para um índice de domínio, o proprietário do indextype.|  
|ITYP_NAME|Cadeia de Caracteres|Para um índice de domínio, o nome do indextype.|  
|PARÂMETROS|Cadeia de Caracteres|Para um índice de domínio, a cadeia de caracteres do parâmetro.|  
|GLOBAL_STATS|Cadeia de Caracteres|Para índices particionados, indica se as estatísticas foram coletadas pela análise de índice como um todo (Sim) ou foram estimadas de estatísticas em partições de índice subjacente e subpartições (não).|  
|DOMIDX_STATUS|Cadeia de Caracteres|Reflete o status do índice de domínio. NULL: o índice especificado não é um índice de domínio. VÁLIDO: é o índice é um índice de domínio válido. IDXTYP_INVLD: o tipo de índice do índice domínio é inválido.|  
|DOMIDX_OPSTATUS|Cadeia de Caracteres|Reflete o status de uma operação que foi executada em um índice de domínio: NULL: o índice especificado não é um índice de domínio. VÁLIDO: a operação executada sem erros. Falha: a operação falhou com um erro.|  
|FUNCIDX_STATUS|Cadeia de Caracteres|Indica o status de um índice com base em função: nulo: isso não é uma função com base em índice habilitado: o índice baseado em função é habilitado, desabilitada: o índice baseado em função está desabilitado.|  
|JOIN_INDEX|Cadeia de Caracteres|Indica se este é um índice de junção ou não.|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|INDEX_OWNER|Cadeia de Caracteres|Proprietário do índice.|  
|INDEX_NAME|Cadeia de Caracteres|Nome do índice.|  
|TABLE_OWNER|Cadeia de Caracteres|Proprietário da tabela ou do cluster.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela ou do cluster.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna ou atributo da coluna de tipo de objeto.|  
|COLUMN_POSITION|Decimal|Posição da coluna ou o atributo dentro do índice.|  
|COLUMN_LENGTH|Decimal|Indexada comprimento da coluna.|  
|CHAR_LENGTH|Decimal|Comprimento máximo do ponto de código da coluna.|  
|DECRESCEM|Cadeia de Caracteres|Se a coluna está classificada em ordem decrescente.|  
  
## <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|  
|OBJECT_NAME|Cadeia de Caracteres|Nome do objeto.|  
|SUBOBJECT_NAME|Cadeia de Caracteres|Nome do subobjeto (por exemplo, a partição).|  
|OBJECT_ID|Decimal|Número de objeto de dicionário do objeto.|  
|DATA_OBJECT_ID|Decimal|Número de objeto de dicionário do segmento que contém o objeto.|  
|LAST_DDL_TIME|DateTime|Carimbo de hora para a última modificação do objeto de resultado de um comando DDL (incluindo as concessões e revoga).|  
|TIMESTAMP|Cadeia de Caracteres|Carimbo de hora para a especificação do objeto (dados de caractere).|  
|STATUS|Cadeia de Caracteres|Status do objeto (válido, inválido ou n/d).|  
|TEMPORÁRIO|Cadeia de Caracteres|Se o objeto é temporário (a sessão atual pode ver apenas os dados que foi colocada no próprio objeto).|  
|GERADO|Cadeia de Caracteres|É o nome do sistema objeto gerado? (Y &AMP;#124; N).|  
|SECUNDÁRIO|Cadeia de Caracteres|Se este é um objeto secundário criado pelo método ODCIIndexCreate de cartucho de dados Oracle9i (Y &#124; N).|  
|CRIADO|DateTime|A data em que o objeto foi criado.|  
  
## <a name="sequences"></a>Sequências  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|SEQUENCE_OWNER|Cadeia de Caracteres|Nome do proprietário da sequência.|  
|SEQUENCE_NAME|Cadeia de Caracteres|Nome da sequência.|  
|MIN_VALUE|Decimal|Valor mínimo da sequência.|  
|MAX_VALUE|Decimal|Valor máximo da sequência.|  
|INCREMENT_BY|Decimal|Valor pelo qual a sequência é incrementada.|  
|CYCLE_FLAG|Cadeia de Caracteres|Sequência circundar ao atingir o limite.|  
|ORDER_FLAG|Cadeia de Caracteres|Números de sequência são gerados na ordem.|  
|TAMANHO_DO_CACHE|Decimal|Número de números de sequência em cache.|  
|LAST_NUMBER|Decimal|Número de sequência último gravado no disco. Se uma sequência usa o cache, o número gravado em disco é o último número colocado no cache de sequência. Esse número é provavelmente será maior que o último número de sequência que foi usado.|  
  
## <a name="synonyms"></a>Sinônimos  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do sinônimo.|  
|SYNONYM_NAME|Cadeia de Caracteres|Nome do sinônimo.|  
|TABLE_OWNER|Cadeia de Caracteres|Proprietário do objeto mencionado pelo sinônimo.|  
|TABLE_NAME|Cadeia de Caracteres|Nome do objeto mencionado pelo sinônimo.|  
|DB_LINK|Cadeia de Caracteres|Nome do vínculo do banco de dados referenciado, se houver.|  
  
## <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|TIPO DE|Cadeia de Caracteres|Tipo de tabela.|  
  
## <a name="users"></a>Usuários  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|NAME|Cadeia de Caracteres|Nome do usuário.|  
|ID|Decimal|Número de identificação do usuário.|  
|CREATEDATE FORMATO|DateTime|Data de criação de usuário.|  
  
## <a name="views"></a>Exibições  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da exibição.|  
|VIEW_NAME|Cadeia de Caracteres|Nome da exibição.|  
|TEXT_LENGTH|Decimal|Comprimento do texto de exibição.|  
|TEXTO|Cadeia de Caracteres|Texto de exibição.|  
|TYPE_TEXT_LENGTH|Decimal|Comprimento da cláusula de tipo do modo de exibição digitada.|  
|TIPO_TEXTO|Cadeia de Caracteres|Digite a cláusula do modo de exibição digitada.|  
|OID_TEXT_LENGTH|Decimal|Comprimento da cláusula com OID do modo de exibição digitada.|  
|OID_TEXT|Cadeia de Caracteres|COM a cláusula OID do modo de exibição digitada.|  
|VIEW_TYPE_OWNER|Cadeia de Caracteres|Proprietário do tipo da exibição se a exibição é um modo de exibição digitado.|  
|VIEW_TYPE|Cadeia de Caracteres|Tipo de exibição se a exibição é um modo de exibição digitado.|  
|SUPERVIEW_NAME|Cadeia de Caracteres|Nome da visão ampla do.|  
  
## <a name="functions"></a>Funções  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|  
|OBJECT_NAME|Cadeia de Caracteres|Nome do objeto.|  
|SUBOBJECT_NAME|Cadeia de Caracteres|Nome do subobjeto (por exemplo, a partição).|  
|OBJECT_ID|Decimal|Número de objeto de dicionário do objeto.|  
|DATA_OBJECT_ID|Decimal|Número de objeto de dicionário do segmento que contém o objeto.|  
|OBJECT_TYPE|Cadeia de Caracteres|Tipo de objeto.|  
|CRIADO|DateTime|A data em que o objeto foi criado.|  
|LAST_DDL_TIME|DateTime|Carimbo de hora para a última modificação do objeto de resultado de um comando DDL (incluindo as concessões e revoga).|  
|TIMESTAMP|Cadeia de Caracteres|Carimbo de hora para a especificação do objeto (dados de caractere)|  
|STATUS|Cadeia de Caracteres|Status do objeto (válido, inválido ou n/d).|  
|TEMPORÁRIO|Cadeia de Caracteres|Se o objeto é temporário (a sessão atual pode ver apenas os dados que foi colocada no próprio objeto).|  
|GERADO|Cadeia de Caracteres|É o nome do sistema objeto gerado? (Y &AMP;#124; N).|  
|SECUNDÁRIO|Cadeia de Caracteres|Se este é um objeto secundário criado pelo método ODCIIndexCreate de cartucho de dados Oracle9i (Y &#124; N).|  
  
## <a name="packages"></a>Pacotes  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|  
|OBJECT_NAME|Cadeia de Caracteres|Nome do objeto.|  
|SUBOBJECT_NAME|Cadeia de Caracteres|Nome do subobjeto (por exemplo, a partição).|  
|OBJECT_ID|Decimal|Número de objeto de dicionário do objeto.|  
|DATA_OBJECT_ID|Decimal|Número de objeto de dicionário do segmento que contém o objeto.|  
|LAST_DDL_TIME|DateTime|Carimbo de hora para a última modificação do objeto de resultado de um comando DDL (incluindo as concessões e revoga).|  
|TIMESTAMP|Cadeia de Caracteres|Carimbo de hora para a especificação do objeto (dados de caractere).|  
|STATUS|Cadeia de Caracteres|Status do objeto (válido, inválido ou n/d).|  
|TEMPORÁRIO|Cadeia de Caracteres|Se o objeto é temporário (a sessão atual pode ver apenas os dados que foi colocada no próprio objeto).|  
|GERADO|Cadeia de Caracteres|É o nome do sistema objeto gerado? (Y &AMP;#124; N).|  
|SECUNDÁRIO|Cadeia de Caracteres|Se este é um objeto secundário criado pelo método ODCIIndexCreate de cartucho de dados Oracle9i (Y &#124; N).|  
|CRIADO|DateTime|A data em que o objeto foi criado.|  
  
## <a name="packagebodies"></a>PackageBodies  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|  
|OBJECT_NAME|Cadeia de Caracteres|Nome do objeto.|  
|SUBOBJECT_NAME|Cadeia de Caracteres|Nome do subobjeto (por exemplo, a partição).|  
|OBJECT_ID|Decimal|Número de objeto de dicionário do objeto.|  
|DATA_OBJECT_ID|Decimal|Número de objeto de dicionário do segmento que contém o objeto.|  
|LAST_DDL_TIME|DateTime|Carimbo de hora para a última modificação do objeto de resultado de um comando DDL (incluindo as concessões e revoga).|  
|TIMESTAMP|Cadeia de Caracteres|Carimbo de hora para a especificação do objeto (dados de caractere).|  
|STATUS|Cadeia de Caracteres|Status do objeto (válido, inválido ou n/d).|  
|TEMPORÁRIO|Cadeia de Caracteres|Se o objeto é temporário (a sessão atual pode ver apenas os dados que foi colocada no próprio objeto).|  
|GERADO|Cadeia de Caracteres|É o nome do sistema objeto gerado? (Y &AMP;#124; N).|  
|SECUNDÁRIO|Cadeia de Caracteres|Se este é um objeto secundário criado pelo método ODCIIndexCreate de cartucho de dados Oracle9i (Y &#124; N).|  
|CRIADO|DateTime|A data em que o objeto foi criado.|  
  
## <a name="arguments"></a>Arguments  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Nome do proprietário do objeto.|  
|PACKAGE_NAME|Cadeia de Caracteres|Nome do pacote.|  
|OBJECT_NAME|Cadeia de Caracteres|Nome do procedimento ou função.|  
|ARGUMENT_NAME|Cadeia de Caracteres|Nome do argumento.|  
|POSIÇÃO|Decimal|Posição na lista de argumentos, ou nulo para o valor de retorno da função.|  
|SEQUÊNCIA|Decimal|Sequência de argumento, incluindo todos os níveis de aninhamento.|  
|DEFAULT_VALUE|Cadeia de Caracteres|Valor padrão para o argumento.|  
|DEFAULT_LENGTH|Decimal|Comprimento do valor padrão para o argumento.|  
|IN_OUT|Cadeia de Caracteres|Direção do argumento (IN, OUT ou IN/OUT).|  
|DATA_LENGTH|Decimal|Comprimento da coluna em bytes.|  
|DATA_PRECISION|Decimal|Comprimento em decimal (número) ou binary dígitos (FLOAT).|  
|DATA_SCALE|Decimal|Dígitos à direita do ponto decimal em um número.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados do argumento.|  
  
## <a name="uniquekeys"></a>UniqueKeys  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da definição da restrição.|  
|CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição da restrição.|  
|TABLE_NAME|Cadeia de Caracteres|Nome do associado com a tabela (ou exibição) com definição de restrição.|  
|SEARCH_CONDITION|Cadeia de Caracteres|Texto do critério de pesquisa para uma restrição de verificação.|  
|R_OWNER|Cadeia de Caracteres|Proprietário da tabela referenciado em uma restrição referencial.|  
|R_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição exclusiva para a tabela referenciada.|  
|DELETE_RULE|Cadeia de Caracteres|Exclua a regra para uma restrição referencial (CASCADE ou nenhuma ação).|  
|STATUS|Cadeia de Caracteres|Status de imposição da restrição (habilitado ou desabilitado).|  
|ADIÁVEL|Cadeia de Caracteres|Se a restrição é Adiável.|  
|VALIDADO|Cadeia de Caracteres|Se todos os dados obedece a restrição (VALIDADO ou não VALIDADOS).|  
|GERADO|Cadeia de Caracteres|Se o nome da restrição é gerada pelo sistema ou usuário.|  
|INCORRETA|Cadeia de Caracteres|Um valor Sim indica que essa restrição Especifica um século de forma ambígua. Para evitar erros resultantes dessa ambiguidade, reescreva a restrição usando a função TO_DATE com um ano de quatro dígitos.|  
|CONFIAR|Cadeia de Caracteres|Se uma restrição habilitada é imposta ou não imposta.|  
|LAST_CHANGE|DateTime|Quando a restrição última foi habilitada ou desabilitada|  
|INDEX_OWNER|Cadeia de Caracteres|Nome do usuário que possui o índice|  
|INDEX_NAME|Cadeia de Caracteres|Nome do índice|  
  
## <a name="primarykeys"></a>PrimaryKeys  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da definição da restrição.|  
|CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição da restrição.|  
|TABLE_NAME|Cadeia de Caracteres|Nome do associado com a tabela (ou exibição) com definição de restrição.|  
|SEARCH_CONDITION|Cadeia de Caracteres|Texto do critério de pesquisa para uma restrição de verificação.|  
|R_OWNER|Cadeia de Caracteres|Proprietário da tabela referenciado em uma restrição referencial.|  
|R_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição exclusiva para a tabela referenciada.|  
|DELETE_RULE|Cadeia de Caracteres|Exclua a regra para uma restrição referencial (CASCADE ou nenhuma ação).|  
|STATUS|Cadeia de Caracteres|Status de imposição da restrição (habilitado ou desabilitado).|  
|ADIÁVEL|Cadeia de Caracteres|Se a restrição é Adiável.|  
|VALIDADO|Cadeia de Caracteres|Se todos os dados obedece a restrição (VALIDADO ou não VALIDADOS).|  
|GERADO|Cadeia de Caracteres|Se o nome da restrição é gerada pelo sistema ou usuário.|  
|INCORRETA|Cadeia de Caracteres|Um valor Sim indica que essa restrição Especifica um século de forma ambígua. Para evitar erros resultantes dessa ambiguidade, reescreva a restrição usando a função TO_DATE com um ano de quatro dígitos.|  
|CONFIAR|Cadeia de Caracteres|Se uma restrição habilitada é imposta ou não imposta.|  
|LAST_CHANGE|DateTime|Quando a restrição última foi habilitada ou desabilitada.|  
|INDEX_OWNER|Cadeia de Caracteres|Nome do usuário que possui o índice.|  
|INDEX_NAME|Cadeia de Caracteres|Nome do índice.|  
  
## <a name="foreignkeys"></a>Chaves externas  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PRIMARY_KEY_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição da restrição.|  
|PRIMARY_KEY_OWNER|Cadeia de Caracteres|Proprietário da definição da restrição.|  
|PRIMARY_KEY_TABLE_NAME|Cadeia de Caracteres|Nome do associado com a tabela (ou exibição) com definição de restrição|  
|FOREIGN_KEY_OWNER|Cadeia de Caracteres|Proprietário da definição da restrição.|  
|FOREIGN_KEY_CONSTRIANT_NAME|Cadeia de Caracteres|Nome da definição da restrição.|  
|FOREIGN_KEY_TABLE_NAME|Cadeia de Caracteres|Nome do associado com a tabela (ou exibição) com definição de restrição.|  
|SEARCH_CONDITION|Cadeia de Caracteres|Texto de condição de pesquisa para uma restrição de verificação|  
|R_OWNER|Cadeia de Caracteres|Proprietário da tabela referenciado em uma restrição referencial.|  
|R_CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição de restrição exclusiva para a tabela referenciada.|  
|DELETE_RULE|Cadeia de Caracteres|Exclua a regra para uma restrição referencial (CASCADE ou nenhuma ação).|  
|STATUS|Cadeia de Caracteres|Status de imposição da restrição (habilitado ou desabilitado).|  
|VALIDADO|Cadeia de Caracteres|Se todos os dados obedece a restrição (VALIDADO ou não VALIDADOS).|  
|GERADO|Cadeia de Caracteres|Se o nome da restrição é gerada pelo sistema ou usuário.|  
|CONFIAR|Cadeia de Caracteres|Se uma restrição habilitada é imposta ou não imposta.|  
|LAST_CHANGE|DateTime|Quando a restrição última foi habilitada ou desabilitada.|  
|INDEX_OWNER|Cadeia de Caracteres|Nome do usuário que possui o índice.|  
|INDEX_NAME|Cadeia de Caracteres|Nome do índice.|  
  
## <a name="foreignkeycolumns"></a>ForeignKeyColumns  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário da definição da restrição.|  
|CONSTRAINT_NAME|Cadeia de Caracteres|Nome da definição da restrição.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela com a definição de restrição.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna ou atributo da coluna de tipo de objeto especificado na definição da restrição.|  
|POSIÇÃO|Decimal|Posição original da coluna ou do atributo na definição do objeto.|  
  
## <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|PROPRIETÁRIO|Cadeia de Caracteres|Proprietário do objeto.|  
|OBJECT_NAME|Cadeia de Caracteres|Nome do procedimento ou função.|  
|PACKAGE_NAME|Cadeia de Caracteres|Nome do procedimento ou função.|  
|OBJECT_ID|Decimal|Número de objeto do objeto.|  
|SOBRECARGA|Cadeia de Caracteres|Identificador exclusivo da sobrecarga.|  
|ARGUMENT_NAME|Cadeia de Caracteres|Nome do argumento.|  
|POSIÇÃO|Decimal|Posição na lista de argumentos, ou null para um valor de retorno da função.|  
|SEQUÊNCIA|Decimal|Sequência de argumento, incluindo todos os níveis de aninhamento.|  
|DATA_LEVEL|Decimal|Profundidade do argumento de tipos compostos de aninhamento.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados do argumento.|  
|DEFAULT_VALUE|Cadeia de Caracteres|Valor padrão para o argumento.|  
|DEFAULT_LENGTH|Decimal|Comprimento do valor padrão para o argumento.|  
|IN_OUT|Cadeia de Caracteres|Direção do argumento (IN, OUT ou IN/OUT).|  
|DATA_LENGTH|Decimal|Comprimento da coluna (em bytes).|  
|DATA_PRECISION|Decimal|Comprimento em decimal (número) ou binary dígitos (FLOAT).|  
|DATA_SCALE|Decimal|Dígitos à direita da vírgula decimal em um número.|  
|BASE|Decimal|Base do argumento para um número.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Nome para o argumento do conjunto de caracteres.|  
|TYPE_OWNER|Cadeia de Caracteres|Proprietário do tipo do argumento.|  
|TYPE_NAME|Cadeia de Caracteres|Nome do tipo do argumento. Se o tipo for um tipo de local do pacote (isto é, ela é declarada em uma especificação de pacote), em seguida, essa coluna exibe o nome do pacote.|  
|TYPE_SUBNAME|Cadeia de Caracteres|Relevante apenas para tipos de local de pacote. Exibe o nome do tipo declarado no pacote identificado na coluna TYPE_NAME.|  
|TYPE_LINK|Cadeia de Caracteres|Relevante apenas para os tipos de local do pacote quando o pacote identificado na coluna TYPE_NAME é um pacote remoto. Esta coluna exibe o link do banco de dados usado para referenciar o pacote remoto.|  
|PLS_TYPE|Cadeia de Caracteres|Para todos os argumentos, o nome do tipo do argumento PL/SQL. Do contrário, nulo.|  
|CHAR_LENGTH|Decimal|Limite de caracteres para tipos de dados de cadeia de caracteres.|  
|CHAR_USED|Cadeia de Caracteres|Indica se o limite de bytes (B) ou char (C) é oficial para a cadeia de caracteres.|  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
