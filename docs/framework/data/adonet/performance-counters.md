---
title: Contadores de desempenho
description: Use contadores de desempenho ADO.NET para monitorar o status do aplicativo e seus recursos de conexão usando o monitor de desempenho do Windows ou programaticamente.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 4f645a51996078f8dd80b6c455c420633db36155
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164592"
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="df201-103">Contadores de desempenho no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="df201-103">Performance Counters in ADO.NET</span></span>

<span data-ttu-id="df201-104">O ADO.NET 2,0 introduziu suporte expandido para contadores de desempenho que incluem suporte para o <xref:System.Data.SqlClient> e o <xref:System.Data.OracleClient> .</span><span class="sxs-lookup"><span data-stu-id="df201-104">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="df201-105">Os <xref:System.Data.SqlClient> contadores de desempenho disponíveis nas versões anteriores do ADO.net foram preteridos e substituídos pelos novos contadores de desempenho discutidos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="df201-105">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="df201-106">Você pode usar contadores de desempenho ADO.NET para monitorar o status do seu aplicativo e os recursos de conexão que ele usa.</span><span class="sxs-lookup"><span data-stu-id="df201-106">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="df201-107">Os contadores de desempenho podem ser monitorados usando o monitor de desempenho do Windows ou podem ser acessados programaticamente usando a <xref:System.Diagnostics.PerformanceCounter> classe no <xref:System.Diagnostics> namespace.</span><span class="sxs-lookup"><span data-stu-id="df201-107">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="df201-108">Contadores de desempenho disponíveis</span><span class="sxs-lookup"><span data-stu-id="df201-108">Available Performance Counters</span></span>  

 <span data-ttu-id="df201-109">Atualmente, há 14 diferentes contadores de desempenho disponíveis <xref:System.Data.SqlClient> para <xref:System.Data.OracleClient> o e conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="df201-109">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="df201-110">Observe que os nomes dos contadores individuais não são localizados em versões regionais do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="df201-110">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="df201-111">Contador de desempenho</span><span class="sxs-lookup"><span data-stu-id="df201-111">Performance counter</span></span>|<span data-ttu-id="df201-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="df201-112">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="df201-113">O número de conexões por segundo que estão sendo feitas a um servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="df201-113">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="df201-114">O número de desconexões por segundo que estão sendo feitas em um servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="df201-114">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="df201-115">O número de grupos de pools de conexão exclusivos que estão ativos.</span><span class="sxs-lookup"><span data-stu-id="df201-115">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="df201-116">Esse contador é controlado pelo número de cadeias de conexão exclusivas encontradas no AppDomain.</span><span class="sxs-lookup"><span data-stu-id="df201-116">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="df201-117">O número total de pools de conexão.</span><span class="sxs-lookup"><span data-stu-id="df201-117">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="df201-118">O número de conexões ativas que estão em uso no momento.</span><span class="sxs-lookup"><span data-stu-id="df201-118">The number of active connections that are currently in use.</span></span> <span data-ttu-id="df201-119">**Observação:**  Esse contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="df201-119">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="df201-120">Para habilitar esse contador de desempenho, consulte [ativando contadores desativados por padrão](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="df201-120">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="df201-121">O número de conexões disponíveis para uso nos pools de conexão.</span><span class="sxs-lookup"><span data-stu-id="df201-121">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="df201-122">**Observação:**  Esse contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="df201-122">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="df201-123">Para habilitar esse contador de desempenho, consulte [ativando contadores desativados por padrão](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="df201-123">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="df201-124">O número de grupos de pools de conexão exclusivos que estão marcados para remoção.</span><span class="sxs-lookup"><span data-stu-id="df201-124">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="df201-125">Esse contador é controlado pelo número de cadeias de conexão exclusivas encontradas no AppDomain.</span><span class="sxs-lookup"><span data-stu-id="df201-125">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="df201-126">O número de pools de conexão inativos que não tiveram nenhuma atividade recente e que estão aguardando para serem descartados.</span><span class="sxs-lookup"><span data-stu-id="df201-126">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="df201-127">O número de conexões ativas que não estão em pool.</span><span class="sxs-lookup"><span data-stu-id="df201-127">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="df201-128">O número de conexões ativas que estão sendo gerenciadas pela infraestrutura de pooling de conexão.</span><span class="sxs-lookup"><span data-stu-id="df201-128">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="df201-129">O número de conexões que foram recuperadas por meio da coleta de lixo onde `Close` ou `Dispose` não foi chamado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df201-129">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="df201-130">Não fechar ou descartar explicitamente as conexões afeta o desempenho.</span><span class="sxs-lookup"><span data-stu-id="df201-130">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="df201-131">O número de conexões que estão aguardando a conclusão de uma ação e que, portanto, não estão disponíveis para uso pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df201-131">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="df201-132">O número de conexões ativas sendo extraídas do pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="df201-132">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="df201-133">**Observação:**  Esse contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="df201-133">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="df201-134">Para habilitar esse contador de desempenho, consulte [ativando contadores desativados por padrão](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="df201-134">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="df201-135">O número de conexões ativas que estão sendo retornadas para o pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="df201-135">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="df201-136">**Observação:**  Esse contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="df201-136">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="df201-137">Para habilitar esse contador de desempenho, consulte [ativando contadores desativados por padrão](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="df201-137">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="df201-138">Grupos de pools de conexão e pools de conexão</span><span class="sxs-lookup"><span data-stu-id="df201-138">Connection Pool Groups and Connection Pools</span></span>  

 <span data-ttu-id="df201-139">Ao usar a autenticação do Windows (segurança integrada), você deve monitorar `NumberOfActiveConnectionPoolGroups` os `NumberOfActiveConnectionPools` contadores de desempenho e.</span><span class="sxs-lookup"><span data-stu-id="df201-139">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="df201-140">O motivo é que os grupos do pool de conexões são mapeados para cadeias de conexão exclusivas.</span><span class="sxs-lookup"><span data-stu-id="df201-140">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="df201-141">Quando a segurança integrada é usada, os pools de conexão são mapeados para cadeias de conexão e também criam pools separados para identidades individuais do Windows.</span><span class="sxs-lookup"><span data-stu-id="df201-141">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="df201-142">Por exemplo, se Fred e Julie, cada um dentro do mesmo AppDomain, ambos usam a cadeia de conexão `"Data Source=MySqlServer;Integrated Security=true"` , um grupo de pools de conexão é criado para a cadeia de conexão e dois pools adicionais são criados, um para Fred e outro para Julie.</span><span class="sxs-lookup"><span data-stu-id="df201-142">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="df201-143">Se João e Martha usarem uma cadeia de conexão com um logon de SQL Server idêntico, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"` apenas um único pool será criado para a identidade **lowPrivUser** .</span><span class="sxs-lookup"><span data-stu-id="df201-143">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>

