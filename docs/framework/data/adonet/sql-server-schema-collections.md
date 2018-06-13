---
title: Coleções de esquema do SQL Server
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 248e5f4caf47f09742358240fa43f46169f0b1e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361049"
---
# <a name="sql-server-schema-collections"></a>Coleções de esquema do SQL Server
O Microsoft .NET Framework Data Provider para SQL Server dá suporte a coleções de esquema adicionais além das coleções de esquema comuns. As coleções de esquema variam ligeiramente conforme a versão do SQL Server que você está usando. Para determinar a lista de coleções de esquema com suporte, chame o **GetSchema** método sem argumentos, ou com o nome da coleção de esquema "MetaDataCollections". Isso retornará um <xref:System.Data.DataTable> com uma lista de coleções de esquema com suporte, o número de restrições que oferecem suporte a cada um deles e o número de partes do identificador que eles usam.  
  
## <a name="databases"></a>Bancos de dados  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|Database_Name|Cadeia de Caracteres|Nome do banco de dados.|  
|DBID|Int16|ID do banco de dados.|  
|create_date|DateTime|Data de criação do banco de dados.|  
  
## <a name="foreign-keys"></a>Chaves estrangeiras  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|Cadeia de Caracteres|A restrição de catálogo ao qual pertence.|  
|CONSTRAINT_SCHEMA|Cadeia de Caracteres|Esquema que contém a restrição.|  
|CONSTRAINT_NAME|Cadeia de Caracteres|Nome.|  
|TABLE_CATALOG|Cadeia de Caracteres|Restrição de nome de tabela faz parte do.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela|  
|CONSTRAINT_TYPE|Cadeia de Caracteres|Tipo de restrição. É permitido apenas "FOREIGN KEY".|  
|IS_DEFERRABLE|Cadeia de Caracteres|Especifica se a restrição é Adiável. Não retorna.|  
|INITIALLY_DEFERRED|Cadeia de Caracteres|Especifica se a restrição é Adiável inicialmente. Não retorna.|  
  
## <a name="indexes"></a>Índices  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|constraint_catalog|Cadeia de Caracteres|Catálogo que índice pertence.|  
|constraint_schema|Cadeia de Caracteres|Esquema que contém o índice.|  
|constraint_name|Cadeia de Caracteres|Nome do índice.|  
|table_catalog|Cadeia de Caracteres|Nome da tabela de índice está associado.|  
|table_schema|Cadeia de Caracteres|Esquema que contém a tabela de índice está associado.|  
|table_name|Cadeia de Caracteres|Nome da tabela.|  
|index_name|Cadeia de Caracteres|Nome do índice.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 Começando com o .NET Framework versão 3.5 SP1 e o SQL Server 2008, as colunas a seguir foram adicionadas à coleção de esquema de índices para dar suporte a novos tipos espaciais, filestream e as colunas esparsas. Essas colunas não têm suporte em versões anteriores do .NET Framework e do SQL Server.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|type_desc|Cadeia de Caracteres|O tipo do índice será um dos seguintes:<br /><br /> -HEAP<br />-CLUSTERIZADO<br />-NÃO CLUSTERIZADO<br />-   XML<br />-ESPACIAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|constraint_catalog|Cadeia de Caracteres|Catálogo que índice pertence.|  
|constraint_schema|Cadeia de Caracteres|Esquema que contém o índice.|  
|constraint_name|Cadeia de Caracteres|Nome do índice.|  
|table_catalog|Cadeia de Caracteres|Nome da tabela de índice está associado.|  
|table_schema|Cadeia de Caracteres|Esquema que contém a tabela de índice está associado.|  
|table_name|Cadeia de Caracteres|Nome da tabela.|  
|nome da coluna|Cadeia de Caracteres|Nome da coluna de índice está associado.|  
|ordinal_position|Int32|Posição ordinal da coluna.|  
|KeyType|Byte|O tipo de objeto.|  
|index_name|Cadeia de Caracteres|Nome do índice.|  
  
