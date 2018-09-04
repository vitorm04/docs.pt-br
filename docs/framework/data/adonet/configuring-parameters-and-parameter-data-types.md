---
title: Configurando parâmetros e tipos de dados de parâmetro
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: 7bb68a7d08d983e93119804db6c1f5a01cd047c9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659383"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Configurando parâmetros e tipos de dados de parâmetro
Objetos de comando usam parâmetros para passar valores para instruções SQL ou procedimentos armazenados, fornecendo verificação de tipo e validação. Diferentemente do texto de comando, o parâmetro de entrada é tratado como um valor literal, não como código executável. Isso ajuda a proteger contra ataques de "Injeção de SQL", em que um invasor insere um comando que compromete a segurança no servidor em uma instrução SQL.  
  
 Os comandos parametrizados também podem melhorar o desempenho de execução da consulta, porque ajudam o servidor de banco de dados a corresponder exatamente ao comando de entrada com um plano de consulta em cache apropriado. Para obter mais informações, consulte [cache de plano de execução e reutilização](/sql/relational-databases/query-processing-architecture-guide#execution-plan-caching-and-reuse) e [parâmetros e reutilização de plano de execução](/sql/relational-databases/query-processing-architecture-guide#PlanReuse). Além dos benefícios de segurança e desempenho, os comandos parametrizados fornecem um método conveniente para organizar os valores passados para uma fonte de dados.  
  
 Um objeto <xref:System.Data.Common.DbParameter> pode ser criado usando o construtor ou adicionando-o ao <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> chamando o método `Add` da coleção <xref:System.Data.Common.DbParameterCollection>. O método `Add` utilizará como entrada argumentos de construtor ou um objeto de parâmetro existente, dependendo do provedor de dados.  
  
## <a name="supplying-the-parameterdirection-property"></a>Fornecendo a propriedade ParameterDirection  
 Ao adicionar parâmetros, você deverá fornecer uma propriedade <xref:System.Data.ParameterDirection> para parâmetros diferentes dos parâmetros de entrada. A tabela a seguir mostra os valores `ParameterDirection` que você pode usar com a enumeração <xref:System.Data.ParameterDirection>.  
  
|Nome do membro|Descrição|  
|-----------------|-----------------|  
|<xref:System.Data.ParameterDirection.Input>|O parâmetro é um parâmetro de entrada. Esse é o padrão.|  
|<xref:System.Data.ParameterDirection.InputOutput>|O parâmetro pode executar entrada e saída.|  
|<xref:System.Data.ParameterDirection.Output>|O parâmetro é um parâmetro de saída.|  
|<xref:System.Data.ParameterDirection.ReturnValue>|O parâmetro representa um valor de retorno de uma operação como um procedimento armazenado, uma função interna ou uma função definida pelo usuário.|  
  
## <a name="working-with-parameter-placeholders"></a>Trabalhando com espaços reservados de parâmetro  
 A sintaxe para espaços reservados de parâmetro depende da fonte de dados. Os provedores de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] manipulam a nomeação e a especificação de parâmetros e de espaços reservados de parâmetros de maneira diferente. Essa sintaxe é personalizada para uma fonte de dados específica, conforme descrito na tabela a seguir.  
  
|Provedor de dados|Sintaxe de nomeação de parâmetro|  
|-------------------|-----------------------------|  
|<xref:System.Data.SqlClient>|Usa parâmetros nomeados no formato `@` *parametername*.|  
|<xref:System.Data.OleDb>|Usa os marcadores de parâmetros posicionais indicados por um ponto de interrogação (`?`).|  
|<xref:System.Data.Odbc>|Usa os marcadores de parâmetros posicionais indicados por um ponto de interrogação (`?`).|  
|<xref:System.Data.OracleClient>|Usa parâmetros nomeados no formato `:` *parmname* (ou *parmname*).|  
  
## <a name="specifying-parameter-data-types"></a>Especificando tipos de dados do parâmetro  
 O tipo de dados de um parâmetro é específico para o provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Especificar o tipo converte o valor do `Parameter` para o tipo de provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] antes de passar o valor para a fonte de dados. Você também pode especificar o tipo de um `Parameter` genericamente definindo a propriedade `DbType` de um objeto `Parameter` para um <xref:System.Data.DbType> específico.  
  
 O tipo do provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] de um objeto `Parameter` é inferido do tipo do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] do `Value` do objeto de `Parameter` ou do `DbType` do objeto de `Parameter`. A tabela a seguir mostra o tipo inferido de `Parameter` baseado no objeto passado como o valor do `Parameter` ou `DbType` especificado.  
  
