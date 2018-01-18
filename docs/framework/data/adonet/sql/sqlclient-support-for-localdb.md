---
title: Suporte do SqlClient para LocalDB
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3d643ac386aebf51673f937b3f47e73c749b78f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="2f165-102">Suporte do SqlClient para LocalDB</span><span class="sxs-lookup"><span data-stu-id="2f165-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="2f165-103">A partir do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Codinome Denali, uma versão leve do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], denominada LocalDB, estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2f165-103">Beginning in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] code name Denali, a lightweight version of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], called LocalDB, will be available.</span></span> <span data-ttu-id="2f165-104">Este tópico discute como se conectar a um banco de dados LocalDB.</span><span class="sxs-lookup"><span data-stu-id="2f165-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f165-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f165-105">Remarks</span></span>  
 <span data-ttu-id="2f165-106">Para obter mais informações sobre o LocalDB, inclusive como instalá-lo e configurar sua instância LocalDB, consulte [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Manuais Online.</span><span class="sxs-lookup"><span data-stu-id="2f165-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="2f165-107">Para resumir o que você pode fazer com LocalDB:</span><span class="sxs-lookup"><span data-stu-id="2f165-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="2f165-108">Criar e iniciar as instâncias de LocalDB com sqllocaldb.exe ou seu arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="2f165-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="2f165-109">Use sqlcmd.exe para adicionar e modificar bancos de dados em uma instância de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="2f165-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="2f165-110">Por exemplo, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="2f165-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="2f165-111">Use o `AttachDBFilename` palavra-chave de cadeia de caracteres de conexão para adicionar um banco de dados para sua instância LocalDB.</span><span class="sxs-lookup"><span data-stu-id="2f165-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="2f165-112">Ao usar `AttachDBFilename`, se você não especificar o nome do banco de dados com o `Database` palavra-chave cadeia de caracteres de conexão, o banco de dados será removido da instância do LocalDB quando o aplicativo for fechado.</span><span class="sxs-lookup"><span data-stu-id="2f165-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="2f165-113">Especifique uma instância de LocalDB em sua cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="2f165-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="2f165-114">Por exemplo, o nome da instância é `myInstance`, inclui a cadeia de caracteres de conexão:</span><span class="sxs-lookup"><span data-stu-id="2f165-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="2f165-115">`User Instance=True`não é permitida durante a conexão com um banco de dados LocalDB.</span><span class="sxs-lookup"><span data-stu-id="2f165-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="2f165-116">Você pode baixar o LocalDB do [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="2f165-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="2f165-117">Se você usar sqlcmd.exe para modificar dados em sua instância de LocalDB, será necessário sqlcmd de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012, que você também pode ser obtido o [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="2f165-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012, which you can also get from the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="2f165-118">Criar programaticamente uma instância nomeada</span><span class="sxs-lookup"><span data-stu-id="2f165-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="2f165-119">Um aplicativo pode criar uma instância nomeada e especificar um banco de dados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2f165-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="2f165-120">Especifique as instâncias de LocalDB para criar o arquivo App. config, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="2f165-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="2f165-121">O número de versão da instância deve ser igual ao número de versão da instalação do LocalDB.</span><span class="sxs-lookup"><span data-stu-id="2f165-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="2f165-122">Especifique o nome da instância usando o `server` palavra-chave de cadeia de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="2f165-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="2f165-123">O nome de instância especificado o `server` palavra-chave de cadeia de caracteres de conexão deve corresponder ao nome especificado no arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="2f165-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="2f165-124">Use o `AttachDBFilename` palavra-chave de cadeia de caracteres de conexão para especificar o. Arquivo MDF.</span><span class="sxs-lookup"><span data-stu-id="2f165-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f165-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f165-125">See Also</span></span>  
 <span data-ttu-id="2f165-126">[SQL Server Features and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md) (Recursos do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2f165-126">[SQL Server Features and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)</span></span>  
 <span data-ttu-id="2f165-127">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2f165-127">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
