---
title: Coleções de esquema do SQL Server
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 0f65bbf2534eb7167baacb1405a8ce6e9769c23f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794327"
---
# <a name="sql-server-schema-collections"></a>Coleções de esquema do SQL Server
O Provedor de Dados do Microsoft .NET Framework para SQL Server dá suporte a coleções de esquema adicionais, além das coleções de esquema comuns. As coleções de esquema variam ligeiramente pela versão do SQL Server que você está usando. Para determinar a lista de coleções de esquema com suporte, chame o método **GetSchema** sem argumentos ou com o nome da coleção de esquema "MetaDataCollections". Isso retornará um <xref:System.Data.DataTable> com uma lista de coleções de esquema com suporte, o número de restrições às quais cada um deles oferece suporte e o número de partes de identificador que elas usam.  
  
## <a name="databases"></a>Bancos de dados  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|database_name|Cadeia de Caracteres|Nome do banco de dados.|  
|DBID|Int16|ID do banco de dados.|  
|create_date|DateTime|Data de criação do banco de dados.|  
  
## <a name="foreign-keys"></a>Chaves estrangeiras  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|Cadeia de Caracteres|Catalogar a restrição pertence a.|  
|CONSTRAINT_SCHEMA|Cadeia de Caracteres|Esquema que contém a restrição.|  
|CONSTRAINT_NAME|Cadeia de Caracteres|Nomes.|  
|TABLE_CATALOG|Cadeia de Caracteres|A restrição de nome de tabela faz parte de.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela|  
|CONSTRAINT_TYPE|Cadeia de Caracteres|Tipo de restrição. Somente a "chave estrangeira" é permitida.|  
|IS_DEFERRABLE|Cadeia de Caracteres|Especifica se a restrição é adiada. Retorna não.|  
|INITIALLY_DEFERRED|Cadeia de Caracteres|Especifica se a restrição é inicialmente adiada. Retorna não.|  
  
## <a name="indexes"></a>Índices  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|constraint_catalog|Cadeia de Caracteres|Catálogo ao qual o índice pertence.|  
|constraint_schema|Cadeia de Caracteres|Esquema que contém o índice.|  
|constraint_name|Cadeia de Caracteres|Nome do índice.|  
|table_catalog|Cadeia de Caracteres|Nome da tabela à qual o índice está associado.|  
|table_schema|Cadeia de Caracteres|Esquema que contém a tabela à qual o índice está associado.|  
|table_name|Cadeia de Caracteres|Nome da tabela.|  
|index_name|Cadeia de Caracteres|Nome do índice.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 A partir do .NET Framework versão 3,5 SP1 e SQL Server 2008, as colunas a seguir foram adicionadas à coleção de esquemas de índices para dar suporte a novos tipos espaciais, FileStream e colunas esparsas. Essas colunas não têm suporte em versões anteriores do .NET Framework e SQL Server.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|type_desc|Cadeia de Caracteres|O tipo do índice será um dos seguintes:<br /><br /> -HEAP<br />-CLUSTERIZADO<br />-   NONCLUSTERED<br />-   XML<br />-ESPACIAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|constraint_catalog|Cadeia de Caracteres|Catálogo ao qual o índice pertence.|  
|constraint_schema|Cadeia de Caracteres|Esquema que contém o índice.|  
|constraint_name|Cadeia de Caracteres|Nome do índice.|  
|table_catalog|Cadeia de Caracteres|Nome da tabela à qual o índice está associado.|  
|table_schema|Cadeia de Caracteres|Esquema que contém a tabela à qual o índice está associado.|  
|table_name|Cadeia de Caracteres|Nome da tabela.|  
|column_name|Cadeia de Caracteres|Nome da coluna à qual o índice está associado.|  
|ordinal_position|Int32|Posição ordinal da coluna.|  
|KeyType|Byte|O tipo de objeto.|  
|index_name|Cadeia de Caracteres|Nome do índice.|  
  
## <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Cadeia de Caracteres|Nome específico para o catálogo.|  
|SPECIFIC_SCHEMA|Cadeia de Caracteres|Nome específico do esquema.|  
|SPECIFIC_NAME|Cadeia de Caracteres|Nome específico do catálogo.|  
|ROUTINE_CATALOG|Cadeia de Caracteres|Catalogar o procedimento armazenado pertence a.|  
|ROUTINE_SCHEMA|Cadeia de Caracteres|Esquema que contém o procedimento armazenado.|  
|ROUTINE_NAME|Cadeia de Caracteres|Nome do procedimento armazenado.|  
|ROUTINE_TYPE|Cadeia de Caracteres|Retorna um procedimento para procedimentos armazenados e função para funções.|  
|CRIAÇÃO|DateTime|Hora em que o procedimento foi criado.|  
|LAST_ALTERED|DateTime|A última vez em que o procedimento foi modificado.|  
  