|Tipo do .NET Framework|DbType|SqlDbType|OleDbType|OdbcType|OracleType|  
|-------------------------|------------|---------------|---------------|--------------|----------------|  
|<xref:System.Boolean>|Boolean|Bit|Boolean|Bit|Byte|  
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|  
|byte[]|Binário|VarBinary`.` essa conversão implícita falhará se a matriz de bytes for maior que o tamanho máximo de um VarBinary, que é de 8000 bytes. Para matrizes de byte maiores que 8000 bytes, defina explicitamente o <xref:System.Data.SqlDbType>.|VarBinary|Binário|Raw|  
|<xref:System.Char>|``|Inferir um <xref:System.Data.SqlDbType> do char não tem suporte.|Char|Char|Byte|  
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|  
|<xref:System.DateTimeOffset>|DateTimeOffset|DateTimeOffset no SQL Server 2008. Inferir um <xref:System.Data.SqlDbType> de DateTimeOffset não tem suporte em versões do SQL Server anteriores ao SQL Server 2008.|||DateTime|  
|<xref:System.Decimal>|Decimal|Decimal|Decimal|Numeric|Número|  
|<xref:System.Double>|Duplo|Float|Duplo|Duplo|Duplo|  
|<xref:System.Single>|Simples|Real|Simples|Real|Float|  
|<xref:System.Guid>|Guid|UniqueIdentifier|Guid|UniqueIdentifier|Raw|  
|<xref:System.Int16>|Int16|SmallInt|SmallInt|SmallInt|Int16|  
|<xref:System.Int32>|Int32|int|int|int|Int32|  
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Número|  
|<xref:System.Object>|Objeto|Variante|Variante|Inferir um OdbcType de objeto não tem suporte.|Blob|  
|<xref:System.String>|Cadeia de Caracteres|NVarChar. Essa conversão implícita falhará se a cadeia de caracteres for maior do que o tamanho máximo de um NVarChar, que é 4000 caracteres. Para cadeias de caracteres maiores que 4000 caracteres, defina explicitamente o <xref:System.Data.SqlDbType>.|VarWChar|NVarChar|NVarChar|  
|<xref:System.TimeSpan>|Hora|Hora no SQL Server 2008. Inferir um <xref:System.Data.SqlDbType> de TimeSpan não tem suporte em versões do SQL Server anteriores ao SQL Server 2008.|DBTime|Hora|DateTime|  
|<xref:System.UInt16>|UInt16|Inferir um <xref:System.Data.SqlDbType> do UInt16 não tem suporte.|UnsignedSmallInt|int|UInt16|  
|<xref:System.UInt32>|UInt32|Inferir um <xref:System.Data.SqlDbType> do UInt32 não tem suporte.|UnsignedInt|BigInt|UInt32|  
|<xref:System.UInt64>|UInt64|Inferir um <xref:System.Data.SqlDbType> do UInt64 não tem suporte.|UnsignedBigInt|Numeric|Número|  
||AnsiString|VarChar|VarChar|VarChar|VarChar|  
||AnsiStringFixedLength|Char|Char|Char|Char|  
|``|Moeda|Money|Moeda|Inferir um `OdbcType` de `Currency` não tem suporte.|Número|  
|``|Date|Data no SQL Server 2008. Inferir um <xref:System.Data.SqlDbType> de Date não tem suporte em versões do SQL Server anteriores ao SQL Server 2008.|DBDate|Date|DateTime|  
|``|SByte|Inferir um <xref:System.Data.SqlDbType> do SByte não tem suporte.|TinyInt|Inferir um `OdbcType` do SByte não tem suporte.|SByte|  
||StringFixedLength|NChar|WChar|NChar|NChar|  
||Hora|Hora no SQL Server 2008. Inferir um <xref:System.Data.SqlDbType> de Time não tem suporte em versões do SQL Server anteriores ao SQL Server 2008.|DBTime|Hora|DateTime|  
||VarNumeric|Inferir um <xref:System.Data.SqlDbType> do VarNumeric não tem suporte.|VarNumeric|Inferir um `OdbcType` do VarNumeric não tem suporte.|Número|  
|tipo definido pelo usuário (um objeto com <xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Objeto ou cadeia de caracteres, dependendo do provedor (SqlClient sempre retorna um objeto, ODBC sempre retorna uma cadeia de caracteres e o provedor de dados gerenciados OleDb pode ver se|SqlDbType.Udt se <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> está presente, caso contrário Variant|OleDbType.VarWChar (se o valor for nulo); caso contrário OleDbType.Variant.|OdbcType.NVarChar|sem suporte|  
  
> [!NOTE]
>  Conversões de decimal para outros tipos são conversões de limitação que arredondam o valor decimal para o valor inteiro mais próximo de zero. Se o resultado da conversão não for representável no tipo de destino, um <xref:System.OverflowException> será gerado.  
  
> [!NOTE]
>  Quando você envia um valor de parâmetro nulo para o servidor, você deve especificar <xref:System.DBNull>, e não `null` (`Nothing` no Visual Basic). O valor nulo no sistema é um objeto vazio que não tem nenhum valor. <xref:System.DBNull> é usado para representar valores nulos. Para obter mais informações sobre valores nulos de banco de dados, consulte [manipulando valores nulos](../../../../docs/framework/data/adonet/sql/handling-null-values.md).  
  
## <a name="deriving-parameter-information"></a>Derivando informações de parâmetro  
 Os parâmetros também podem ser derivados de um procedimento armazenado usando a classe `DbCommandBuilder`. As classes `SqlCommandBuilder` e `OleDbCommandBuilder` fornecem um método estático, `DeriveParameters`, que preenche automaticamente a coleção de parâmetros de um objeto de comando que usa informações de parâmetro de um procedimento armazenado. Observe que `DeriveParameters` substitui qualquer informação de parâmetro existente para o comando.  
  
> [!NOTE]
>  Derivar informações de parâmetro provoca uma penalidade de desempenho porque exige ida e volta adicional à fonte de dados para recuperar as informações. Se as informações de parâmetro forem conhecidas em tempo de design, você poderá melhorar o desempenho do seu aplicativo definindo os parâmetros explicitamente.  
  
 Para obter mais informações, consulte [Gerando comandos com CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Usando parâmetros com um SqlCommand e um procedimento armazenado  
 Os procedimentos armazenados oferecem várias vantagens em aplicativos orientados a dados. Ao usar procedimentos armazenados, as operações de banco de dados podem ser encapsuladas em um único comando, otimizadas para melhor desempenho e aprimoradas com segurança adicional. Embora um procedimento armazenado pode ser chamado, passando o nome do procedimento armazenado seguido por argumentos de parâmetro como uma instrução SQL, usando o <xref:System.Data.Common.DbCommand.Parameters%2A> coleção do [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.Common.DbCommand> objeto permite que você definir mais explicitamente armazenado os parâmetros de procedimento e para acessar parâmetros de saída e valores de retorno.  
  
> [!NOTE]
> As instruções parametrizadas são executadas no servidor usando `sp_executesql,` que permite a reutilização do plano de consulta. Os cursores locais ou variáveis no lote `sp_executesql` não são visíveis para os lotes que chamam `sp_executesql`. As alterações no contexto de banco de dados duram somente até o final da instrução `sp_executesql`. Para obter mais informações, consulte [sp_executesql (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql).
  
 Ao usar parâmetros com um <xref:System.Data.SqlClient.SqlCommand> para executar um procedimento armazenado do SQL Server, os nomes dos parâmetros adicionados à coleção de <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> devem coincidir com os nomes dos marcadores de parâmetros no procedimento armazenado. O provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para o SQL Server não oferece suporte ao espaço reservado de ponto de interrogação (?) para passar parâmetros para uma instrução SQL ou procedimento armazenado. Ele trata parâmetros no procedimento armazenado como parâmetros nomeados e procura marcadores de parâmetro compatíveis. Por exemplo, o procedimento armazenado `CustOrderHist` é definido usando um parâmetro chamado `@CustomerID`. Quando o código executar o procedimento armazenado, também deverá usar um parâmetro chamado `@CustomerID`.  
  
```  
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)  
```  
  
### <a name="example"></a>Exemplo  
 Este exemplo demonstra como chamar um procedimento armazenado do SQL Server no banco de dados de exemplo `Northwind`. O nome do procedimento armazenado é `dbo.SalesByCategory` e tem um parâmetro de entrada chamado `@CategoryName` com um tipo de dados de `nvarchar(15)`. O código cria um novo <xref:System.Data.SqlClient.SqlConnection> dentro de um bloco using para que a conexão seja descartada quando o procedimento terminar. Os objetos <xref:System.Data.SqlClient.SqlCommand> e <xref:System.Data.SqlClient.SqlParameter> são criados e suas propriedades são definidas. Um <xref:System.Data.SqlClient.SqlDataReader> executa o `SqlCommand` e retorna o conjunto de resultados do procedimento armazenado, exibindo a saída na janela do console.  
  
> [!NOTE]
>  Em vez de criar objetos `SqlCommand` e `SqlParameter` e depois definir as propriedades em instruções separadas, você poderá eleger usar um dos construtores sobrecarregados para definir várias propriedades em uma única instrução.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Usando parâmetros com um OleDbCommand ou um OdbcCommand  
 Ao usar parâmetros com um <xref:System.Data.OleDb.OleDbCommand> ou <xref:System.Data.Odbc.OdbcCommand>, a ordem dos parâmetros adicionados à coleção de `Parameters` deve coincidir com a ordem dos parâmetros definidos no procedimento armazenado. O Provedor de Dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB e o provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para ODBC lidam com parâmetros em um procedimento armazenado como espaços reservados e aplicam valores de parâmetro na ordem. Além disso, os parâmetros do valor de retorno devem ser os primeiros parâmetros adicionados à coleção de `Parameters`.  
  
 O provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB e o provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para ODBC não oferecem suporte aos parâmetros nomeados para passar parâmetros para uma instrução SQL ou procedimento armazenado. Nesse caso, você deverá usar o espaço reservado de ponto de interrogação (?), como no exemplo a seguir.  
  
```  
SELECT * FROM Customers WHERE CustomerID = ?  
```  
  
 Como resultado, a ordem na qual os objetos `Parameter` são adicionados à coleção de `Parameters` deve corresponder diretamente à posição do espaço reservado do ? para o parâmetro.  
  
### <a name="oledb-example"></a>Exemplo de OleDb  
  
```vb  
Dim command As OleDbCommand = New OleDbCommand( _  
  "SampleProc", connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As OleDbParameter = command.Parameters.Add( _  
  "RETURN_VALUE", OleDbType.Integer)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OleDbType.VarChar, 12)  
parameter.Value = "Sample Value"  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OleDbType.VarChar, 28)  
parameter.Direction = ParameterDirection.Output  
```  
  
```csharp  
OleDbCommand command = new OleDbCommand("SampleProc", connection);  
command.CommandType = CommandType.StoredProcedure;  
  
OleDbParameter parameter = command.Parameters.Add(  
  "RETURN_VALUE", OleDbType.Integer);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@InputParm", OleDbType.VarChar, 12);  
parameter.Value = "Sample Value";  
  
parameter = command.Parameters.Add(  
  "@OutputParm", OleDbType.VarChar, 28);  
parameter.Direction = ParameterDirection.Output;  
```  
  
## <a name="odbc-example"></a>Exemplo de ODBC  
  
```vb  
Dim command As OdbcCommand = New OdbcCommand( _  
  "{ ? = CALL SampleProc(?, ?) }", connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As OdbcParameter = command.Parameters.Add("RETURN_VALUE", OdbcType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OdbcType.VarChar, 12)  
parameter.Value = "Sample Value"  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OdbcType.VarChar, 28)  
parameter.Direction = ParameterDirection.Output  
```  
  
```csharp  
OdbcCommand command = new OdbcCommand( _  
  "{ ? = CALL SampleProc(?, ?) }", connection);  
command.CommandType = CommandType.StoredProcedure;  
  
OdbcParameter parameter = command.Parameters.Add( _  
  "RETURN_VALUE", OdbcType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OdbcType.VarChar, 12);  
parameter.Value = "Sample Value";  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OdbcType.VarChar, 28);  
parameter.Direction = ParameterDirection.Output;  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Parâmetros DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
