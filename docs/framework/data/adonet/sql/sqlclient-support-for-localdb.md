---
title: Suporte do SqlClient para LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 841c455605b0b32668d26cab16a6207dc1c0f716
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203417"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="84aef-102">Suporte do SqlClient para LocalDB</span><span class="sxs-lookup"><span data-stu-id="84aef-102">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="84aef-103">Do SQL Server code name Denali em diante, uma versão leve do SQL Server, chamada LocalDB, estará disponível.</span><span class="sxs-lookup"><span data-stu-id="84aef-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="84aef-104">Este tópico descreve como conectar-se a um banco de dados do LocalDB.</span><span class="sxs-lookup"><span data-stu-id="84aef-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84aef-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="84aef-105">Remarks</span></span>  

 <span data-ttu-id="84aef-106">Para obter mais informações sobre o LocalDB, inclusive como instalá-lo e configurar sua instância do LocalDB, confira os Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="84aef-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="84aef-107">Para resumir o que você pode fazer com o LocalDB:</span><span class="sxs-lookup"><span data-stu-id="84aef-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="84aef-108">Crie e inicie instâncias do LocalDB com sqllocaldb.exe ou seu arquivo app.config.</span><span class="sxs-lookup"><span data-stu-id="84aef-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="84aef-109">Use sqlcmd.exe para adicionar e modificar bancos de dados em uma instância do LocalDB.</span><span class="sxs-lookup"><span data-stu-id="84aef-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="84aef-110">Por exemplo, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="84aef-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="84aef-111">Use a palavra-chave da cadeia de conexão `AttachDBFilename` para adicionar um banco de dados à instância do LocalDB.</span><span class="sxs-lookup"><span data-stu-id="84aef-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="84aef-112">Ao usar `AttachDBFilename`, se você não especificar o nome do banco de dados com a palavra-chave da cadeia de conexão `Database`, o banco de dados será removido da instância do LocalDB quando o aplicativo for fechado.</span><span class="sxs-lookup"><span data-stu-id="84aef-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="84aef-113">Especifique uma instância do LocalDB em sua cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="84aef-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="84aef-114">Por exemplo, o nome da instância é `myInstance`, a cadeia de conexão incluiria:</span><span class="sxs-lookup"><span data-stu-id="84aef-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="84aef-115">`User Instance=True` não é permitido ao se conectar a um banco de dados LocalDB.</span><span class="sxs-lookup"><span data-stu-id="84aef-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="84aef-116">Você pode baixar LocalDB do [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="84aef-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="84aef-117">Se você usar sqlcmd.exe para modificar dados em sua instância LocalDB, precisará do sqlcmd do SQL Server 2012, que você também poderá obter do SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="84aef-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="84aef-118">Criar programaticamente uma instância nomeada</span><span class="sxs-lookup"><span data-stu-id="84aef-118">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="84aef-119">Um aplicativo pode criar uma instância nomeada e especificar um banco de dados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="84aef-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="84aef-120">Especifique as instâncias LocalDB a serem criadas no arquivo app.config, da maneira a seguir.</span><span class="sxs-lookup"><span data-stu-id="84aef-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="84aef-121">O número de versão da instância deve ser igual ao número de versão da sua instalação do LocalDB.</span><span class="sxs-lookup"><span data-stu-id="84aef-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="84aef-122">Especifique o nome da instância que usa a palavra-chave da cadeia de conexão `server`.</span><span class="sxs-lookup"><span data-stu-id="84aef-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="84aef-123">O nome da instância especificado na palavra-chave da cadeia de conexão `server` deve corresponder ao nome especificado no arquivo app.config.</span><span class="sxs-lookup"><span data-stu-id="84aef-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="84aef-124">Use a palavra-chave da cadeia de conexão `AttachDBFilename` para especificar o arquivo .MDF.</span><span class="sxs-lookup"><span data-stu-id="84aef-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84aef-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="84aef-125">See also</span></span>

- [<span data-ttu-id="84aef-126">Recursos de SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="84aef-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="84aef-127">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="84aef-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