## <a name="procedure-parameters"></a>Parâmetros do procedimento  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Cadeia de Caracteres|Nome do catálogo do procedimento para o qual este é um parâmetro.|  
|SPECIFIC_SCHEMA|Cadeia de Caracteres|Esquema que contém o procedimento para o qual esse parâmetro faz parte.|  
|SPECIFIC_NAME|Cadeia de Caracteres|Nome do procedimento para o qual este parâmetro faz parte.|  
|ORDINAL_POSITION|Int32|Posição ordinal do parâmetro começando em 1. Para o valor de retorno de um procedimento, é 0.|  
|PARAMETER_MODE|Cadeia de Caracteres|Retorna em se um parâmetro de entrada, OUT se for um parâmetro de saída e INOUT, se um parâmetro de entrada/saída.|  
|IS_RESULT|Cadeia de Caracteres|Retorna YES se indica o resultado do procedimento que é uma função. Caso contrário, retornará não.|  
|AS_LOCATOR|Cadeia de Caracteres|Retorna Sim se declarado como localizador. Caso contrário, retornará não.|  
|PARAMETER_NAME|Cadeia de Caracteres|Nome do parâmetro. NULL se isso corresponder ao valor de retorno de uma função.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados fornecido pelo sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Comprimento máximo em caracteres para tipos de dados binários ou de caracteres. Caso contrário, retornará NULL.|  
|CHARACTER_OCTET_LENGTH|Int32|Comprimento máximo, em bytes, para tipos de dados binary ou Character. Caso contrário, retornará NULL.|  
|COLLATION_CATALOG|Cadeia de Caracteres|Nome do catálogo do agrupamento do parâmetro. Se não for um dos tipos de caracteres, retornará NULL.|  
|COLLATION_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|COLLATION_NAME|Cadeia de Caracteres|Nome do agrupamento do parâmetro. Se não for um dos tipos de caracteres, retornará NULL.|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|Nome do catálogo do conjunto de caracteres do parâmetro. Se não for um dos tipos de caracteres, retornará NULL.|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Nome do conjunto de caracteres do parâmetro. Se não for um dos tipos de caracteres, retornará NULL.|  
|NUMERIC_PRECISION|Byte|Precisão dos dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, retornará NULL.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de precisão de dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, retornará NULL.|  
|NUMERIC_SCALE|Int32|Escala de dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, retornará NULL.|  
|DATETIME_PRECISION|Int16|Precisão em segundos fracionários se o tipo de parâmetro for DateTime ou smalldatetime. Caso contrário, retornará NULL.|  
|INTERVAL_TYPE|Cadeia de Caracteres|NULO. Reservado para uso futuro por SQL Server.|  
|INTERVAL_PRECISION|Int16|NULO. Reservado para uso futuro por SQL Server.|  
  
## <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|TABLE_TYPE|Cadeia de Caracteres|Tipo de tabela. Pode ser exibição ou tabela BASE.|  
  
