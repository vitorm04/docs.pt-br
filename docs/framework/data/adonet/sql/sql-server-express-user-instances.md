---
title: Instâncias de usuário do SQL Server Express
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: b456549daefa0fdf67524b0b039a091652cf41ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876272"
---
# <a name="sql-server-express-user-instances"></a>Instâncias de usuário do SQL Server Express
O Microsoft SQL Server Express Edition (SQL Server Express) dá suporte ao recurso de instância de usuário, que somente está disponível quando é usado o Provedor de Dados .NET Framework para SQL Server (`SqlClient`). Uma instância de usuário é uma instância separada do Mecanismo de Banco de Dados SQL Server Express que é gerado por uma instância pai. As instâncias de usuário permitem que usuários que não são administradores em seus computadores locais anexem e conectem-se aos bancos de dados SQL Server Express. Cada instância é executada no contexto de segurança do usuário individual, uma instância por usuário.  
  
## <a name="user-instance-capabilities"></a>Recursos de instância de usuário  
 As instâncias de usuário são úteis para os usuários que estão executando o Windows com uma conta de usuário de privilégios mínimos (LUA), pois cada usuário tem privilégios de administrador do sistema do SQL Server (`sysadmin`) na instância em execução em seu computador sem precisar ser também administrador do Windows. O software que é executado em uma instância de usuário com permissões limitadas não pode fazer alterações em todo o sistema porque a instância do SQL Server Express está sendo executada na conta do usuário do Windows que não é administrador, não como um serviço. Cada instância de usuário é isolada de sua instância pai e de todas as outras instâncias de usuário que são executadas no mesmo computador. Os bancos de dados que são executados em uma instância de usuário são abertos somente no modo de usuário único, e não é possível para vários usuários se conectarem a bancos de dados que são executados em uma instância de usuário. A replicação e as consultas distribuídas também são desativadas para instâncias de usuário.  
  
 Para obter mais informações, consulte “Instâncias de usuário” nos Manuais Online do SQL Server.  
  
> [!NOTE]
>  As instâncias de usuário não são necessárias para os usuários que já são administradores em seus próprios computadores ou para cenários que envolvem vários usuários do banco de dados.  
  
## <a name="enabling-user-instances"></a>Habilitando instâncias de usuário  
 Para gerar instâncias de usuário, uma instância pai do SQL Server Express deve estar em execução. Instâncias de usuário são habilitadas por padrão, quando o SQL Server Express é instalado, e eles podem ser explicitamente habilitados ou desabilitados pelo administrador do sistema executando o **sp_configure** procedimento armazenado do sistema na instância pai.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 O protocolo de rede para instâncias de usuário deve ser o Pipes Nomeados local. Uma instância de usuário não pode ser iniciada em uma instância remota do SQL Server e os logons do SQL Server não são permitidos.  
  
