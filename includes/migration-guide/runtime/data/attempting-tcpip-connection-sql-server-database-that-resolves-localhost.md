### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Falha ao tentar uma conexão TCP/IP com um banco de dados do SQL Server resolvida para `localhost`

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6 e 4.6.1, tentar uma conexão TCP/IP com um banco de dados do SQL Server resolvida para <code>localhost</code> falha com o erro &quot;Ocorreu um erro relacionado à rede ou específico da instância durante o estabelecimento de uma conexão com o SQL Server. O servidor não foi encontrado ou não estava acessível. Verifique se o nome da instância está correto e se o SQL Server está configurado para permitir conexões remotas. (provedor: Adaptadores de Rede do SQL, erro: 26 – Erro ao Localizar Servidor/Instância Especificada)&quot;|
|Sugestão|Esse problema foi resolvido e o comportamento anterior restaurado no .NET Framework 4.6.2. Para se conectar a um banco de dados do SQL Server que seja resolvido para <code>localhost</code>, faça upgrade para o .NET Framework 4.6.2.|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Tempo de execução|

