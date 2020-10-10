---
title: Conectar .NET para Apache Spark a SQL Server
description: Saiba como se conectar a uma instância de SQL Server de seu aplicativo .NET para Apache Spark.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 773e743a67c066438cb86d983ebfa34f73692c2d
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877825"
---
# <a name="connect-net-for-apache-spark-to-sql-server"></a><span data-ttu-id="f80b0-103">Conectar .NET para Apache Spark a SQL Server</span><span class="sxs-lookup"><span data-stu-id="f80b0-103">Connect .NET for Apache Spark to SQL Server</span></span>

<span data-ttu-id="f80b0-104">Neste artigo, você aprenderá a se conectar a uma instância do SQL Server de seu aplicativo [.net para Apache Spark](https://github.com/dotnet/spark) .</span><span class="sxs-lookup"><span data-stu-id="f80b0-104">In this article, you learn how to connect to an SQL server instance from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

## <a name="configure-sql-server-to-grant-your-application-access"></a><span data-ttu-id="f80b0-105">Configurar SQL Server para conceder acesso ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="f80b0-105">Configure SQL Server to grant your application access</span></span>

1. <span data-ttu-id="f80b0-106">Adicione um usuário e senha de logon escolhendo SQL Server autenticação para sua instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f80b0-106">Add a login user and password choosing SQL Server authentication to your SQL Server instance.</span></span>
2. <span data-ttu-id="f80b0-107">Conceda permissões necessárias ao usuário de logon no nível de banco de dados relevante, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f80b0-107">Give that login user necessary permissions at the relevant database level as shown below:</span></span>

    ![Permissões do SQL Server](./media/connect-external-sources/SqlServerAuth.png)

3. <span data-ttu-id="f80b0-109">Verifique se a porta padrão para SQL Server `1433` é permitida por meio do firewall.</span><span class="sxs-lookup"><span data-stu-id="f80b0-109">Make sure the default port for SQL Server `1433` is allowed through the firewall.</span></span>
4. <span data-ttu-id="f80b0-110">Abra o SQL configure Manager para habilitar o TCP/IP por meio da configuração de rede, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f80b0-110">Open SQL configure manager to enable TCP/IP through the network configuration as shown below:</span></span>

    ![Habilitar SQL Server TCP/IP](./media/connect-external-sources/SqlServerTCPIP.png)

    <span data-ttu-id="f80b0-112">Observe também o valor de **escutar tudo** na guia acima, em **protocolo**.</span><span class="sxs-lookup"><span data-stu-id="f80b0-112">Also note the value of **Listen All** in above tab under **Protocol**.</span></span>

5. <span data-ttu-id="f80b0-113">Configure a porta TCP/IP para 1433 para todos os endereços IP necessários se o `Listen All` for definido como `No` .</span><span class="sxs-lookup"><span data-stu-id="f80b0-113">Configure the TCP/IP port to 1433 for all required IP addresses if the `Listen All` is set to `No`.</span></span> <span data-ttu-id="f80b0-114">Caso contrário, defina a porta TCP em IPAll.</span><span class="sxs-lookup"><span data-stu-id="f80b0-114">Otherwise, set the TCP Port in IPAll.</span></span>

    ![SQL Server porta TCP/IP](./media/connect-external-sources/SQLServerTCPIIPPort.png)

## <a name="connect-to-sql-server-from-your-application"></a><span data-ttu-id="f80b0-116">Conectar-se a SQL Server do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f80b0-116">Connect to SQL Server from your application</span></span>

1. <span data-ttu-id="f80b0-117">Use o Microsoft JDBC Driver para SQL Server para fornecer conectividade de banco de dados por meio de seu aplicativo (Baixe deste [site oficial](https://docs.microsoft.com/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)).</span><span class="sxs-lookup"><span data-stu-id="f80b0-117">Use the Microsoft JDBC Driver for SQL Server to provide database connectivity through your application (download from [this official website](https://docs.microsoft.com/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)).</span></span>
2. <span data-ttu-id="f80b0-118">Defina as seguintes configurações para se conectar à instância do SQL Server e ao banco de dados do seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="f80b0-118">Set the following configurations to connect to the SQL server instance and database from your application:</span></span>
    1. <span data-ttu-id="f80b0-119">**connection_url**: essa é a URL usada para se conectar à instância/banco de dados do SQL Server e tem o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="f80b0-119">**connection_url**: This is the URL used to connect to the SQL server instance/database and has the following format:</span></span>

        ```
        jdbc:sqlserver://<SQL_server_IP_address>:1433;instanceName=<instance_name>;databaseName=<database_name>;
        ```

    2. <span data-ttu-id="f80b0-120">**DBTABLE**: nome da tabela que está sendo acessada.</span><span class="sxs-lookup"><span data-stu-id="f80b0-120">**dbtable**: Name of table being accessed.</span></span>
    3. <span data-ttu-id="f80b0-121">**usuário**: logon de usuário configurado na etapa 1 de configuração do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f80b0-121">**user**: Login user set up in Step 1 of configuring the SQL server.</span></span>
    4. <span data-ttu-id="f80b0-122">**senha**: senha do usuário configurada na etapa 1 de configuração do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f80b0-122">**password**: Password of user set up in Step 1 of configuring the SQL server.</span></span>
3. <span data-ttu-id="f80b0-123">Use a configuração acima no código do aplicativo para ler os dados de uma tabela, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f80b0-123">Use the above configuration in your application code to read the data from a table as shown below:</span></span>

    ```csharp
    static void Main()
    {
        SparkSession spark = SparkSession
            .Builder()
            .AppName("Connect to SQL Server")
            .GetOrCreate();

        string connection_url = "<URL to connect to SQL server instance>";
        string dbtable = "<database table to access>";
        string user = "<Login user name>";
        string password = "<Login user password>";

        DataFrame jdbcDF = spark.Read()
            .Format("jdbc")
            .Option("driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver")
            .Option("url", connection_url)
            .Option("dbtable", dbtable)
            .Option("user", user)
            .Option("password", password).Load();
        jdbcDF.Show(); // Displays the content of the SQL table as a DataFrame
    }
    ```
