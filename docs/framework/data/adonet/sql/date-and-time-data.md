---
title: Dados de data e hora
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 2130c79ba79ce7e327a2a1b3adccd92e52153d85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="date-and-time-data"></a>Dados de data e hora
O SQL Server 2008 apresenta novos tipos de dados para manipular as informações de data e hora. Os novos tipos de dados incluem tipos separados para data e hora, e tipos de dados expandidos com maior intervalo, precisão e reconhecimento de fuso horário. A partir do .NET Framework versão 3.5 Service Pack (SP) 1, o Provedor de Dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>) oferece suporte completo para todos os novos recursos do Mecanismo de Banco de Dados do SQL Server 2008. Você deve instalar o .NET Framework 3.5 SP1 (ou posterior) para usar esses novos recursos com o SqlClient.  
  
 As versões do SQL Server anteriores ao SQL Server 2008 tinham apenas dois tipos de dados para trabalhar com valores de data e hora: `datetime` e `smalldatetime`. Os dois tipos de dados contêm tanto o valor de data e o valor de hora, o que dificulta trabalhar com apenas valores de data ou apenas valores de hora. Além disso, esses tipos de dados apenas dão suporte às datas que ocorrem após a introdução do calendário gregoriano na Inglaterra em 1753. Outra restrição é que esses tipos de dados mais antigos não têm reconhecimento de fuso horário, o que dificulta trabalhar com dados que são originados de vários fusos horários.  
  
 A documentação completa para os tipos de dados do SQL Server está disponível nos Manuais Online do SQL Server. A tabela a seguir lista os tópicos básicos específicos de versão para dados de data e hora.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
