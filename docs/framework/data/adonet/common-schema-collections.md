---
title: Coleções de esquema comuns
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: b6c2c89101f3304a0cab014de2def22195541471
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249468"
---
# <a name="common-schema-collections"></a>Coleções de esquema comuns
As coleções de esquemas comuns são as coleções de esquemas que são implementadas por cada um dos provedores gerenciados do .NET Framework. Você pode consultar um provedor gerenciado pelo .NET Framework para determinar a lista de coleções de esquemas suportadas chamando o método **GetSchema** sem argumentos ou com o nome de coleta de esquemas "MetaDataCollections". Isso retornará <xref:System.Data.DataTable> um com uma lista das coleções de esquemas suportadas, o número de restrições que cada um suporta e o número de peças de identificação que eles usam. Essas coleções descrevem todas as colunas necessárias. Os provedores são livres para adicionar colunas adicionais, se desejarem. Por `SqlClient` exemplo, `OracleClient` e adicione ParameterName à coleção de restrições.  
  
 Se um provedor não conseguir determinar o valor de uma coluna requerida, ele retornará nulo.  
  
 Para obter mais informações sobre como usar os métodos **GetSchema,** consulte [GetSchema e Schema Collections](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>Metadatacollections  
 Esta coleção de esquemas expõe informações sobre todas as coleções de esquemas suportadas pelo provedor gerenciado .NET Framework que atualmente é usado para se conectar ao banco de dados.  
  
|ColumnName|Tipo de dados|Descrição|  
|----------------|--------------|-----------------|  
|CollectionName|string|O nome da coleção para passar para o método **GetSchema** para devolver a coleção.|  
|NumberOfRestrições|INT|O número de restrições que podem ser especificadas para a coleta.|  
|NúmeroOfIdentifierParts|INT|O número de partes no nome do objeto identificador/banco de dados composto. Por exemplo, no SQL Server, este seria 3 para tabelas e 4 para colunas. No Oracle, seria 2 para tabelas e 3 para colunas.|  
  
## <a name="datasourceinformation"></a>Datasourceinformation  
 Essa coleta de esquemas expõe informações sobre a fonte de dados à que o provedor gerenciado pelo .NET Framework está atualmente conectado.  
  
|ColumnName|Tipo de dados|Descrição|  
|----------------|--------------|-----------------|  
|CompostoIdentificadorSeparadorPadrão de separator|string|A expressão regular para combinar com os separadores compostos em um identificador composto. Por exemplo, "\\". (para SQL Server)\@ \\ou "&#124;." (para Aoráculo).<br /><br /> Um identificador composto é tipicamente o que é usado para um nome de objeto\@de banco de dados, por exemplo: pubs.dbo.authors ou pubs dbo.authors.<br /><br /> Para o SQL Server,\\use a expressão regular " .". Para OracleClient,\@ use \\"&#124;.".<br /><br /> Para o ODBC utilize o Catalog_name_seperator.<br /><br /> Para o OLE DB use DBLITERAL_CATALOG_SEPARATOR ou DBLITERAL_SCHEMA_SEPARATOR.|  
|DataSourceNome do produto|string|O nome do produto acessado pelo provedor, como "Oracle" ou "SQLServer".|  
|DataSourceProductVersion|string|Indica a versão do produto acessado pelo provedor, no formato nativo das fontes de dados e não no formato Microsoft.<br /><br /> Em alguns casos, DataSourceProductVersion e DataSourceProductVersionNormalized serão o mesmo valor. No caso do OLE DB e do ODBC, estes serão sempre os mesmos que são mapeados para a mesma chamada de função na API nativa subjacente.|  
|DataSourceProductVersionNormalized|string|Uma versão normalizada para a fonte de dados, de tal forma que possa ser comparada com `String.Compare()`. O formato disso é consistente para todas as versões do provedor para evitar que a versão 10 se classifique entre a versão 1 e a versão 2.<br /><br /> Por exemplo, o provedor Oracle usa um formato de "nn.nn.nn.nn" para sua versão normalizada, o que faz com que uma fonte de dados Oracle 8i retorne "08.01.07.04.01". O SQL Server usa o formato típico da Microsoft "nn.nn.nnnn".<br /><br /> Em alguns casos, DataSourceProductVersion e DataSourceProductVersionNormalized terão o mesmo valor. No caso do OLE DB e o ODBC, estes serão sempre os mesmos que são mapeados para a mesma chamada de função na API nativa subjacente.|  
|Groupbybehavior|<xref:System.Data.Common.GroupByBehavior>|Especifica a relação entre as colunas em uma cláusula GROUP BY e as colunas não agregadas na lista selecionada.|  
|IdentificadorPadrão|string|Uma expressão regular que corresponde a um identificador e tem um valor de correspondência do identificador. Por exemplo "[A-Za-z0-9_#$]".|  
|IdentificadorCaso|<xref:System.Data.Common.IdentifierCase>|Indica se os identificadores não citados são tratados como sensíveis a maiúsculas e minúsculas.|  
|OrderByColumnsInSelect|bool|Especifica se as colunas em uma cláusula ORDER BY devem estar na lista de seleção. Um valor de verdade indica que eles são obrigados a estar na lista de seleção, um valor de falso indica que eles não são obrigados a estar na lista de seleção.|  
|Parametermarkerformat|string|Uma seqüência de formato que representa como formatar um parâmetro.<br /><br /> Se os parâmetros nomeados forem suportados pela fonte de dados, o primeiro espaço reservado nesta seqüência deve ser onde o nome do parâmetro deve ser formatado.<br /><br /> Por exemplo, se a fonte de dados espera que os parâmetros sejam{0}nomeados e prefixados com um ':' isso seria ": ". Ao formatar isso com um nome de parâmetro de "p1" a seqüência resultante é ":p1".<br /><br /> Se a fonte de dados espera que\@os parâmetros sejam prefixados com{0}o ' ', mas os nomes\@já os incluem,\@isso seria ' ', e o resultado da formatação de um parâmetro chamado " p1 " seria simplesmente " p1 ".<br /><br /> Para fontes de dados que não esperam parâmetros nomeados e esperam o uso do caractere '?', a seqüência de formato pode ser especificada como simplesmente '?', o que ignoraria o nome do parâmetro. Para OLE DB retornamos '?'.|  
|ParâmetroMarcadorPadrão|string|Uma expressão regular que corresponde a um marcador de parâmetro. Ele terá um valor de correspondência do nome do parâmetro, se houver.<br /><br /> Por exemplo, se os parâmetros\@nomeados forem suportados com um ' caractere de entrada\@' que será incluído no nome do parâmetro, este será: "(A-Za-z0-9_$#]".<br /><br /> No entanto, se os parâmetros nomeados forem suportados com um ':' como caractere principal e não fizer parte do nome do\*parâmetro, isso seria: ":([A-Za-z0-9_$#] ".<br /><br /> Claro, se a fonte de dados não suportar parâmetros nomeados, isso seria simplesmente "?".|  
|Parameternamemaxlength|INT|O comprimento máximo de um nome parâmetro em caracteres. O Visual Studio espera que, se os nomes dos parâmetros forem suportados, o valor mínimo para o comprimento máximo é de 30 caracteres.<br /><br /> Se a fonte de dados não suportar parâmetros nomeados, esta propriedade retorna zero.|  
|Parameternamepattern|string|Uma expressão regular que corresponda aos nomes de parâmetros válidos. Diferentes fontes de dados têm regras diferentes em relação aos caracteres que podem ser usados para nomes de parâmetros.<br /><br /> O Visual Studio espera que, se os nomes dos parâmetros forem suportados, os caracteres "\p{Lu}\p{Ll}\p{Lt}\p{Lo}\p{NL}\p{Nd}" são o conjunto mínimo de caracteres suportados válidos para nomes de parâmetros.|  
|CitedIdentifierPattern|string|Uma expressão regular que corresponde a um identificador citado e tem um valor de correspondência do próprio identificador sem as aspas. Por exemplo, se a fonte de dados usou aspas duplas para identificar identificadores\\citados, isso seria: "([^ "]&#124;\\")*".\\|  
|Caso de identificador citado|<xref:System.Data.Common.IdentifierCase>|Indica se os identificadores citados são tratados como sensíveis a maiúsculas e minúsculas.|  
|Padrão de declaraçãoSeparador|string|Uma expressão regular que corresponde ao separador de declaração.|  
|StringLiteralPattern|string|Uma expressão regular que corresponde a uma seqüência literal e tem um valor de correspondência do próprio literal. Por exemplo, se a fonte de dados usou cotações únicas para identificar strings, isso seria: "('[^']&#124;'')''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''|  
|Operadores de join-suporte|<xref:System.Data.Common.SupportedJoinOperators>|Especifica quais tipos de declarações de adesão ao SQL são suportadas pela fonte de dados.|  
  
