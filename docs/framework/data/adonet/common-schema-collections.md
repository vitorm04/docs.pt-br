---
title: "Coleções de esquema comuns"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 19a95cf5d8d9b5fc5f805574b6de15c90fb38efd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="common-schema-collections"></a>Coleções de esquema comuns
As coleções de esquema comum são as coleções de esquemas que são implementadas por cada um dos provedores gerenciados do .NET Framework. Você pode consultar um provedor gerenciado do .NET Framework para determinar a lista de coleções de esquema com suporte ao chamar o **GetSchema** método sem argumentos, ou com o nome da coleção de esquema "MetaDataCollections". Isso retornará um <xref:System.Data.DataTable> com uma lista de coleções de esquema com suporte, o número de restrições que oferecem suporte a cada um deles e o número de partes do identificador que eles usam. Essas coleções descrevem todas as colunas necessárias. Provedores serão livres para adicionar colunas adicionais, se desejarem. Por exemplo, `SqlClient` e `OracleClient` adicionar o nome do parâmetro na coleção de restrições.  
  
 Se um provedor é incapaz de determinar o valor de uma coluna necessária, ela retornará nulo.  
  
 Para obter mais informações sobre como usar o **GetSchema** métodos, consulte [GetSchema e coleções de esquema](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Esta coleção de esquema expõe informações sobre todas as coleções de esquema com suporte do provedor gerenciado do .NET Framework que está sendo usado para conectar-se ao banco de dados.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|CollectionName|cadeia de caracteres|O nome da coleção para passar para o **GetSchema** método para retornar a coleção.|  
|NumberOfRestrictions|int|O número de restrições que podem ser especificadas para a coleção.|  
|NumberOfIdentifierParts|int|O número de partes no nome do objeto de identificador/banco de dados compostos. Por exemplo, no SQL Server, isso seria 3 para tabelas e 4 para colunas. No Oracle, ele seria 2 para tabelas e 3 para colunas.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Esta coleção de esquema expõe informações sobre a fonte de dados que o .NET Framework provedor gerenciado está se conectem.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|cadeia de caracteres|A expressão regular para corresponder os separadores de composição em um identificador composto. Por exemplo, "\\." (para o SQL Server) ou "@&#124; \\." (para Oracle).<br /><br /> Um identificador composto normalmente é o que é usado para um nome de objeto de banco de dados, por exemplo: pubs.dbo.authors ou pubs@dbo.authors.<br /><br /> Para o SQL Server, use a expressão regular "\\.". Para OracleClient, use "@&#124; \\.".<br /><br /> Para usar o Catalog_name_seperator do ODBC.<br /><br /> Para OLE DB, use DBLITERAL_CATALOG_SEPARATOR ou DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|cadeia de caracteres|O nome do produto acessado pelo provedor, como "Oracle" ou "SQLServer".|  
|DataSourceProductVersion|cadeia de caracteres|Indica a versão do produto acessado pelo provedor, no formato nativo de fontes de dados e não está no formato de Microsoft.<br /><br /> Em alguns casos DataSourceProductVersion e DataSourceProductVersionNormalized será o mesmo valor. No caso de OLE DB e ODBC, eles sempre será o mesmo conforme eles são mapeados para a mesma chamada de função na API nativa subjacente.|  
|DataSourceProductVersionNormalized|cadeia de caracteres|Uma versão normalizada para os dados de origem, que pode ser comparado com `String.Compare()`. O formato deste é consistente para todas as versões do provedor para impedir que a versão 10 classificação entre a versão 1 e 2.<br /><br /> Por exemplo, o provedor Oracle usa um formato de "nn.nn.nn.nn.nn" para sua versão normalizada, o que faz com que uma fonte de dados do Oracle 8i retornar "08.01.07.04.01". SQL Server usa o formato típico de "nn.nn.nnnn" Microsoft.<br /><br /> Em alguns casos, DataSourceProductVersion e DataSourceProductVersionNormalized será o mesmo valor. No caso de OLE DB e ODBC esses sempre será o mesmo como eles são mapeados para a mesma chamada de função na API nativa subjacente.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Especifica a relação entre as colunas em uma cláusula GROUP BY e as colunas não agregadas na lista de seleção.|  
|IdentifierPattern|cadeia de caracteres|Uma expressão regular que corresponde a um identificador e tem um valor de correspondência do identificador. Por exemplo, "[A-Za-z0-9 _ #$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Indica se os identificadores entre aspas não são tratados como maiusculas e minúsculas ou não.|  
|OrderByColumnsInSelect|bool|Especifica se as colunas em uma cláusula ORDER BY devem estar na lista de seleção. Um valor true indica que eles devem estar na lista de seleção, um valor false indica que eles não precisam estar na lista de seleção.|  
|ParameterMarkerFormat|cadeia de caracteres|Uma cadeia de caracteres de formato representa como formatar um parâmetro.<br /><br /> Se a fonte de dados oferece suporte a parâmetros nomeados, o primeiro espaço reservado na cadeia de caracteres deve ser onde o nome do parâmetro deve ser formatado.<br /><br /> Por exemplo, se a fonte de dados espera parâmetros nomeado e prefixado com um ':' deve ser ": {0}". Ao formatar isso com um nome de parâmetro "P1" resultante é cadeia de caracteres ": p1".<br /><br /> Se a fonte de dados espera parâmetros para ser prefixados com o ' @', mas os nomes já incluírem-los, deve ser '{0}' e o resultado da formatação de um parâmetro denominado "@p1"poderia ser simplesmente"@p1".<br /><br /> Para fontes de dados que não espera parâmetros nomeados e esperar que o uso do '?' caracteres, a cadeia de caracteres de formato pode ser especificada simplesmente '?', que deve ignorar o nome do parâmetro. Para OLE DB retornamos '?'.|  
|ParameterMarkerPattern|cadeia de caracteres|Uma expressão regular que corresponda a um marcador de parâmetro. Ele tem um valor de correspondência do nome do parâmetro, se houver.<br /><br /> Por exemplo, se os parâmetros nomeados são compatíveis com um ' @' caracteres iniciais que serão incluído no nome do parâmetro, isso seria: "(@[A-Za-z0-9 _ $#] *)".<br /><br /> No entanto, se os parâmetros nomeados são compatíveis com um ':' como o caractere de apresentação e não é parte do nome do parâmetro, isso seria: ": ([A-Za-z0-9 _ $#]\*)".<br /><br /> É claro que, se a fonte de dados não dá suporte a parâmetros nomeados, isso seria apenas "?".|  
|ParameterNameMaxLength|int|O comprimento máximo de um nome de parâmetro em caracteres. O Visual Studio espera que se há suporte para nomes de parâmetro, o valor mínimo para o tamanho máximo é de 30 caracteres.<br /><br /> Se a fonte de dados não dá suporte a parâmetros nomeados, essa propriedade retornará zero.|  
|ParameterNamePattern|cadeia de caracteres|Uma expressão regular compatível com os nomes de parâmetro válido. Fontes de dados diferentes têm diferentes regras relativas ao uso de caracteres que podem ser usados para nomes de parâmetro.<br /><br /> O Visual Studio espera se há suporte para nomes de parâmetro, os caracteres "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" são o conjunto com suporte mínimo de caracteres que são válidos para nomes de parâmetro.|  
|QuotedIdentifierPattern|cadeia de caracteres|Uma expressão regular que corresponda a um identificador entre aspas e tem um valor de correspondência de identificador sem as aspas. Por exemplo, se a fonte de dados usadas aspas duplas para identificar os identificadores entre aspas, isso seria: "(([^\\"] &#124;\\" \\")*)".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Indica se os identificadores entre aspas são tratados como maiusculas e minúsculas ou não.|  
|StatementSeparatorPattern|cadeia de caracteres|Uma expressão regular compatível com o separador de instrução.|  
|StringLiteralPattern|cadeia de caracteres|Uma expressão regular que coincida com uma literal de cadeia de caracteres e tem um valor de correspondência do literal em si. Por exemplo, se a fonte de dados usadas aspas simples para identificar as cadeias de caracteres, isso seria: "('([^'] &#124; ') *')"'|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Especifica que tipos de instruções de associação do SQL são suportados pela fonte de dados.|  
  
