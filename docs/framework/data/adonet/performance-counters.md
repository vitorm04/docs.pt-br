---
title: Contadores de desempenho no ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9843d5c5edfc5ea590e4e6d0e5474a7d817e0ba6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="35f24-102">Contadores de desempenho no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="35f24-102">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="35f24-103">O ADO.NET 2.0 introduziu suporte expandido para contadores de desempenho que inclui suporte para ambos <xref:System.Data.SqlClient> e <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="35f24-103">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="35f24-104">O <xref:System.Data.SqlClient> contadores de desempenho disponíveis em versões anteriores do ADO.NET foram preteridos e substituídos por novos contadores de desempenho discutidos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="35f24-104">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="35f24-105">Você pode usar o ADO.NET contadores de desempenho para monitorar o status de seu aplicativo e os recursos de conexão que ele usa.</span><span class="sxs-lookup"><span data-stu-id="35f24-105">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="35f24-106">Contadores de desempenho podem ser monitorados usando o Monitor de desempenho do Windows ou podem ser acessados programaticamente usando o <xref:System.Diagnostics.PerformanceCounter> classe no <xref:System.Diagnostics> namespace.</span><span class="sxs-lookup"><span data-stu-id="35f24-106">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="35f24-107">Contadores de desempenho disponíveis</span><span class="sxs-lookup"><span data-stu-id="35f24-107">Available Performance Counters</span></span>  
 <span data-ttu-id="35f24-108">Atualmente, há 14 diferentes contadores de desempenho disponíveis para <xref:System.Data.SqlClient> e <xref:System.Data.OracleClient> conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="35f24-108">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="35f24-109">Observe que os nomes dos contadores individuais não são localizados nas versões regionais do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="35f24-109">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="35f24-110">Contador de desempenho</span><span class="sxs-lookup"><span data-stu-id="35f24-110">Performance counter</span></span>|<span data-ttu-id="35f24-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="35f24-111">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="35f24-112">O número de conexões por segundo que estão sendo feitas em um servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="35f24-112">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="35f24-113">O número de desconexões por segundo que estão sendo feitas em um servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="35f24-113">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="35f24-114">O número de grupos de pool de conexão exclusiva que estão ativos.</span><span class="sxs-lookup"><span data-stu-id="35f24-114">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="35f24-115">Esse contador é controlado pelo número de cadeias de caracteres de conexão exclusivas que são encontradas no AppDomain.</span><span class="sxs-lookup"><span data-stu-id="35f24-115">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="35f24-116">O número total de pools de conexão.</span><span class="sxs-lookup"><span data-stu-id="35f24-116">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="35f24-117">O número de conexões ativas que estão atualmente em uso.</span><span class="sxs-lookup"><span data-stu-id="35f24-117">The number of active connections that are currently in use.</span></span> <span data-ttu-id="35f24-118">**Observação:** esse contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="35f24-118">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="35f24-119">Para habilitar esse contador de desempenho, consulte [ativando desativado por padrão contadores](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="35f24-119">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="35f24-120">O número de conexões disponíveis para uso nos pools de conexão.</span><span class="sxs-lookup"><span data-stu-id="35f24-120">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="35f24-121">**Observação:** esse contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="35f24-121">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="35f24-122">Para habilitar esse contador de desempenho, consulte [ativando desativado por padrão contadores](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="35f24-122">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="35f24-123">O número de grupos de pools de conexão exclusivas que são marcadas para remoção.</span><span class="sxs-lookup"><span data-stu-id="35f24-123">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="35f24-124">Esse contador é controlado pelo número de cadeias de caracteres de conexão exclusivas que são encontradas no AppDomain.</span><span class="sxs-lookup"><span data-stu-id="35f24-124">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="35f24-125">O número de pools de conexão inativos que não tenham qualquer atividade recente e estão aguardando para ser descartado.</span><span class="sxs-lookup"><span data-stu-id="35f24-125">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="35f24-126">O número de conexões ativas que não são agrupados.</span><span class="sxs-lookup"><span data-stu-id="35f24-126">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="35f24-127">O número de conexões ativas que estão sendo gerenciadas pela infraestrutura do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="35f24-127">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="35f24-128">O número de conexões que foram recuperados por meio de coleta de lixo onde `Close` ou `Dispose` não foi chamado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="35f24-128">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="35f24-129">Não foi explicitamente fechar ou descartar conexões reduz o desempenho.</span><span class="sxs-lookup"><span data-stu-id="35f24-129">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="35f24-130">O número de conexões no momento aguardando a conclusão de uma ação e que, portanto, não está disponível para uso pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="35f24-130">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="35f24-131">O número de conexões ativas que está sendo recebida do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="35f24-131">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="35f24-132">**Observação:** esse contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="35f24-132">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="35f24-133">Para habilitar esse contador de desempenho, consulte [ativando desativado por padrão contadores](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="35f24-133">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="35f24-134">O número de conexões ativas que estão sendo retornados ao pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="35f24-134">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="35f24-135">**Observação:** esse contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="35f24-135">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="35f24-136">Para habilitar esse contador de desempenho, consulte [ativando desativado por padrão contadores](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="35f24-136">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="35f24-137">Grupos de Pool de Conexão e Pools de Conexão</span><span class="sxs-lookup"><span data-stu-id="35f24-137">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="35f24-138">Ao usar a autenticação do Windows (segurança integrada), você deve monitorar tanto o `NumberOfActiveConnectionPoolGroups` e `NumberOfActiveConnectionPools` contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="35f24-138">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="35f24-139">O motivo é que mapa de grupos de pool de conexão em cadeias de caracteres de conexão exclusivo.</span><span class="sxs-lookup"><span data-stu-id="35f24-139">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="35f24-140">Quando a segurança integrada é usada, os pools de conexão mapeiam para cadeias de caracteres de conexão e Além disso, criar pools de separado para identidades individuais do Windows.</span><span class="sxs-lookup"><span data-stu-id="35f24-140">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="35f24-141">Por exemplo, se Fred e Julie, cada dentro do mesmo AppDomain, usar a cadeia de caracteres de conexão `"Data Source=MySqlServer;Integrated Security=true"`, será criado um grupo de pool de conexão para a cadeia de caracteres de conexão e dois grupos adicionais são criados, um para Fred e outro para Julie.</span><span class="sxs-lookup"><span data-stu-id="35f24-141">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="35f24-142">Se João e Marta usam uma cadeia de caracteres de conexão com um logon do SQL Server idêntico, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, em seguida, somente um único pool é criado para o **lowPrivUser** identidade.</span><span class="sxs-lookup"><span data-stu-id="35f24-142">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="35f24-143">Ativar contadores desativado por padrão</span><span class="sxs-lookup"><span data-stu-id="35f24-143">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="35f24-144">Os contadores de desempenho `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, e `SoftConnectsPerSecond` são desativados por padrão.</span><span class="sxs-lookup"><span data-stu-id="35f24-144">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="35f24-145">Adicione as seguintes informações ao arquivo de configuração do aplicativo para habilitá-los:</span><span class="sxs-lookup"><span data-stu-id="35f24-145">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="35f24-146">Recuperando valores de contador de desempenho</span><span class="sxs-lookup"><span data-stu-id="35f24-146">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="35f24-147">O aplicativo de console a seguir mostra como recuperar valores de contador de desempenho em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="35f24-147">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="35f24-148">Conexões devem ser aberto e ativo para obter informações a serem retornadas para todos os contadores de desempenho do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="35f24-148">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35f24-149">Este exemplo usa o exemplo **AdventureWorks** banco de dados incluído com [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35f24-149">This example uses the sample **AdventureWorks** database included with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="35f24-150">As cadeias de caracteres de conexão fornecidas no código de exemplo pressupõem que o banco de dados está instalado e disponível no computador local com um nome de instância de SqlExpress, e que você criou os logons do SQL Server que correspondam aos fornecidos nas cadeias de conexão.</span><span class="sxs-lookup"><span data-stu-id="35f24-150">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="35f24-151">Talvez seja necessário habilitar os logons do SQL Server se o servidor é configurado usando as configurações de segurança padrão que permite que somente a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="35f24-151">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="35f24-152">Modificar as cadeias de caracteres de conexão conforme necessário para adequar ao seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="35f24-152">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="35f24-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35f24-153">Example</span></span>  
  
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
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
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
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
        //  "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="35f24-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35f24-154">See Also</span></span>  
 [<span data-ttu-id="35f24-155">Conectando a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="35f24-155">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="35f24-156">Conexão do Oracle, ODBC e OLE DB Pooling</span><span class="sxs-lookup"><span data-stu-id="35f24-156">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="35f24-157">Contadores de desempenho para ASP.NET</span><span class="sxs-lookup"><span data-stu-id="35f24-157">Performance Counters for ASP.NET</span></span>](http://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)  
 [<span data-ttu-id="35f24-158">Criação de perfil do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="35f24-158">Runtime Profiling</span></span>](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)  
 [<span data-ttu-id="35f24-159">Introdução ao monitoramento de limites de desempenho</span><span class="sxs-lookup"><span data-stu-id="35f24-159">Introduction to Monitoring Performance Thresholds</span></span>](http://msdn.microsoft.com/library/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)  
 <span data-ttu-id="35f24-160">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="35f24-160">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
