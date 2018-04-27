### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection não pode mais se conectar ao SQL Server 1997 ou a bancos de dados usando o adaptador VIA

|   |   |
|---|---|
|Detalhes|Conexões a bancos de dados do SQL Server usando o [Protocolo VIA (Virtual Interface Adapter)](https://technet.microsoft.com/library/ms191229%28v=sql.105%29.aspx) não têm mais suporte. O protocolo usado para se conectar a um banco de dados do SQL Server fica visível na cadeia de conexão. Uma conexão VIA conterá via:&lt;nomedoservidor&gt;. Se o aplicativo estiver se conectando ao SQL usando um protocolo diferente do VIA (tcp: ou np:, por exemplo), nenhuma alteração da falha será encontrada. Além disso, não há suporte para conexões com o SQL Server 7 (1997).|
|Sugestão|O protocolo VIA foi preterido, de modo que um protocolo alternativo deve ser usado para se conectar a bancos de dados SQL. O protocolo mais usado é o TCP/IP. Instruções para habilitar o protocolo TCP/IP podem ser encontradas [aqui](https://msdn.microsoft.com/library/bb909712.aspx). Se o banco de dados for acessado somente de dentro de uma intranet, o protocolo de pipes compartilhado poderá fornecer um melhor desempenho se a rede estiver lenta.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