## <a name="connecting-to-a-user-instance"></a>Conectando-se a uma instância de usuário  
 O `User Instance` e `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> palavras-chave permitem que um <xref:System.Data.SqlClient.SqlConnection> para se conectar a uma instância de usuário. As instâncias de usuário também têm o suporte das propriedades <xref:System.Data.SqlClient.SqlConnectionStringBuilder>`UserInstance` e `AttachDBFilename`.  
  
 Observe o seguinte sobre a cadeia de conexão no exemplo mostrado abaixo:  
  
-   A palavra-chave `Data Source` refere-se à instância pai do SQL Server Express que está gerando a instância do usuário. A instância padrão é. \sqlexpress.  
  
-   `Integrated Security` é definido como `true`. Para se conectar a uma instância de usuário, a Autenticação do Windows é necessária; os logons do SQL Server não têm suporte.  
  
-   A `User Instance` é definida como `true`, o que invoca uma instância de usuário. (O padrão é `false`.)  
  
-   A palavra-chave de cadeia de conexão `AttachDbFileName` é usada para anexar o arquivo de banco de dados primário (.mdf), que deve incluir o nome do caminho completo. `AttachDbFileName` também corresponde às chaves "extended properties" e "initial file name" dentro de uma cadeia de conexão <xref:System.Data.SqlClient.SqlConnection>.  
  
-   A cadeia de caracteres de substituição `|DataDirectory|` incluída nos símbolos pipe refere-se ao diretório de dados do aplicativo que abre a conexão e fornece um caminho relativo que indica o local do banco de dados .mdf e .ldf e dos arquivos de log. Se você deseja localizar esses arquivos em outro lugar, deverá fornecer o caminho completo para os arquivos.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Você também pode usar as propriedades <xref:System.Data.SqlClient.SqlConnectionStringBuilder><xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> e <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> para compilar uma cadeia de conexão em tempo de execução.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Usando o &#124;DataDirectory&#124; cadeia de caracteres de substituição  
 `AttachDbFileName` foi ampliado no ADO.NET 2.0 com a introdução da cadeia de caracteres de substituição `|DataDirectory|` (entre barras verticais). `DataDirectory` é usado em conjunto com `AttachDbFileName` para indicar um caminho relativo para um arquivo de dados, permitindo que os desenvolvedores criem cadeias de conexão que são baseadas em um caminho relativo para a fonte de dados em vez de precisarem especificar um caminho completo.  
  
 A localização física para a qual o `DataDirectory` aponta depende do tipo de aplicativo. Nesse exemplo, o arquivo Northwind.mdf a ser anexado está localizado na pasta \app_data do aplicativo.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Quando `DataDirectory` é usado, o caminho do arquivo resultante não pode ser mais alto na estrutura de diretórios que o diretório apontado pela cadeia de caracteres de substituição. Por exemplo, se `DataDirectory` totalmente expandido for C:\AppDirectory\app_data, a cadeia de conexão de exemplo mostrada acima funcionará porque está abaixo de c:\AppDirectory. No entanto, tentar especificar `DataDirectory` como `|DataDirectory|\..\data` resultará em um erro porque \data não é um subdiretório de \appdirectory.  
  
 Se a cadeia de conexão tiver uma cadeia de caracteres de substituição formatada incorretamente, uma <xref:System.ArgumentException> será gerada.  
  
> [!NOTE]
>  <xref:System.Data.SqlClient> resolve as cadeias de caracteres de substituição em caminhos completos no sistema de arquivos do computador local. Portanto, os nomes do servidor remoto, de HTTP e do caminho UNC não têm suporte. Uma exceção será gerada quando a conexão for aberta se o servidor não estiver localizado no computador local.  
  
 Quando <xref:System.Data.SqlClient.SqlConnection> estiver aberto, ele será redirecionado da instância padrão do SQL Server Express para uma instância iniciada em tempo de execução que é executada na conta do chamador.  
  
> [!NOTE]
>  Pode ser necessário aumentar o valor de <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> porque as instâncias de usuários podem levar mais tempo para carregar que instâncias normais.  
  
 O fragmento de código a seguir abre uma nova `SqlConnection`, exibe a cadeia de conexão na janela do console e, em seguida, fecha a conexão ao sair do bloco de código `using`.  
  
```vb  
Private Sub OpenSqlConnection()  
    ' Retrieve the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Using connection As New SqlConnection(connectionString)  
        connection.Open()  
        Console.WriteLine("ConnectionString: {0}", _  
           connection.ConnectionString)  
    End Using  
End Sub  
```  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =   
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",   
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
>  As instâncias de usuário não têm suporte no código CLR (Common Language Runtime) que está sendo executado dentro do SQL Server. Uma <xref:System.InvalidOperationException> é gerada se `Open` é chamado em um <xref:System.Data.SqlClient.SqlConnection> que tem `User Instance=true` na cadeia de conexão.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Tempo de vida de uma conexão de instância de usuário  
 Ao contrário das versões do SQL Server que são executadas como um serviço, as instâncias do SQL Server Express não precisam ser iniciadas e interrompidas manualmente. Cada vez que um usuário faz logon e se conecta a uma instância de usuário, a instância do usuário é iniciada se já não estiver em execução. Os bancos de dados de instância de usuário têm a opção `AutoClose` definida de modo que o banco de dados seja fechado automaticamente após um período de inatividade. O processo do sqlservr.exe que é iniciado permanece em execução por um período limitado depois que a última conexão à instância é fechada, para que ele não precisa ser reiniciado se outra conexão for aberta antes de o tempo limite expirar. A instância do usuário será encerrada automaticamente se nenhuma nova conexão for aberta antes de o período de tempo limite expirar. Um administrador do sistema na instância pai pode definir a duração do período de tempo limite para uma instância de usuário utilizando **sp_configure** para alterar o **tempo limite de instância de usuário** opção. O padrão é 60 minutos.  
  
> [!NOTE]
>  Se `Min Pool Size` for usado na cadeia de conexão com um valor maior que zero, o pooler de conexão sempre manterá algumas conexões abertas e a instância do usuário não será fechada automaticamente.  
  
## <a name="how-user-instances-work"></a>Como as instâncias de usuário funcionam  
 Na primeira vez que uma instância de usuário é gerada para cada usuário, o **mestre** e **msdb** bancos de dados do sistema são copiados da pasta de dados de modelo para um caminho no repositório de dados de aplicativo local do usuário diretório para uso exclusivo da instância de usuário. Esse caminho normalmente é `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Quando uma instância de usuário é inicializado, o **tempdb**, registrar e rastrear arquivos também são gravados nesse diretório. Um nome é gerado para a instância, que deve ser exclusiva para cada usuário.  
  
 Por padrão, todos os membros do grupo Builtin\Users do Windows têm permissões para se conectarem à instância local bem como ler e executar permissões nos binários do SQL Server. Depois de as credenciais do usuário de chamada que hospeda a instância de usuário tiverem sido verificadas, o usuário torna-se `sysadmin` nessa instância. Somente a memória compartilhada é habilitada para instâncias de usuário, o que significa que somente operações no computador local são possíveis.  
  
 Os usuários devem ter permissões de leitura e gravação nos arquivos .mdf e .ldf especificados na cadeia de conexão.  
  