## <a name="datatypes"></a>Tipos de dados  
 Essas informações de expõe de coleção de esquema sobre tipos de dados que são suportados pelo banco de dados que o .NET Framework provedor gerenciado estão conectadas atualmente à.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|NomeDoTipo|cadeia de caracteres|Os dados específicos do provedor de nome de tipo.|  
|ProviderDbType|int|O valor de tipo específico de provedor que deve ser usado ao especificar o tipo do parâmetro. Por exemplo, SqlDbType.Money ou OracleType.Blob.|  
|ColumnSize|long|O comprimento de uma coluna não numérica ou parâmetro refere-se para o máximo ou o comprimento definido para esse tipo pelo provedor.<br /><br /> Para dados de caracteres, esse é o máximo ou definido o comprimento em unidades, definidas pela fonte de dados. Oracle tem o conceito de especificar um comprimento e, em seguida, especificando o tamanho real do armazenamento para alguns tipos de dados de caractere. Isso define apenas o tamanho em unidades para Oracle.<br /><br /> Para tipos de dados de data e hora, esse é o comprimento da representação de cadeia de caracteres (supondo que a precisão máxima permitida do componente frações de segundo).<br /><br /> Se o tipo de dados for numérico, esse é o limite superior na precisão máxima do tipo de dados.|  
|CreateFormat|cadeia de caracteres|Cadeia de caracteres de formato que representa como adicionar essa coluna para uma instrução de definição de dados, como CREATE TABLE. Cada elemento na matriz CreateParameter deve ser representado por um "marcador de parâmetro" na cadeia de caracteres de formato.<br /><br /> Por exemplo, o tipo de dados SQL DECIMAL requer uma precisão e uma escala. Nesse caso, a cadeia de caracteres de formato seria "DECIMAL({0},{1})".|  
|CreateParameters|cadeia de caracteres|Os parâmetros de criação devem ser especificados ao criar uma coluna desse tipo de dados. Cada parâmetro de criação é listado na cadeia de caracteres, separada por uma vírgula na ordem em que eles devem ser fornecidos.<br /><br /> Por exemplo, o tipo de dados SQL DECIMAL requer uma precisão e uma escala. Nesse caso, os parâmetros de criação devem conter a cadeia de caracteres "precisão, escala".<br /><br /> Em um comando de texto para criar uma coluna DECIMAL com uma precisão de 10 e uma escala de 2, o valor da coluna CreateFormat pode ser DECIMAL({0},{1}) "e a especificação de tipo completa seria DECIMAL(10,2).|  
|DataType|cadeia de caracteres|O nome do tipo do tipo de dados do .NET Framework.|  
|IsAutoincrementable|bool|True – valores desse tipo de dados podem ser de incremento automático.<br /><br /> FALSO-valores desse tipo de dados podem não ser incremento automático.<br /><br /> Observe que isso apenas indica se uma coluna desse tipo de dados pode ser incremento automático, nem todas as colunas desse tipo são incremento automático.|  
|IsBestMatch|bool|True – o tipo de dados é a melhor correspondência entre todos os tipos de dados no repositório de dados e o tipo de dados do .NET Framework indicado pelo valor na coluna de tipo de dados.<br /><br /> False – o tipo de dados não é a melhor correspondência.<br /><br /> Para cada conjunto de linhas em que o valor da coluna de tipo de dados é o mesmo, a coluna IsBestMatch é definida como true em apenas uma linha.|  
|IsCaseSensitive|bool|True – o tipo de dados é um tipo de caractere e diferencia maiusculas de minúsculas.<br /><br /> False – o tipo de dados não é um tipo de caractere ou não diferencia maiusculas de minúsculas.|  
|IsFixedLength|bool|True – colunas desse tipo de dados criado pela linguagem de definição de dados (DDL) terão comprimento fixo.<br /><br /> False – colunas deste tipo de dados criadas pelo DDL será de comprimento variável.<br /><br /> DBNull.Value—It não se sabe se o provedor mapeará esse campo com uma coluna de comprimento fixo ou comprimento variável.|  
|IsFixedPrecisionScale|bool|True – o tipo de dados tem uma precisão e escala fixas.<br /><br /> False – o tipo de dados não tem uma precisão e escala fixas.|  
|IsLong|bool|True – o tipo de dados contém dados muito longos; a definição de dados muito longos é específica do provedor.<br /><br /> False – o tipo de dados não contém dados muito longos.|  
|IsNullable|bool|True – o tipo de dados é anulável.<br /><br /> False – o tipo de dados não é anulável.<br /><br /> DBNull.Value—It não se sabe se o tipo de dados é anulável.|  
|IsSearchable|bool|True – o tipo de dados pode ser usado em uma cláusula WHERE com qualquer operador, exceto o predicado LIKE.<br /><br /> False – o tipo de dados não pode ser usado em uma cláusula WHERE com qualquer operador, exceto o predicado LIKE.|  
|IsSearchableWithLike|bool|True – o tipo de dados pode ser usado com o predicado LIKE<br /><br /> False – o tipo de dados não pode ser usado com o predicado LIKE.|  
|IsUnsigned|bool|True – o tipo de dados não está assinado.<br /><br /> False – o tipo de dados é assinado.<br /><br /> DBNull.Value—Not aplicável ao tipo de dados.|  
|MaximumScale|short|Se o indicador de tipo é um tipo numérico, esse é o número máximo de dígitos permitidos à direita da vírgula decimal. Caso contrário, isso é DBNull.|  
|MinimumScale|short|Se o indicador de tipo é um tipo numérico, esse é o número mínimo de dígitos permitidos à direita da vírgula decimal. Caso contrário, isso é DBNull.|  
|IsConcurrencyType|bool|True – o tipo de dados é atualizado no banco de dados sempre que a linha é alterada e o valor da coluna é diferente de todos os valores anteriores<br /><br /> FALSO – o tipo de dados é atualizada no banco de dados sempre que a linha é alterada de Observação<br /><br /> DBNull – o banco de dados não suporta esse tipo de tipo de dados|  
|IsLiteralSupported|bool|True – o tipo de dados pode ser expresso como um literal<br /><br /> FALSO – o tipo de dados não pode ser expresso como um literal|  
|LiteralPrefix|cadeia de caracteres|O prefixo aplicado a um determinado literal.|  
|LiteralSuffix|cadeia de caracteres|O sufixo aplicado a um determinado literal.|  
|NativeDataType|Cadeia de caracteres|NativeDataType é uma coluna específica do OLE DB para expor o tipo de OLE DB do tipo de dados.|  
  
## <a name="restrictions"></a>Restrições  
 Esta coleção de esquema exposto informações sobre as restrições que são suportados pelo provedor gerenciado do .NET Framework que está sendo usado para conectar-se ao banco de dados.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|CollectionName|cadeia de caracteres|O nome da coleção que essas restrições se aplicam a.|  
|RestrictionName|cadeia de caracteres|O nome da restrição na coleção.|  
|RestrictionDefault|cadeia de caracteres|Ignorado.|  
|RestrictionNumber|int|O local real nas restrições de coleções que essa restrição específica cairá.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Esta coleção de esquema expõe informações sobre as palavras que são reservados pelo banco de dados que o .NET Framework gerenciado provedor que está atualmente conectado a.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|ReservedWord|cadeia de caracteres|Palavra reservada específica do provedor.|  
  
## <a name="see-also"></a>Consulte também  
 [Recuperando informações de esquema de banco de dados](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [GetSchema e coleções de esquema](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
