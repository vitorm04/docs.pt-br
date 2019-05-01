---
title: Construtores de cadeia de conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 17ef057fccbea48da698e0ecfa5c789e125adbb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034535"
---
# <a name="connection-string-builders"></a>Construtores de cadeia de conexão
Em versões anteriores do [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]verificação de cadeias de caracteres de conexão com a cadeia de caracteres concatenada valores não tivesse ocorrido, para que no tempo de execução, uma palavra-chave incorreta gerada pelo tempo de compilação um <xref:System.ArgumentException>. Cada provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dava suporte a diferentes tipos de sintaxe de palavras-chave de cadeias de conexão, o que dificultava a construção de cadeias de conexão válidas manualmente. Para resolver esse problema, o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 introduziu novos construtores de cadeia de conexão para cada provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Cada provedor de dados inclui uma classe de construtor de cadeia de conexão fortemente tipada que herda de <xref:System.Data.Common.DbConnectionStringBuilder>. A tabela a seguir lista os provedores de dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e suas respectivas classes de construtores de cadeias de conexão.  
  
|Provider|Classe ConnectionStringBuilder|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>Ataques de injeção de cadeias de conexão  
 Um ataque de injeção de cadeia de conexão pode ocorrer quando a concatenação de cadeias dinâmicas é usada para criar cadeias de conexão com base na entrada do usuário. Se a cadeia de caracteres não for validada e o texto mal-intencionado ou os caracteres não forem escapados, um invasor poderá potencialmente acessar dados confidenciais ou outros recursos no servidor. Por exemplo, um invasor pode montar um ataque fornecendo um ponto e vírgula e acrescentando outro valor. A cadeia de conexão é analisada usando o algoritmo "o último vence", e a entrada hostil é substituída por um valor legítimo.  
  
 As classes de construtores de cadeias de conexão são criadas para eliminar hipóteses e proteger contra erros de sintaxe e vulnerabilidades à segurança. Elas fornecem métodos e propriedades que correspondem a pares chave-valor conhecidos e permitidos por cada provedor de dados. Cada classe mantém uma coleção fixa de sinônimos e pode converter um sinônimo no nome da chave conhecida correspondente. As verificações são executadas para pares chave-valor válidos e um par inválido gera uma exceção. Além disso, os valores injetados são tratados de maneira segura.  
  
 O exemplo a seguir demonstra como <xref:System.Data.SqlClient.SqlConnectionStringBuilder> trata um valor adicional inserido para a configuração `Initial Catalog`.  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 A saída mostra que <xref:System.Data.SqlClient.SqlConnectionStringBuilder> tratou esse valor corretamente colocando em uma sequência de escape, entre aspas duplas, o valor adicional, em vez de acrescentá-lo à cadeia de conexão como um novo par chave-valor.  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>Construindo cadeias de conexão a partir de arquivos de configuração  
 Se determinados elementos de uma cadeia de conexão forem conhecidos antecipadamente, eles poderão ser armazenados em um arquivo de configuração e recuperados em tempo de execução para construir uma cadeia de conexão completa. Por exemplo, o nome do banco de dados pode ser conhecido com antecedência, mas não o nome do servidor. Ou, talvez, você deseje que um usuário forneça um nome e uma senha em tempo de execução, sem que possa injetar outros valores na cadeia de conexão.  
  
 Um dos construtores sobrecarregados de um construtor de cadeias de conexão obtém um <xref:System.String> como argumento, o que permite a você fornecer uma cadeia de conexão parcial que depois poderá ser concluída pela entrada do usuário. A cadeia de conexão parcial pode ser armazenada em um arquivo de configuração e recuperada em tempo de execução.  
  
> [!NOTE]
>  O namespace <xref:System.Configuration> permite acesso programático aos arquivos de configuração que usam <xref:System.Web.Configuration.WebConfigurationManager> para aplicativos Web e <xref:System.Configuration.ConfigurationManager> para aplicativos do Windows. Para obter mais informações sobre como trabalhar com cadeias de caracteres de conexão e arquivos de configuração, consulte [cadeias de caracteres de Conexão e arquivos de configuração](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
### <a name="example"></a>Exemplo  
 Este exemplo demonstra como recuperar uma cadeia de conexão parcial de um arquivo de configuração e concluí-la definindo as propriedades <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A> e <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> do <xref:System.Data.SqlClient.SqlConnectionStringBuilder>. O arquivo de configuração é definido como a seguir.  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  Você deve definir uma referência à `System.Configuration.dll` em seu projeto para que o código seja executado.  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Cadeia de Conexão](../../../../docs/framework/data/adonet/connection-strings.md)
- [Privacidade e segurança de dados](../../../../docs/framework/data/adonet/privacy-and-data-security.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