## <a name="datatypes"></a>DataTypes  
 Essa coleta de esquemas expõe informações sobre os tipos de dados suportados pelo banco de dados ao que o provedor gerenciado pelo .NET Framework está conectado atualmente.  
  
|ColumnName|Tipo de dados|Descrição|  
|----------------|--------------|-----------------|  
|TypeName|string|O nome de tipo de dados específico do provedor.|  
|ProviderDbType|INT|O valor de tipo específico do provedor que deve ser usado ao especificar o tipo de parâmetro. Por exemplo, SqlDbType.Money ou OracleType.Blob.|  
|ColumnSize|long|O comprimento de uma coluna ou parâmetro não numérico refere-se ao máximo ou ao comprimento definido para este tipo pelo provedor.<br /><br /> Para os dados de caracteres, este é o comprimento máximo ou definido em unidades, definido pela fonte de dados. A Oracle tem o conceito de especificar um comprimento e, em seguida, especificar o tamanho real de armazenamento para alguns tipos de dados de caracteres. Isso define apenas o comprimento das unidades para o Oracle.<br /><br /> Para tipos de dados de data-hora, este é o comprimento da representação de string (assumindo a precisão máxima permitida do componente de segundos fracionados).<br /><br /> Se o tipo de dados for numérico, esse será o limite superior na precisão máxima do tipo de dados.|  
|Criarformato|string|String de formato que representa como adicionar esta coluna a uma declaração de definição de dados, como CREATE TABLE. Cada elemento na matriz CreateParameter deve ser representado por um "marcador de parâmetro" na seqüência de formatos.<br /><br /> Por exemplo, o tipo de dados SQL DECIMAL precisa de uma precisão e uma escala. Neste caso, a seqüência de formato{0}{1}seria "DECIMAL( , )".|  
|Criar parâmetros|string|Os parâmetros de criação que devem ser especificados ao criar uma coluna desse tipo de dados. Cada parâmetro de criação é listado na seqüência, separado por uma comma na ordem em que devem ser fornecidos.<br /><br /> Por exemplo, o tipo de dados SQL DECIMAL precisa de uma precisão e uma escala. Neste caso, os parâmetros de criação devem conter a string "precisão, escala".<br /><br /> Em um comando de texto para criar uma coluna DECIMAL com uma precisão de 10 e uma{0}{1}escala de 2, o valor da coluna CreateFormat pode ser DECIMAL e a especificação completa do tipo seria DECIMAL(10,2).|  
|Tipo de dados|string|O nome do tipo .NET Framework do tipo de dados.|  
|Éautoincrementável|bool|verdadeiro — valores desse tipo de dados podem ser incrementados automaticamente.<br /><br /> falso — valores desse tipo de dados podem não ser incrementados automaticamente.<br /><br /> Observe que isso apenas indica se uma coluna deste tipo de dados pode ser incrementada automaticamente, não que todas as colunas deste tipo estejam incrementando automaticamente.|  
|IsBestMatch|bool|true — O tipo de dados é a melhor combinação entre todos os tipos de dados no armazenamento de dados e o tipo de dados .NET Framework indicado pelo valor na coluna DataType.<br /><br /> falso — o tipo de dados não é a melhor combinação.<br /><br /> Para cada conjunto de linhas em que o valor da coluna DataType é o mesmo, a coluna IsBestMatch é definida como true em apenas uma linha.|  
|IsCaseSensitive|bool|verdadeiro — o tipo de dados é um tipo de caractere e é sensível a maiúsculas e minúsculas.<br /><br /> falso — o tipo de dados não é um tipo de caractere ou não é sensível a maiúsculas e minúsculas.|  
|IsFixedLength|bool|verdade — as colunas desse tipo de dados criadas pelo DDL (Data Definition Language, linguagem de definição de dados) serão de comprimento fixo.<br /><br /> falsa — as colunas desse tipo de dados criadas pelo DDL terão comprimento variável.<br /><br /> DBNull.Value — Não se sabe se o provedor mapeará este campo com uma coluna de comprimento fixo ou de comprimento variável.|  
|escala isFixedPrecision|bool|verdadeiro — o tipo de dados tem uma precisão e escala fixas.<br /><br /> falso — o tipo de dados não tem uma precisão e escala fixas.|  
|IsLong|bool|verdadeiro — o tipo de dados contém dados muito longos; a definição de dados muito longos é específica do provedor.<br /><br /> falso — o tipo de dados não contém dados muito longos.|  
|IsNullable|bool|verdadeiro — o tipo de dados é anulado.<br /><br /> falso — o tipo de dados não é anulado.<br /><br /> DBNull.Value — Não se sabe se o tipo de dados é anulado.|  
|Issearchable|bool|verdadeiro — o tipo de dados pode ser usado em uma cláusula WHERE com qualquer operador, exceto o predicado LIKE.<br /><br /> falso — o tipo de dados não pode ser usado em uma cláusula WHERE com qualquer operador, exceto o predicado LIKE.|  
|ÉsearchableComLike|bool|verdadeiro — o tipo de dados pode ser usado com o predicado LIKE<br /><br /> falso — o tipo de dados não pode ser usado com o predicado LIKE.|  
|Não está assinado|bool|verdadeiro — o tipo de dados não é assinado.<br /><br /> falso — o tipo de dados é assinado.<br /><br /> DBNull.Value — Não aplicável ao tipo de dados.|  
|Maximumscale|short|Se o indicador de tipo for um tipo numérico, este é o número máximo de dígitos permitidos à direita do ponto decimal. Caso contrário, este é DBNull.Value.|  
|Minimumscale|short|Se o indicador de tipo for um tipo numérico, este é o número mínimo de dígitos permitidos à direita do ponto decimal. Caso contrário, este é DBNull.Value.|  
|IsConcurrencyType|bool|verdadeiro – o tipo de dados é atualizado pelo banco de dados toda vez que a linha é alterada e o valor da coluna é diferente de todos os valores anteriores<br /><br /> falso – o tipo de dados é atualizado pelo banco de dados toda vez que a linha é alterada<br /><br /> DBNull.Value – o banco de dados não suporta esse tipo de tipo de dados|  
|IsLiterSupported|bool|verdadeiro – o tipo de dados pode ser expresso como um literal<br /><br /> falso – o tipo de dados não pode ser expresso como um literal|  
|LiteralPrefix|string|O prefixo aplicado a um determinado literal.|  
|LiteralSufix|string|O sufixo aplicado a um determinado literal.|  
|NativeDataType|String|NativeDataType é uma coluna específica do OLE DB para expor o tipo OLE DB do tipo de dados .|  
  
## <a name="restrictions"></a>Restrições  
 Essa coleta de esquemas expôs informações sobre as restrições suportadas pelo provedor gerenciado .NET Framework que atualmente é usado para se conectar ao banco de dados.  
  
|ColumnName|Tipo de dados|Descrição|  
|----------------|--------------|-----------------|  
|CollectionName|string|O nome da coleção a que essas restrições se aplicam.|  
|Nome da restrição|string|O nome da restrição na coleção.|  
|RestriçãoDefault|string|Ignorado.|  
|Número de restrições|INT|A localização real nas coleções restrições que esta restrição particular cai dentro|  
  
## <a name="reservedwords"></a>Reservedwords  
 Essa coleta de esquemas expõe informações sobre as palavras reservadas pelo banco de dados ao que o provedor gerenciado pelo .NET Framework está conectado atualmente.  
  
|ColumnName|Tipo de dados|Descrição|  
|----------------|--------------|-----------------|  
|Palavra Reservada|string|Palavra reservada específica do provedor.|  
  
## <a name="see-also"></a>Confira também

- [Recuperando informações de esquema de banco de dados](retrieving-database-schema-information.md)
- [GetSchema e coleções de esquema](getschema-and-schema-collections.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