> [!NOTE]
>  Os arquivos .mdf e .ldf representam o banco de dados e os arquivos de log, respectivamente. Esses dois arquivos são um conjunto correspondente, portanto tome cuidado durante operações de backup e restauração. O arquivo de banco de dados contém informações sobre a versão exata do arquivo de log, e o banco de dados não será aberto se estiver agrupado com o arquivo de log incorreto.  
  
 Para evitar a corrupção de dados, um banco de dados na instância do usuário é aberto com acesso exclusivo. Se duas instâncias de usuário diferentes compartilharem o mesmo banco de dados no mesmo computador, o usuário na primeira instância deverá fechar o banco de dados antes de ser aberto em uma segunda instância.  
  
## <a name="user-instance-scenarios"></a>Cenários de instância de usuário  
 As instâncias de usuários fornecem aos desenvolvedores de aplicativos de banco de dados um armazenamento de dados do SQL Server que não depende de os desenvolvedores terem contas administrativas em seus computadores de desenvolvimento. As instâncias de usuário são baseadas no modelo Access/Jet, onde o aplicativo de banco de dados simplesmente se conecta a um arquivo, e o usuário automaticamente tem permissões completas em todos os objetos de banco de dados sem precisar da intervenção de um administrador do sistema para conceder permissões. Ele destina-se a funcionar em situações onde o usuário está executando em uma conta de usuário de privilégios mínimos (LUA) e não tem privilégios administrativos no servidor ou no computador local, mas precisa criar objetos de banco de dados e aplicativos. As instâncias de usuário permitem que os usuários criem as instâncias em tempo de execução que são executadas no próprio contexto de segurança do usuário, e não no contexto de segurança de um serviço do sistema mais privilegiado.  
  
> [!IMPORTANT]
>  As instâncias de usuário devem ser utilizadas somente em situações onde todos os aplicativos que as usam são totalmente confiáveis.  
  
 Os cenários de instância de usuário incluem:  
  
-   Qualquer aplicativo de usuário único onde compartilhar dados não é necessário.  
  
-   Implantação do ClickOnce. Se o .NET Framework 2.0 (ou posterior) e o SQL Server Express já estiver instalado no computador de destino, o pacote de instalação baixado como resultado de uma ação de ClickOnce poderá ser instalado e usado por usuários não administrativos. Observe que um administrador deve instalar o SQL Server Express se isso for parte da instalação. Para obter mais informações, consulte [implantação de ClickOnce para o Windows Forms](../../../winforms/clickonce-deployment-for-windows-forms.md).
  
-   ASP.NET dedicado hospedado usando a Autenticação do Windows. Uma única instância do SQL Server Express pode ser hospedada em uma intranet. O aplicativo conecta-se usando a conta ASPNET do Windows, não usando representação. As instâncias de usuário não devem ser usadas para os cenários de hospedagem compartilhados ou de terceiros onde todos os aplicativos compartilhariam a mesma instância de usuário e não permanecessem isolados entre si.  
  
## <a name="see-also"></a>Consulte também

- [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)
- [Cadeia de Conexão](../../../../../docs/framework/data/adonet/connection-strings.md)
- [Conectando a uma fonte de dados](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