## <a name="columns"></a>Colunas  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
|ORDINAL_POSITION|Int32|Número de identificação da coluna.|  
|COLUMN_DEFAULT|Cadeia de Caracteres|Valor padrão da coluna|  
|IS_NULLABLE|Cadeia de Caracteres|Nulidade da coluna. Se essa coluna permitir NULL, essa coluna retornará Sim. Caso contrário, não será retornado.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados fornecido pelo sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|Comprimento máximo, em caracteres, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|Comprimento máximo, em bytes, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION|Byte não assinado|Precisão dos dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de precisão de dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_SCALE|Int32|Escala de dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|DATETIME_PRECISION|Int16|Código de subtipo para tipos de dados DateTime e SQL-92 Interval. Para outros tipos de dados, NULL é retornado.|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|Retorna Master, indicando o banco de dados no qual o conjunto de caracteres está localizado, se a coluna é de dados de caracteres ou de texto. Caso contrário, NULL será retornado.|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Retorna o nome exclusivo para o conjunto de caracteres se esta coluna for de dados de caracteres ou tipo de dados de texto. Caso contrário, NULL será retornado.|  
|COLLATION_CATALOG|Cadeia de Caracteres|Retorna Master, indicando o banco de dados no qual o agrupamento é definido, se a coluna é de dados de caractere ou de texto. Caso contrário, essa coluna será nula.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 A partir do .NET Framework versão 3,5 SP1 e SQL Server 2008, as colunas a seguir foram adicionadas à coleção de esquemas de colunas para dar suporte a novos tipos espaciais, FileStream e colunas esparsas. Essas colunas não têm suporte em versões anteriores do .NET Framework e SQL Server.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|Cadeia de Caracteres|Sim se a coluna tiver o atributo FILESTREAM.<br /><br /> Não se a coluna não tiver o atributo FILESTREAM.|  
|IS_SPARSE|Cadeia de Caracteres|Sim se a coluna for uma coluna esparsa.<br /><br /> Não se a coluna não for uma coluna esparsa.|  
|IS_COLUMN_SET|Cadeia de Caracteres|Sim se a coluna for uma coluna de conjunto de colunas.<br /><br /> Não se a coluna não for uma coluna de conjunto de colunas.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 A partir do .NET Framework versão 3,5 SP1 e SQL Server 2008, a coleção de esquemas das colunas foi adicionada para dar suporte a colunas esparsas. Não há suporte para as colunas em versões anteriores do .NET Framework e SQL Server.  
  
 As colunas têm as mesmas restrições e o esquema DataTable resultante como a coleção de esquemas Columns. A única diferença é que as colunas incluem colunas de conjunto de colunas que não estão incluídas na coleção de esquemas de colunas. A tabela a seguir descreve essas colunas.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
|ORDINAL_POSITION|Int32|Número de identificação da coluna.|  
|COLUMN_DEFAULT|Cadeia de Caracteres|Valor padrão da coluna|  
|IS_NULLABLE|Cadeia de Caracteres|Nulidade da coluna. Se essa coluna permitir NULL, essa coluna retornará Sim. Caso contrário, não será retornado.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados fornecido pelo sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Comprimento máximo, em caracteres, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|CHARACTER_OCTET_LENGTH|Int32|Comprimento máximo, em bytes, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION|Byte não assinado|Precisão dos dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de precisão de dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_SCALE|Int32|Escala de dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|DATETIME_PRECISION|Int16|Código de subtipo para tipos de dados DateTime e SQL-92 Interval. Para outros tipos de dados, NULL é retornado.|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|Retorna Master, indicando o banco de dados no qual o conjunto de caracteres está localizado, se a coluna é de dados de caracteres ou de texto. Caso contrário, NULL será retornado.|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Retorna o nome exclusivo para o conjunto de caracteres se esta coluna for de dados de caracteres ou tipo de dados de texto. Caso contrário, NULL será retornado.|  
|COLLATION_CATALOG|Cadeia de Caracteres|Retorna Master, indicando o banco de dados no qual o agrupamento é definido, se a coluna é de dados de caractere ou de texto. Caso contrário, essa coluna será nula.|  
|IS_FILESTREAM|Cadeia de Caracteres|Sim se a coluna tiver o atributo FILESTREAM.<br /><br /> Não se a coluna não tiver o atributo FILESTREAM.|  
|IS_SPARSE|Cadeia de Caracteres|Sim se a coluna for uma coluna esparsa.<br /><br /> Não se a coluna não for uma coluna esparsa.|  
|IS_COLUMN_SET|Cadeia de Caracteres|Sim se a coluna for uma coluna de conjunto de colunas.<br /><br /> Não se a coluna não for uma coluna de conjunto de colunas.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 A partir do .NET Framework versão 3,5 SP1 e SQL Server 2008, a coleção de esquemas ColumnSetColumns foi adicionada para dar suporte a colunas esparsas. Não há suporte para ColumnSetColumns em versões anteriores do .NET Framework e SQL Server. A coleção de esquema ColumnSetColumns retorna o esquema para todas as colunas em um conjunto de colunas. A tabela a seguir descreve essas colunas.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
|ORDINAL_POSITION|Int32|Número de identificação da coluna.|  
|COLUMN_DEFAULT|Cadeia de Caracteres|Valor padrão da coluna|  
|IS_NULLABLE|Cadeia de Caracteres|Nulidade da coluna. Se essa coluna permitir NULL, essa coluna retornará Sim. Caso contrário, não será retornado.|  
|DATA_TYPE|Cadeia de Caracteres|Tipo de dados fornecido pelo sistema.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|Comprimento máximo, em caracteres, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|CHARACTER_OCTET_LENGTH|Int32|Comprimento máximo, em bytes, para dados binários, dados de caractere ou dados de texto e imagem. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION|Byte não assinado|Precisão dos dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_PRECISION_RADIX|Int16|Base de precisão de dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|NUMERIC_SCALE|Int32|Escala de dados numéricos aproximados, dados numéricos exatos, dados inteiros ou dados monetários. Caso contrário, NULL será retornado.|  
|DATETIME_PRECISION|Int16|Código de subtipo para tipos de dados DateTime e SQL-92 Interval. Para outros tipos de dados, NULL é retornado.|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|Retorna Master, indicando o banco de dados no qual o conjunto de caracteres está localizado, se a coluna é de dados de caracteres ou de texto. Caso contrário, NULL será retornado.|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|Sempre retorna NULL.|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|Retorna o nome exclusivo para o conjunto de caracteres se esta coluna for de dados de caracteres ou tipo de dados de texto. Caso contrário, NULL será retornado.|  
|COLLATION_CATALOG|Cadeia de Caracteres|Retorna Master, indicando o banco de dados no qual o agrupamento é definido, se a coluna é de dados de caractere ou de texto. Caso contrário, essa coluna será nula.|  
|IS_FILESTREAM|Cadeia de Caracteres|Sim se a coluna tiver o atributo FILESTREAM.<br /><br /> Não se a coluna não tiver o atributo FILESTREAM.|  
|IS_SPARSE|Cadeia de Caracteres|Sim se a coluna for uma coluna esparsa.<br /><br /> Não se a coluna não for uma coluna esparsa.|  
|IS_COLUMN_SET|Cadeia de Caracteres|Sim se a coluna for uma coluna de conjunto de colunas.<br /><br /> Não se a coluna não for uma coluna de conjunto de colunas.|  
  