## <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Cadeia de Caracteres|Nome específico para o catálogo.|  
|SPECIFIC_SCHEMA|Cadeia de Caracteres|Nome específico do esquema.|  
|SPECIFIC_NAME|Cadeia de Caracteres|Nome específico do catálogo.|  
|ROUTINE_CATALOG|Cadeia de Caracteres|O procedimento armazenado catálogo ao qual pertence.|  
|ROUTINE_SCHEMA|Cadeia de Caracteres|Esquema que contém o procedimento armazenado.|  
|ROUTINE_NAME|Cadeia de Caracteres|Nome do procedimento armazenado.|  
|ROUTINE_TYPE|Cadeia de Caracteres|Retorna o procedimento para procedimentos armazenados e FUNCTION para funções.|  
|CRIADO|DateTime|Hora que da criação do procedimento.|  
|LAST_ALTERED|DateTime|A última vez em que o procedimento foi modificado.|  
  
## <a name="procedure-parameters"></a>Parâmetros de procedimento  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Cadeia de Caracteres|Nome do procedimento para o qual este é um parâmetro do catálogo.|  
|SPECIFIC_SCHEMA|Cadeia de Caracteres|Esquema que contém o procedimento para o qual esse parâmetro faz parte do.|  
|SPECIFIC_NAME|Cadeia de Caracteres|Nome do procedimento para o qual esse parâmetro faz parte.|  
|ORDINAL_POSITION|Int32|Posição ordinal do parâmetro começando em 1. O valor de retorno de um procedimento, este é um 0.|  
|PARAMETER_MODE|Cadeia de Caracteres|Retorna se um parâmetro de entrada, se um parâmetro de saída e INOUT se um parâmetro de entrada/saída.|  
|IS_RESULT|Cadeia de Caracteres|Retorna YES se indica o resultado do procedimento que é uma função. Caso contrário, retornará não.|  
|AS_LOCATOR|Cadeia de Caracteres|Retorna YES se declarado como localizador. Caso contrário, retornará não.|  
|PARAMETER_NAME|Cadeia de Caracteres|Nome do parâmetro. NULL se isso corresponde ao valor de retorno de uma função.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados fornecido pelo sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Comprimento máximo em caracteres para tipos de dados de caractere ou binário. Caso contrário, retornará NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Comprimento máximo, em bytes, para tipos de dados de caractere ou binário. Caso contrário, retornará NULL.|  
|COLLATION_CATALOG|Cadeia de Caracteres|Nome do agrupamento do parâmetro do catálogo. Se não for um dos tipos de caractere, retorna NULL.|  
|COLLATION_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|COLLATION_NAME|Cadeia de Caracteres|Nome do agrupamento do parâmetro. Se não for um dos tipos de caractere, retorna NULL.|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|Nome do conjunto de caracteres do parâmetro do catálogo. Se não for um dos tipos de caractere, retorna NULL.|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Nome do conjunto de caracteres do parâmetro. Se não for um dos tipos de caractere, retorna NULL.|  
|NUMERIC_PRECISION|Byte|Precisão de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários. Caso contrário, retornará NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários precisão. Caso contrário, retornará NULL.|  
|NUMERIC_SCALE|Int32|Escala de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários. Caso contrário, retornará NULL.|  
|DATETIME_PRECISION|Int16|Precisão em segundos fracionários se o tipo de parâmetro for datetime ou smalldatetime. Caso contrário, retornará NULL.|  
|INTERVAL_TYPE|Cadeia de Caracteres|NULL. Reservado para uso futuro pelo SQL Server.|  
|INTERVAL_PRECISION|Int16|NULL. Reservado para uso futuro pelo SQL Server.|  
  
## <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|TABLE_TYPE|Cadeia de Caracteres|Tipo de tabela. Pode ser a exibição ou tabela BASE.|  
  