1.  [Usando dados de data e hora](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Tipos de dados de data/hora introduzidos no SQL Server 2008  
 A tabela a seguir descreve os novos tipos de dados de data e hora.  
  
|Tipo de dados do SQL Server|Descrição|  
|--------------------------|-----------------|  
|`date`|O tipo de dados `date` tem um intervalo de 1 de janeiro de 01 a 31 de dezembro de 9999 com uma precisão de 1 dia. O valor padrão é 1 de janeiro de 1900. O tamanho do armazenamento é 3 bytes.|  
|`time`|O tipo de dados `time` armazena apenas valores de hora, com base em um relógio de 24 horas. O tipo de dados `time` tem um intervalo de 00:00:00,0000000 a 23:59:59,9999999 com uma precisão de 100 nanossegundos. O valor padrão é 00:00:00,0000000 (meia-noite). O tipo de dados `time` oferece suporte à precisão de segundos fracionária definida pelo usuário, e o tamanho de armazenamento varia de 3 a 6 bytes dependendo da precisão especificada.|  
|`datetime2`|O tipo de dados `datetime2` combina o intervalo e a precisão dos tipos de dados `date` e `time` em um único tipo de dados.<br /><br /> Os formatos de valores padrão e literal de cadeia de caracteres são os mesmos que os definidos nos tipos de dados `date` e `time`.|  
|`datetimeoffset`|O tipo de dados `datetimeoffset` tem todos os recursos de `datetime2` com um deslocamento adicional de fuso horário. O deslocamento de fuso horário é representado como [+&#124;-] hh: mm. HH significa 2 dígitos variando de 00 a 14, que representa o número de horas no deslocamento de fuso horário. MM significa 2 dígitos variando de 00 a 59, que representa o número de minutos adicionais no deslocamento de fuso horário. Os formatos de hora têm suporte para 100 nanossegundos. O sinal de + ou - obrigatório indica se o deslocamento de fuso horário é adicionado ou subtraído do UTC (Tempo Universal Coordenado ou Horário do Meridiano de Greenwich) para obter a hora local.|  
  
> [!NOTE]
>  Para obter mais informações sobre como usar a palavra-chave `Type System Version`, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Formato de data e ordem de data  
 A maneira como o SQL Server analisa os valores de data e hora depende não apenas da versão do sistema de tipos e da versão do servidor, mas também das configurações de formato e idioma padrão do servidor. Uma cadeia de caracteres de data que funciona para formatos de data de uma linguagem poderá ser irreconhecível se a consulta for executada por uma conexão que usa uma configuração diferente de idioma e formato de data.  
  
 A instrução SET LANGUAGE do Transact-SQL define implicitamente o DATEFORMAT que determina a ordem das partes de data. Você pode usar a instrução SET DATEFORMAT do Transact-SQL em uma conexão para remover a ambiguidade de valores de data ordenando as partes de data como MDY, DMY, YMD, YDM, MYD, ou DYM.  
  
 Se você não especificar nenhum DATEFORMAT para a conexão, o SQL Server usará o idioma padrão associado com a conexão. Por exemplo, uma cadeia de caracteres de data '01/02/03' seria interpretada como MDY (2 de janeiro de 2003) em um servidor com a configuração de idioma do inglês dos EUA e como DMY (1º de fevereiro de 2003) em um servidor com a configuração de idioma inglês britânico. O ano é determinado usando a regra de ano de corte do SQL Server, que define a data de corte para atribuir o valor do século. Para obter mais informações, consulte [opção two-digit year cutoff](http://go.microsoft.com/fwlink/?LinkId=120473) nos Manuais Online do SQL Server.  
  
> [!NOTE]
>  O formato de data de YDM não tem suporte ao converter de um formato de cadeia de caracteres para `date`, `time`, `datetime2` ou `datetimeoffset`.  
  
 Para obter mais informações sobre como o SQL Server interpreta os dados de data e hora, consulte [usando dados de data e hora](http://go.microsoft.com/fwlink/?LinkID=98361) nos Manuais Online do SQL Server 2008.  
  
## <a name="datetime-data-types-and-parameters"></a>Parâmetros e tipos de dados de data/hora  
 As seguintes enumerações foram adicionadas ao <xref:System.Data.SqlDbType> para oferecer suporte aos novos tipos de dados de data e hora.  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  

Você pode especificar o tipo de dados de um <xref:System.Data.SqlClient.SqlParameter> usando um dos anteriores <xref:System.Data.SqlDbType> enumerações. 

> [!NOTE]
> Não é possível definir o `DbType` propriedade de um `SqlParameter` para `SqlDbType.Date`.

 Você também pode especificar o tipo de um <xref:System.Data.SqlClient.SqlParameter> genericamente definindo a propriedade <xref:System.Data.SqlClient.SqlParameter.DbType%2A> de um objeto `SqlParameter` para um valor de enumeração específico de <xref:System.Data.DbType>. Os seguintes valores de enumeração foram adicionados ao <xref:System.Data.DbType> para dar suporte aos tipos de dados `datetime2` e `datetimeoffset`:  
  
-   DbType.DateTime2  
  
-   DbType.DateTimeOffset  
  
 Essas novas enumerações suplementam as enumerações `Date`, `Time` e `DateTime`, que existiam em versões anteriores do .NET Framework.  
  
 O tipo do provedor de dados do .NET Framework de um objeto de parâmetro é inferido do tipo do .NET Framework do valor do objeto de parâmetro ou do `DbType` do objeto de parâmetro. Nenhum novo tipo de dados <xref:System.Data.SqlTypes> foi introduzido para oferecer suporte aos novos tipos de dados de data e hora. A tabela a seguir descreve os mapeamentos entre os tipos de dados de data e hora do SQL Server 2008 e os tipos de dados CLR.  
  
|Tipo de dados do SQL Server|Tipo do .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.DateTime|Date|Date|  
|hora|System.TimeSpan|Hora|Hora|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Propriedades do SqlParameter  
 A tabela a seguir descreve as propriedades do `SqlParameter` que são relevantes para os tipos de dados de data e hora.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Obtém ou define se um valor é anulável. Quando você envia um valor do parâmetro nulo para o servidor, deve especificar <xref:System.DBNull>, em vez de `null` (`Nothing` no Visual Basic). Para obter mais informações sobre valores nulos de banco de dados, consulte [tratar valores nulos](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Obtém ou define o número máximo de dígitos usados para representar o valor. Essa configuração é ignorada para tipos de dados de data e hora.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Obtém ou define o número de casas decimais para o qual a parte de hora do valor é resolvida para `Time`, `DateTime2`, e `DateTimeOffset`. O valor padrão é 0, o que significa que a escala real é inferida do valor e enviada para o servidor.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignorado para tipos de dados de data e hora.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Obtém ou define o valor do parâmetro.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Obtém ou define o valor do parâmetro.|  
  
> [!NOTE]
>  Os valores de hora que são menores que zero ou maiores ou iguais a 24 horas gerarão um <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Criando parâmetros  
 Você pode criar um objeto <xref:System.Data.SqlClient.SqlParameter> usando o construtor ou adicionando-o a uma coleção de <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> chamando o método `Add` do <xref:System.Data.SqlClient.SqlParameterCollection>. O método `Add` utilizará como entrada argumentos de construtor ou um objeto de parâmetro existente.  
  
 As seções seguintes neste tópico fornecem exemplos de como especificar parâmetros de data e hora. Para obter exemplos adicionais de trabalhar com parâmetros, consulte [Configurando parâmetros e tipos de dados do parâmetro](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) e [parâmetros DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
### <a name="date-example"></a>Exemplo de data  
 O fragmento de código a seguir demonstra como especificar um parâmetro `date`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a>Exemplo de hora  
 O fragmento de código a seguir demonstra como especificar um parâmetro `time`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Exemplo de Datetime2  
 O fragmento de código a seguir demonstra como especificar um parâmetro `datetime2` com partes de data e hora.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>Exemplo de DateTimeOffSet  
 O fragmento de código a seguir demonstra como especificar um parâmetro `DateTimeOffSet` com um deslocamento de data, hora e fuso horário de 0.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
 Você também pode fornecer parâmetros usando o método `AddWithValue` de um <xref:System.Data.SqlClient.SqlCommand>, conforme mostrado no fragmento de código a seguir. No entanto, o método `AddWithValue` não permite que você especifique <xref:System.Data.SqlClient.SqlParameter.DbType%2A> ou <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> para o parâmetro.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 O `@date` pôde mapear o parâmetro para um `date`, `datetime`, ou `datetime2` tipo de dados no servidor. Ao trabalhar com os novos tipos de dados `datetime`, você deverá explicitamente definir a propriedade <xref:System.Data.SqlDbType> do parâmetro para o tipo de dados da instância. Usar <xref:System.Data.SqlDbType.Variant> ou implicitamente fornecer valores de parâmetro pode causar problemas com a compatibilidade com versões anteriores com os tipos de dados `datetime` e `smalldatetime`.  
  
 A tabela a seguir mostra quais `SqlDbTypes` são inferidos de quais tipos CLR:  
  
|Tipo CLR|SqlDbType inferido|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Recuperando dados de data e hora  
 A tabela a seguir descreve os métodos que são usados para recuperar os valores de data e hora do SQL Server 2008.  
  
|Método SqlClient|Descrição|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Recupera o valor de coluna especificado como uma estrutura de <xref:System.DateTime>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Recupera o valor de coluna especificado como uma estrutura de <xref:System.DateTimeOffset>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Retorna o tipo que é específico do provedor subjacente para o campo. Retorna os mesmos tipos que `GetFieldType` para novos tipos de data e hora.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Recupera o valor da coluna especificada. Retorna os mesmos tipos que `GetValue` para os novos tipos de data e hora.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Recupera os valores na matriz especificada.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Recupera o valor da coluna como um <xref:System.Data.SqlTypes.SqlString>. Um <xref:System.InvalidCastException> ocorrerá se os dados não puderem ser expressos como um `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Recupera dados da coluna como seu `SqlDbType` padrão. Retorna os mesmos tipos que `GetValue` para os novos tipos de data e hora.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Recupera os valores na matriz especificada.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Recupera o valor da coluna como uma cadeia de caracteres se a versão do sistema de tipos é definida como o SQL Server 2005. Um <xref:System.InvalidCastException> ocorrerá se os dados não puderem ser expressos como uma cadeia de caracteres.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Recupera o valor de coluna especificado como uma estrutura de <xref:System.TimeSpan>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Recupera o valor de coluna especificado como seu tipo CLR subjacente.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Recupera valores de coluna em uma matriz.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Retorna um <xref:System.Data.DataTable> que descreve os metadados do conjunto de resultados.|  
  
> [!NOTE]
>  Os novos `SqlDbTypes` de data e hora não têm suporte para o código que é executado no processo no SQL Server. Uma exceção será gerada se um desses tipos for passado para o servidor.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Especificando valores de data e hora como literais  
 Você pode especificar tipos de dados de data e hora usando uma variedade de formatos diferentes de cadeia de caracteres literal, que o SQL Server em seguida avalia em tempo de execução, convertendo-os para as estruturas internas de data/hora. O SQL Server reconhece os dados de data e hora que estão incluídos entre aspas simples ('). Os seguintes exemplos demonstram alguns formatos:  
  
-   Formatos de data alfabéticos, como `'October 15, 2006'`.  
  
-   Formatos de data numéricos, como `'10/15/2006'`.  
  
-   Formatos de cadeia de caracteres não separadas, como `'20061015'`, que poderiam ser interpretados como 15 de outubro de 2006 se você estivesse usando o formato de data padrão ISO.  
  
> [!NOTE]
>  Você pode encontrar a documentação completa para todos os formatos de cadeia de caracteres literal e outros recursos de tipos de dados de data e hora nos Manuais Online do SQL Server.  
  
 Os valores de hora que são menores que zero ou maiores ou iguais a 24 horas gerarão um <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Recursos nos Manuais Online do SQL Server 2008  
 Para obter mais informações sobre como trabalhar com valores de data e hora no SQL Server 2008, consulte os seguintes recursos nos Manuais Online do SQL Server 2008.  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Dados de data e hora tipos e funções (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98360)|Fornece uma visão geral de todos os tipos e as funções de dados de data e hora de Transact-SQL.|  
|[Usando dados de data e hora](http://go.microsoft.com/fwlink/?LinkId=98361)|Fornece informações sobre os tipos e as funções de dados de data e hora, e exemplos de como usá-los.|  
|[Tipos de dados (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98362)|Descreve os tipos de dados do sistema no SQL Server 2008.|  
  
## <a name="see-also"></a>Consulte também  
 [Mapeamentos de tipo de dados do SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Configurando parâmetros e tipos de dados de parâmetro](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