## <a name="users"></a>Usuários  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|UID|Int16|ID de usuário, exclusiva neste banco de dados. 1 é o proprietário do banco de dados.|  
|user_name|Cadeia de Caracteres|Nome de usuário ou grupo, exclusivo neste banco de dados.|  
|CreateDate|DateTime|Data em que a conta foi adicionada.|  
|updateDate|DateTime|Data em que a conta foi alterada pela última vez.|  
  
## <a name="views"></a>Exibições  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da exibição.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a exibição.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da exibição.|  
|CHECK_OPTION|Cadeia de Caracteres|Tipo de com opção de verificação. Será em cascata se a exibição original tiver sido criada usando a opção WITH CHECK. Caso contrário, nenhum será retornado.|  
|IS_UPDATABLE|Cadeia de Caracteres|Especifica se a exibição é atualizável. Sempre retorna não.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|Cadeia de Caracteres|Catálogo da exibição.|  
|VIEW_SCHEMA|Cadeia de Caracteres|Esquema que contém a exibição.|  
|VIEW_NAME|Cadeia de Caracteres|Nome da exibição.|  
|TABLE_CATALOG|Cadeia de Caracteres|Catálogo da tabela que está associada a esta exibição.|  
|TABLE_SCHEMA|Cadeia de Caracteres|Esquema que contém a tabela associada a esta exibição.|  
|TABLE_NAME|Cadeia de Caracteres|Nome da tabela associada à exibição. Tabela base.|  
|COLUMN_NAME|Cadeia de Caracteres|Nome da coluna.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|assembly_name|Cadeia de Caracteres|O nome do arquivo para o assembly.|  
|udt_name|Cadeia de Caracteres|O nome da classe para o assembly.|  
|version_major|Object|Número de versão principal.|  
|version_minor|Object|Número de versão secundário.|  
|version_build|Object|Número da compilação.|  
|version_revision|Object|Número de revisão.|  
|culture_info|Object|As informações de cultura associadas a esse UDT.|  
|public_key|Object|A chave pública usada por este assembly.|  
|is_fixed_length|Boolean|Especifica se o comprimento do tipo é sempre o mesmo que max_length.|  
|max_length|Int16|Comprimento máximo do tipo em bytes.|  
|Create_Date|DateTime|A data em que o assembly foi criado/registrado.|  
|Permission_set_desc|Cadeia de Caracteres|O nome amigável para o conjunto de permissões/nível de segurança do assembly.|  
  
## <a name="see-also"></a>Consulte também

- [Recuperando informações de esquema de banco de dados](retrieving-database-schema-information.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
