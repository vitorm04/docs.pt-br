---
title: Coleções de esquema comuns
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: 0b23164b56c6fefc6c258f313e9e17b156605518
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786790"
---
# <a name="common-schema-collections"></a>Coleções de esquema comuns
As coleções de esquema comuns são as coleções de esquema que são implementadas por cada um dos provedores gerenciados .NET Framework. Você pode consultar um provedor gerenciado .NET Framework para determinar a lista de coleções de esquema com suporte chamando o método **GetSchema** sem argumentos ou com o nome da coleção de esquema "MetaDataCollections". Isso retornará um <xref:System.Data.DataTable> com uma lista de coleções de esquema com suporte, o número de restrições às quais cada um deles oferece suporte e o número de partes de identificador que elas usam. Essas coleções descrevem todas as colunas necessárias. Os provedores são livres para adicionar mais colunas se quiserem. Por exemplo, `SqlClient` e `OracleClient` adicione ParameterName à coleção de restrições.  
  
 Se um provedor não puder determinar o valor de uma coluna necessária, ele retornará NULL.  
  
 Para obter mais informações sobre como usar os métodos **GetSchema** , consulte [GetSchema e coleções de esquema](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Essa coleção de esquema expõe informações sobre todas as coleções de esquema com suporte no provedor gerenciado .NET Framework que é usado atualmente para se conectar ao banco de dados.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|CollectionName|cadeia de caracteres|O nome da coleção a ser passada para o método **GetSchema** para retornar a coleção.|  
|NumberOfRestrictions|int|O número de restrições que podem ser especificadas para a coleção.|  
|NumberOfIdentifierParts|int|O número de partes no identificador composto/nome do objeto do banco de dados. Por exemplo, em SQL Server, isso seria 3 para tabelas e 4 para colunas. No Oracle, seria 2 para tabelas e 3 para colunas.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Essa coleção de esquema expõe informações sobre a fonte de dados à qual o provedor gerenciado .NET Framework está atualmente conectado.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|cadeia de caracteres|A expressão regular para corresponder os separadores de composição em um identificador composto. Por exemplo, "\\." (para SQL Server) ou "\@&#124;\\." (para Oracle).<br /><br /> Um identificador composto normalmente é o que é usado para um nome de objeto de banco de dados, por exemplo: pubs.\@dbo. Authors ou pubs dbo. Authors.<br /><br /> Por SQL Server, use a expressão regular "\\.". Para o OracleClient, use\@"&#124;\\.".<br /><br /> Para ODBC, use o Catalog_name_seperator.<br /><br /> Para OLE DB use DBLITERAL_CATALOG_SEPARATOR ou DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceProductName|cadeia de caracteres|O nome do produto acessado pelo provedor, como "Oracle" ou "SQLServer".|  
|DataSourceProductVersion|cadeia de caracteres|Indica a versão do produto acessado pelo provedor, no formato nativo de fontes de dados e não no formato Microsoft.<br /><br /> Em alguns casos, DataSourceProductVersion e DataSourceProductVersionNormalized terão o mesmo valor. No caso de OLE DB e ODBC, eles serão sempre os mesmos que são mapeados para a mesma chamada de função na API nativa subjacente.|  
|DataSourceProductVersionNormalized|cadeia de caracteres|Uma versão normalizada para a fonte de dados, de modo que ela possa ser `String.Compare()`comparada com. O formato disso é consistente para todas as versões do provedor para impedir que a versão 10 seja classificada entre a versão 1 e a versão 2.<br /><br /> Por exemplo, o provedor Oracle usa um formato de "nn. nn. nn. nn. nn" para sua versão normalizada, o que faz com que uma fonte de dados Oracle 8i retorne "08.01.07.04.01". SQL Server usa o formato típico da Microsoft "nn. nn. nnnn".<br /><br /> Em alguns casos, DataSourceProductVersion e DataSourceProductVersionNormalized terão o mesmo valor. No caso de OLE DB e ODBC, eles serão sempre os mesmos que são mapeados para a mesma chamada de função na API nativa subjacente.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Especifica a relação entre as colunas em uma cláusula GROUP BY e as colunas não agregadas na lista de seleção.|  
|IdentifierPattern|cadeia de caracteres|Uma expressão regular que corresponde a um identificador e tem um valor de correspondência do identificador. Por exemplo, "[A-Za-z0-9_ # $]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Indica se identificadores não entre aspas são tratados como diferenciando maiúsculas de minúsculas ou não.|  
|OrderByColumnsInSelect|bool|Especifica se as colunas em uma cláusula ORDER BY devem estar na lista de seleção. Um valor true indica que eles devem estar na lista de seleção, um valor false indica que eles não devem estar na lista de seleção.|  
|ParameterMarkerFormat|cadeia de caracteres|Uma cadeia de caracteres de formato que representa como formatar um parâmetro.<br /><br /> Se os parâmetros nomeados forem compatíveis com a fonte de dados, o primeiro espaço reservado nessa cadeia de caracteres deverá ser o local em que o nome do parâmetro deve ser formatado.<br /><br /> Por exemplo, se a fonte de dados espera que os parâmetros sejam nomeados e prefixados com um ': ',{0}isso seria ":". Ao Formatar isso com um nome de parâmetro "P1", a cadeia de caracteres resultante é ":p 1".<br /><br /> Se a fonte de dados espera que os parâmetros sejam prefixados\@com o ' ', mas os nomes já os incluem, isso{0}seria ' ', e o resultado da formatação de um\@parâmetro chamado "P1" seria\@simplesmente "P1".<br /><br /> Para fontes de dados que não esperam parâmetros nomeados e esperam o uso de '? ' , a cadeia de caracteres de formato pode ser especificada simplesmente como '? ', o que ignoraria o nome do parâmetro. Por OLE DB retornamos '? '.|  
|ParameterMarkerPattern|cadeia de caracteres|Uma expressão regular que corresponde a um marcador de parâmetro. Ele terá um valor de correspondência do nome do parâmetro, se houver.<br /><br /> Por exemplo, se houver suporte para parâmetros nomeados com\@um caractere de lead-in que será incluído no nome do parâmetro, isso seria: "(\@[a-Za-z0-9_ $ #] *)".<br /><br /> No entanto, se houver suporte para parâmetros nomeados com um ': ' como o caractere de lead-in e ele não fizer parte do nome do parâmetro, isso seria: ":([A-Za-z0-\*9_ $ #])".<br /><br /> É claro que, se a fonte de dados não der suporte a parâmetros nomeados, isso simplesmente seria "?".|  
|ParameterNameMaxLength|int|O comprimento máximo de um nome de parâmetro em caracteres. O Visual Studio espera que, se houver suporte para nomes de parâmetro, o valor mínimo para o comprimento máximo é de 30 caracteres.<br /><br /> Se a fonte de dados não oferecer suporte a parâmetros nomeados, essa propriedade retornará zero.|  
|ParameterNamePattern|cadeia de caracteres|Uma expressão regular que corresponde aos nomes de parâmetro válidos. Fontes de dados diferentes têm regras diferentes sobre os caracteres que podem ser usados para nomes de parâmetro.<br /><br /> O Visual Studio espera que, se houver suporte para nomes de parâmetros, os caracteres "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" sejam o conjunto mínimo de caracteres com suporte válidos para nomes de parâmetro.|  
|QuotedIdentifierPattern|cadeia de caracteres|Uma expressão regular que corresponde a um identificador entre aspas e tem um valor de correspondência do próprio identificador sem aspas. Por exemplo, se a fonte de dados usou aspas duplas para identificar identificadores entre aspas, isso seria: "(([\\^"&#124;\\]\\"") *) ".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Indica se os identificadores entre aspas são tratados como diferenciando maiúsculas de minúsculas ou não.|  
|StatementSeparatorPattern|cadeia de caracteres|Uma expressão regular que corresponde ao separador de instrução.|  
|StringLiteralPattern|cadeia de caracteres|Uma expressão regular que corresponde a um literal de cadeia de caracteres e tem um valor de correspondência do próprio literal. Por exemplo, se a fonte de dados usou aspas simples para identificar cadeias de caracteres, isso seria: "(' ([^&#124;'] ' ') * ')" '|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Especifica quais tipos de instruções SQL Join são compatíveis com a fonte de dados.|  
  
## <a name="datatypes"></a>Tipos  
 Essa coleção de esquema expõe informações sobre os tipos de dados com suporte no banco de dado ao qual o provedor gerenciado .NET Framework está atualmente conectado.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|NomeDoTipo|cadeia de caracteres|O nome do tipo de dados específico do provedor.|  
|ProviderDbType|int|O valor do tipo específico do provedor que deve ser usado ao especificar o tipo de um parâmetro. Por exemplo, SqlDbType. Money ou OracleType. blob.|  
|ColumnSize|long|O comprimento de uma coluna ou parâmetro não numérico refere-se ao máximo ou ao comprimento definido para esse tipo pelo provedor.<br /><br /> Para dados de caractere, esse é o comprimento máximo ou definido em unidades, definido pela fonte de dados. A Oracle tem o conceito de especificar um comprimento e, em seguida, especificar o tamanho real do armazenamento para alguns tipos de dados de caractere. Isso define apenas o comprimento em unidades para Oracle.<br /><br /> Para tipos de dados de data e hora, esse é o comprimento da representação de cadeia de caracteres (supondo a precisão máxima permitida do componente de segundos fracionários).<br /><br /> Se o tipo de dados for numérico, esse será o limite superior na precisão máxima do tipo de dados.|  
|CreateFormat|cadeia de caracteres|Cadeia de caracteres de formato que representa como adicionar essa coluna a uma instrução de definição de dados, como CREATE TABLE. Cada elemento na matriz CreateParameter deve ser representado por um "marcador de parâmetro" na cadeia de caracteres de formato.<br /><br /> Por exemplo, o tipo de dados SQL DECIMAL precisa de uma precisão e uma escala. Nesse caso, a cadeia de caracteres de formato seria "DECIMAL{0}({1},)".|  
|Criarparameters|cadeia de caracteres|Os parâmetros de criação que devem ser especificados ao criar uma coluna desse tipo de dados. Cada parâmetro de criação é listado na cadeia de caracteres, separados por uma vírgula na ordem em que eles devem ser fornecidos.<br /><br /> Por exemplo, o tipo de dados SQL DECIMAL precisa de uma precisão e uma escala. Nesse caso, os parâmetros de criação devem conter a cadeia de caracteres "precisão, escala".<br /><br /> Em um comando de texto para criar uma coluna decimal com uma precisão de 10 e uma escala de 2, o valor da coluna CreateFormat pode ser decimal{0}({1},) "e a especificação de tipo completo seria decimal (10, 2).|  
|DataType|cadeia de caracteres|O nome do tipo de .NET Framework do tipo de dados.|  
|IsAutoincrementable|bool|true – os valores desse tipo de dados podem ser incrementados automaticamente.<br /><br /> false — os valores desse tipo de dados podem não ser incrementados automaticamente.<br /><br /> Observe que isso simplesmente indica se uma coluna desse tipo de dados pode ser incrementada automaticamente, e não que todas as colunas desse tipo sejam incrementadas automaticamente.|  
|IsBestMatch|bool|true – o tipo de dados é a melhor correspondência entre todos os tipos de dados no repositório de dados e o tipo de dados .NET Framework indicado pelo valor na coluna DataType.<br /><br /> false — o tipo de dados não é a melhor correspondência.<br /><br /> Para cada conjunto de linhas em que o valor da coluna DataType é o mesmo, a coluna IsBestMatch é definida como true em apenas uma linha.|  
|IsCaseSensitive|bool|true – o tipo de dados é um tipo de caractere e diferencia maiúsculas de minúsculas.<br /><br /> false — o tipo de dados não é um tipo de caractere ou não diferencia maiúsculas de minúsculas.|  
|IsFixedLength|bool|true – colunas desse tipo de dados criadas pelo DDL (linguagem de definição de dados) terão comprimento fixo.<br /><br /> false — colunas desse tipo de dados criadas pelo DDL serão de comprimento variável.<br /><br /> DBNull. Value — não é conhecido se o provedor mapear esse campo com uma coluna de comprimento fixo ou de comprimento variável.|  
|IsFixedPrecisionScale|bool|true – o tipo de dados tem uma precisão e uma escala fixas.<br /><br /> false — o tipo de dados não tem uma precisão e uma escala fixas.|  
|IsLong|bool|true – o tipo de dados contém dados muito longos; a definição de dados muito longos é específica do provedor.<br /><br /> false — o tipo de dados não contém dados muito longos.|  
|IsNullable|bool|true — o tipo de dados é anulável.<br /><br /> false — o tipo de dados não permite valor nulo.<br /><br /> DBNull. Value — não é conhecido se o tipo de dados é anulável.|  
|IsSearchable|bool|true — o tipo de dados pode ser usado em uma cláusula WHERE com qualquer operador, exceto o predicado LIKE.<br /><br /> false — o tipo de dados não pode ser usado em uma cláusula WHERE com qualquer operador, exceto o predicado LIKE.|  
|IsSearchableWithLike|bool|true — o tipo de dados pode ser usado com o predicado LIKE<br /><br /> false — o tipo de dados não pode ser usado com o predicado LIKE.|  
|IsUnsigned|bool|true – o tipo de dados não é assinado.<br /><br /> false — o tipo de dados é assinado.<br /><br /> DBNull. Value — não aplicável ao tipo de dados.|  
|MaximumScale|short|Se o indicador de tipo for um tipo numérico, esse será o número máximo de dígitos permitidos à direita do ponto decimal. Caso contrário, é DBNull. Value.|  
|MinimumScale|short|Se o indicador de tipo for um tipo numérico, esse será o número mínimo de dígitos permitidos à direita do ponto decimal. Caso contrário, é DBNull. Value.|  
|IsConcurrencyType|bool|true – o tipo de dados é atualizado pelo banco de dado sempre que a linha é alterada e o valor da coluna é diferente de todos os valores anteriores<br /><br /> false – o tipo de dados é nota atualizado pelo banco de dado toda vez que a linha é alterada<br /><br /> DBNull. Value – o banco de dados não oferece suporte a esse tipo de tipo de dado|  
|IsLiteralSupported|bool|true – o tipo de dados pode ser expresso como um literal<br /><br /> false – o tipo de dados não pode ser expresso como um literal|  
|LiteralPrefix|cadeia de caracteres|O prefixo aplicado a um literal específico.|  
|LiteralSuffix|cadeia de caracteres|O sufixo aplicado a um literal específico.|  
|NativeDataType|Cadeia de Caracteres|NativeDataType é um OLE DB coluna específica para expor o tipo de OLE DB do tipo de dados.|  
  
## <a name="restrictions"></a>Restrições  
 Essa coleção de esquema expôs informações sobre as restrições que têm suporte no provedor gerenciado .NET Framework que é usado atualmente para se conectar ao banco de dados.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|CollectionName|cadeia de caracteres|O nome da coleção à qual essas restrições se aplicam.|  
|RestrictionName|cadeia de caracteres|O nome da restrição na coleção.|  
|RestrictionDefault|cadeia de caracteres|Ignorado.|  
|RestrictionNumber|int|O local real nas restrições de coleções que essa restrição específica cai.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Essa coleção de esquema expõe informações sobre as palavras reservadas pelo banco de dados que o .NET Framework provedor gerenciado ao qual está atualmente conectado.  
  
|ColumnName|DataType|Descrição|  
|----------------|--------------|-----------------|  
|ReservedWord|cadeia de caracteres|Palavra reservada específica do provedor.|  
  
## <a name="see-also"></a>Consulte também

- [Recuperando informações de esquema de banco de dados](retrieving-database-schema-information.md)
- [GetSchema e coleções de esquema](getschema-and-schema-collections.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