## <a name="columns"></a>Colunas  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
|ORDINAL_POSITION|Int32|Número de identificação de coluna.|  
|COLUMN_DEFAULT|Cadeia de Caracteres|Valor padrão da coluna|  
|IS_NULLABLE|Cadeia de Caracteres|Nulidade da coluna. Se essa coluna permitir NULL, essa coluna retornará YES. Caso contrário, não será retornado.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados fornecido pelo sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|Comprimento máximo em caracteres para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Comprimento máximo, em bytes, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION|Byte não atribuído|Precisão de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários precisão. Caso contrário, NULL será retornado.|  
|NUMERIC_SCALE|Int32|Escala de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários. Caso contrário, NULL será retornado.|  
|DATETIME_PRECISION|Int16|Código de subtipo para tipos de dados de intervalo de SQL-92 e datetime. Para outros tipos de dados, NULL será retornado.|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|Mestre retorna, indicando o banco de dados no qual o conjunto de caracteres, se a coluna de dados de caractere ou dados de texto tipo. Caso contrário, NULL será retornado.|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Retorna o nome exclusivo para o caractere definido se essa coluna for dados de texto ou dados de caractere de tipo. Caso contrário, NULL será retornado.|  
|COLLATION_CATALOG|Cadeia de Caracteres|Mestre retorna, indicando o banco de dados no qual o agrupamento é definido, se a coluna de dados de caractere ou dados de texto tipo. Caso contrário, essa coluna é NULL.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 Começando com o .NET Framework versão 3.5 SP1 e o SQL Server 2008, as colunas a seguir foram adicionadas à coleção de esquema de colunas para dar suporte a novos tipos espaciais, filestream e as colunas esparsas. Essas colunas não têm suporte em versões anteriores do .NET Framework e do SQL Server.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|Cadeia de Caracteres|Sim, se a coluna tiver o atributo FILESTREAM.<br /><br /> NÃO se a coluna não tem o atributo FILESTREAM.|  
|IS_SPARSE|Cadeia de Caracteres|Sim, se a coluna é uma coluna esparsa.<br /><br /> NÃO se a coluna não é uma coluna esparsa.|  
|IS_COLUMN_SET|Cadeia de Caracteres|Sim se a coluna é uma coluna do conjunto de colunas.<br /><br /> NÃO se a coluna não é uma coluna do conjunto de colunas.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 Começando com o .NET Framework versão 3.5 SP1 e o SQL Server 2008, a coleção de esquema AllColumns foi adicionada para oferecer suporte a colunas esparsas. Não há suporte para AllColumns em versões anteriores do .NET Framework e do SQL Server.  
  
 AllColumns tem as mesmas restrições e esquema de DataTable resultante como a coleção de esquema de colunas. A única diferença é que AllColumns inclui colunas do conjunto de colunas que não estão incluídas na coleção de esquema Columns. A tabela a seguir descreve essas colunas.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
|ORDINAL_POSITION|Int32|Número de identificação de coluna.|  
|COLUMN_DEFAULT|Cadeia de Caracteres|Valor padrão da coluna|  
|IS_NULLABLE|Cadeia de Caracteres|Nulidade da coluna. Se essa coluna permitir NULL, essa coluna retornará YES. Caso contrário, não será retornado.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados fornecido pelo sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Comprimento máximo em caracteres para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|CHARACTER_OCTET_LENGTH|Int32|Comprimento máximo, em bytes, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION|Byte não atribuído|Precisão de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários precisão. Caso contrário, NULL será retornado.|  
|NUMERIC_SCALE|Int32|Escala de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários. Caso contrário, NULL será retornado.|  
|DATETIME_PRECISION|Int16|Código de subtipo para tipos de dados de intervalo de SQL-92 e datetime. Para outros tipos de dados, NULL será retornado.|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|Mestre retorna, indicando o banco de dados no qual o conjunto de caracteres, se a coluna de dados de caractere ou dados de texto tipo. Caso contrário, NULL será retornado.|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Retorna o nome exclusivo para o caractere definido se essa coluna for dados de texto ou dados de caractere de tipo. Caso contrário, NULL será retornado.|  
|COLLATION_CATALOG|Cadeia de Caracteres|Mestre retorna, indicando o banco de dados no qual o agrupamento é definido, se a coluna de dados de caractere ou dados de texto tipo. Caso contrário, essa coluna é NULL.|  
|IS_FILESTREAM|Cadeia de Caracteres|Sim, se a coluna tiver o atributo FILESTREAM.<br /><br /> NÃO se a coluna não tem o atributo FILESTREAM.|  
|IS_SPARSE|Cadeia de Caracteres|Sim, se a coluna é uma coluna esparsa.<br /><br /> NÃO se a coluna não é uma coluna esparsa.|  
|IS_COLUMN_SET|Cadeia de Caracteres|Sim se a coluna é uma coluna do conjunto de colunas.<br /><br /> NÃO se a coluna não é uma coluna do conjunto de colunas.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 Começando com o .NET Framework versão 3.5 SP1 e o SQL Server 2008, a coleção de esquema ColumnSetColumns foi adicionada para oferecer suporte a colunas esparsas. Não há suporte para ColumnSetColumns em versões anteriores do .NET Framework e do SQL Server. A coleção de esquema ColumnSetColumns retorna o esquema para todas as colunas em um conjunto de colunas. A tabela a seguir descreve essas colunas.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
|ORDINAL_POSITION|Int32|Número de identificação de coluna.|  
|COLUMN_DEFAULT|Cadeia de Caracteres|Valor padrão da coluna|  
|IS_NULLABLE|Cadeia de Caracteres|Nulidade da coluna. Se essa coluna permitir NULL, essa coluna retornará YES. Caso contrário, não será retornado.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados fornecido pelo sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Comprimento máximo em caracteres para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|CHARACTER_OCTET_LENGTH|Int32|Comprimento máximo, em bytes, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION|Byte não atribuído|Precisão de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários precisão. Caso contrário, NULL será retornado.|  
|NUMERIC_SCALE|Int32|Escala de dados numéricos aproximados, dados numéricos exatos, dados de número inteiro ou dados monetários. Caso contrário, NULL será retornado.|  
|DATETIME_PRECISION|Int16|Código de subtipo para tipos de dados de intervalo de SQL-92 e datetime. Para outros tipos de dados, NULL será retornado.|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|Mestre retorna, indicando o banco de dados no qual o conjunto de caracteres, se a coluna de dados de caractere ou dados de texto tipo. Caso contrário, NULL será retornado.|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Retorna o nome exclusivo para o caractere definido se essa coluna for dados de texto ou dados de caractere de tipo. Caso contrário, NULL será retornado.|  
|COLLATION_CATALOG|Cadeia de Caracteres|Mestre retorna, indicando o banco de dados no qual o agrupamento é definido, se a coluna de dados de caractere ou dados de texto tipo. Caso contrário, essa coluna é NULL.|  
|IS_FILESTREAM|Cadeia de Caracteres|Sim, se a coluna tiver o atributo FILESTREAM.<br /><br /> NÃO se a coluna não tem o atributo FILESTREAM.|  
|IS_SPARSE|Cadeia de Caracteres|Sim, se a coluna é uma coluna esparsa.<br /><br /> NÃO se a coluna não é uma coluna esparsa.|  
|IS_COLUMN_SET|Cadeia de Caracteres|Sim se a coluna é uma coluna do conjunto de colunas.<br /><br /> NÃO se a coluna não é uma coluna do conjunto de colunas.|  
  
