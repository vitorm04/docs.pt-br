---
title: Contadores de Desempenho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 985951180a5c8ee09460b7fe4bf3213b986c3bb6
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980061"
---
# <a name="performance-counters-in-adonet"></a>Contadores de desempenho no ADO.NET
O ADO.NET 2,0 introduziu suporte expandido para contadores de desempenho que incluem suporte para <xref:System.Data.SqlClient> e <xref:System.Data.OracleClient>. Os contadores de desempenho <xref:System.Data.SqlClient> disponíveis nas versões anteriores do ADO.NET foram preteridos e substituídos pelos novos contadores de desempenho discutidos neste tópico. Você pode usar contadores de desempenho ADO.NET para monitorar o status do seu aplicativo e os recursos de conexão que ele usa. Os contadores de desempenho podem ser monitorados usando o monitor de desempenho do Windows ou podem ser acessados programaticamente usando a classe <xref:System.Diagnostics.PerformanceCounter> no namespace <xref:System.Diagnostics>.  
  
## <a name="available-performance-counters"></a>Contadores de desempenho disponíveis  
 Atualmente, há 14 contadores de desempenho diferentes disponíveis para <xref:System.Data.SqlClient> e <xref:System.Data.OracleClient>, conforme descrito na tabela a seguir. Observe que os nomes dos contadores individuais não são localizados em versões regionais do Microsoft .NET Framework.  
  
|Contador de desempenho|Descrição|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|O número de conexões por segundo que estão sendo feitas a um servidor de banco de dados.|  
|`HardDisconnectsPerSecond`|O número de desconexões por segundo que estão sendo feitas em um servidor de banco de dados.|  
|`NumberOfActiveConnectionPoolGroups`|O número de grupos de pools de conexão exclusivos que estão ativos. Esse contador é controlado pelo número de cadeias de conexão exclusivas encontradas no AppDomain.|  
|`NumberOfActiveConnectionPools`|O número total de pools de conexão.|  
|`NumberOfActiveConnections`|O número de conexões ativas que estão em uso no momento. **Observação:**  Esse contador de desempenho não está habilitado por padrão. Para habilitar esse contador de desempenho, consulte [ativando contadores desativados por padrão](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|O número de conexões disponíveis para uso nos pools de conexão. **Observação:**  Esse contador de desempenho não está habilitado por padrão. Para habilitar esse contador de desempenho, consulte [ativando contadores desativados por padrão](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|O número de grupos de pools de conexão exclusivos que estão marcados para remoção. Esse contador é controlado pelo número de cadeias de conexão exclusivas encontradas no AppDomain.|  
|`NumberOfInactiveConnectionPools`|O número de pools de conexão inativos que não tiveram nenhuma atividade recente e que estão aguardando para serem descartados.|  
|`NumberOfNonPooledConnections`|O número de conexões ativas que não estão em pool.|  
|`NumberOfPooledConnections`|O número de conexões ativas que estão sendo gerenciadas pela infraestrutura de pooling de conexão.|  
|`NumberOfReclaimedConnections`|O número de conexões que foram recuperadas por meio da coleta de lixo em que `Close` ou `Dispose` não foi chamado pelo aplicativo. Não fechar ou descartar explicitamente as conexões afeta o desempenho.|  
|`NumberOfStasisConnections`|O número de conexões que estão aguardando a conclusão de uma ação e que, portanto, não estão disponíveis para uso pelo seu aplicativo.|  
|`SoftConnectsPerSecond`|O número de conexões ativas sendo extraídas do pool de conexões. **Observação:**  Esse contador de desempenho não está habilitado por padrão. Para habilitar esse contador de desempenho, consulte [ativando contadores desativados por padrão](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|O número de conexões ativas que estão sendo retornadas para o pool de conexões. **Observação:**  Esse contador de desempenho não está habilitado por padrão. Para habilitar esse contador de desempenho, consulte [ativando contadores desativados por padrão](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Grupos de pools de conexão e pools de conexão  
 Ao usar a autenticação do Windows (segurança integrada), você deve monitorar os contadores de desempenho `NumberOfActiveConnectionPoolGroups` e `NumberOfActiveConnectionPools`. O motivo é que os grupos do pool de conexões são mapeados para cadeias de conexão exclusivas. Quando a segurança integrada é usada, os pools de conexão são mapeados para cadeias de conexão e também criam pools separados para identidades individuais do Windows. For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie. If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a>Activating Off-By-Default Counters  
 The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default. Add the following information to the application's configuration file to enable them:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Retrieving Performance Counter Values  
 The following console application shows how to retrieve performance counter values in your application. Connections must be open and active for information to be returned for all of the ADO.NET performance counters.  
  
> [!NOTE]
> This example uses the sample **AdventureWorks** database included with SQL Server. The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings. You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication. Modify the connection strings as necessary to suit your environment.  
  
### <a name="example"></a>Exemplo  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.   
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.   
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\   
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's   
        'FriendlyName. Replace the line above that sets the instanceName with this:   
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrieve it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrieve it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrieve it from a configuration file.   
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  

```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's   
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
          "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  

## <a name="see-also"></a>Veja também

- [Conectando a uma fonte de dados](connecting-to-a-data-source.md)
- [Conexão do Oracle, ODBC e OLE DB Pooling](ole-db-odbc-and-oracle-connection-pooling.md)
- [Performance Counters for ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))
- [Criação de perfil do runtime](../../debug-trace-profile/runtime-profiling.md)
- [Introduction to Monitoring Performance Thresholds](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