### <a name="activating-off-by-default-counters"></a><span data-ttu-id="df201-144">Ativando contadores desativados por padrão</span><span class="sxs-lookup"><span data-stu-id="df201-144">Activating Off-By-Default Counters</span></span>  

 <span data-ttu-id="df201-145">Os contadores de desempenho `NumberOfFreeConnections` , `NumberOfActiveConnections` , `SoftDisconnectsPerSecond` e `SoftConnectsPerSecond` estão desativados por padrão.</span><span class="sxs-lookup"><span data-stu-id="df201-145">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="df201-146">Adicione as seguintes informações ao arquivo de configuração do aplicativo para habilitá-las:</span><span class="sxs-lookup"><span data-stu-id="df201-146">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="df201-147">Recuperando valores do contador de desempenho</span><span class="sxs-lookup"><span data-stu-id="df201-147">Retrieving Performance Counter Values</span></span>  

 <span data-ttu-id="df201-148">O aplicativo de console a seguir mostra como recuperar valores de contador de desempenho em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df201-148">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="df201-149">As conexões devem estar abertas e ativas para que as informações sejam retornadas para todos os contadores de desempenho ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="df201-149">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df201-150">Este exemplo usa o banco de dados **AdventureWorks** de exemplo incluído com SQL Server.</span><span class="sxs-lookup"><span data-stu-id="df201-150">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="df201-151">As cadeias de conexão fornecidas no código de exemplo pressupõem que o banco de dados está instalado e disponível no computador local com um nome de instância de SQLExpress e que você criou SQL Server logons que correspondem àqueles fornecidos nas cadeias de conexão.</span><span class="sxs-lookup"><span data-stu-id="df201-151">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="df201-152">Talvez seja necessário habilitar os logons SQL Server se o servidor estiver configurado usando as configurações de segurança padrão que permitem apenas a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="df201-152">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="df201-153">Modifique as cadeias de conexão conforme necessário para se adequar ao seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="df201-153">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="df201-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df201-154">Example</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="df201-155">Confira também</span><span class="sxs-lookup"><span data-stu-id="df201-155">See also</span></span>

- [<span data-ttu-id="df201-156">Conectando a uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="df201-156">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="df201-157">OLE DB, ODBC e pool de conexões Oracle</span><span class="sxs-lookup"><span data-stu-id="df201-157">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="df201-158">[Contadores de Desempenho do ASP.NET](/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="df201-158">[Performance Counters for ASP.NET](/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="df201-159">Criação de perfil do runtime</span><span class="sxs-lookup"><span data-stu-id="df201-159">Runtime Profiling</span></span>](../../debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="df201-160">[Introdução ao monitoramento de limites de desempenho](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="df201-160">[Introduction to Monitoring Performance Thresholds](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- [<span data-ttu-id="df201-161">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="df201-161">ADO.NET Overview</span></span>](ado-net-overview.md)