## <a name="users"></a>Usuários  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|UID|Int16|ID de usuário, exclusivo neste banco de dados. 1 é o proprietário do banco de dados.|  
|user_name|Cadeia de Caracteres|Nome de usuário ou grupo de nome, exclusivo neste banco de dados.|  
|CREATEDATE formato|DateTime|Data em que a conta foi adicionada.|  
|updatedate|DateTime|Data em que a conta foi alterado pela última vez.|  
  
## <a name="views"></a>Exibições  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo do modo de exibição.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a exibição.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da exibição.|  
|CHECK_OPTION|Cadeia de Caracteres|Tipo de WITH CHECK OPTION. Será CASCADE se a exibição original foi criada com WITH CHECK OPTION. Caso contrário, nenhum é retornado.|  
|IS_UPDATABLE|Cadeia de Caracteres|Especifica se a exibição é atualizável. Sempre retorna não.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|Cadeia de Caracteres|Catálogo do modo de exibição.|  
|VIEW_SCHEMA|Cadeia de Caracteres|Esquema que contém a exibição.|  
|VIEW_NAME|Cadeia de Caracteres|Nome da exibição.|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela que está associado este modo de exibição.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela que está associada este modo de exibição.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela que está associada com o modo de exibição. Tabela base.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|assembly_name|Cadeia de Caracteres|O nome do arquivo do assembly.|  
|udt_name|Cadeia de Caracteres|O nome da classe do assembly.|  
|version_major|Objeto|Número de versão principal.|  
|version_minor|Objeto|Número de versão secundária.|  
|versão compilação|Objeto|Número de compilação.|  
|version_revision|Objeto|Número de revisão.|  
|culture_info|Objeto|As informações de cultura associadas a este tipo.|  
|public_key|Objeto|A chave pública usada por este Assembly.|  
|is_fixed_length|Boolean|Especifica se o comprimento do tipo é sempre o mesmo que max_length.|  
|max_length|Int16|Comprimento máximo do tipo em bytes.|  
|Create_Date|DateTime|A data em que o assembly foi criado/registrado.|  
|Permission_set_desc|Cadeia de Caracteres|O nome amigável para o permissão-conjunto/nível de segurança para o assembly.|  
  
## <a name="see-also"></a>Consulte também  
 [Recuperando informações de esquema de banco de dados](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
