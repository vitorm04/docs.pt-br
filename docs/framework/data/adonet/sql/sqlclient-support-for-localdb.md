---
title: Suporte do SqlClient para LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: d02524cd5901adeca7bc36d6fd13c7abdc46c69b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894406"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="90cf8-102">Suporte do SqlClient para LocalDB</span><span class="sxs-lookup"><span data-stu-id="90cf8-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="90cf8-103">A partir do SQL Server nome do código Denali, uma versão leve do SQL Server, chamada LocalDB, estará disponível.</span><span class="sxs-lookup"><span data-stu-id="90cf8-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="90cf8-104">Este tópico discute como se conectar a um banco de dados LocalDB.</span><span class="sxs-lookup"><span data-stu-id="90cf8-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90cf8-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="90cf8-105">Remarks</span></span>  
 <span data-ttu-id="90cf8-106">Para obter mais informações sobre o LocalDB, incluindo como instalar o LocalDB e configurar sua instância do LocalDB, consulte Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90cf8-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="90cf8-107">Para resumir o que você pode fazer com o LocalDB:</span><span class="sxs-lookup"><span data-stu-id="90cf8-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="90cf8-108">Crie e inicie instâncias do LocalDB com sqllocaldb. exe ou seu arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="90cf8-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="90cf8-109">Use sqlcmd. exe para adicionar e modificar bancos de dados em uma instância de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="90cf8-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="90cf8-110">Por exemplo: `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="90cf8-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="90cf8-111">Use a `AttachDBFilename` palavra-chave da cadeia de conexão para adicionar um banco de dados à instância do LocalDB.</span><span class="sxs-lookup"><span data-stu-id="90cf8-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="90cf8-112">Ao usar `AttachDBFilename`, se você não especificar o nome do banco de dados com a `Database` palavra-chave da cadeia de conexão, o banco de dados será removido da instância de LocalDB quando o aplicativo for fechado.</span><span class="sxs-lookup"><span data-stu-id="90cf8-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="90cf8-113">Especifique uma instância de LocalDB na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="90cf8-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="90cf8-114">Por exemplo, o nome da instância `myInstance`é, a cadeia de conexão inclui:</span><span class="sxs-lookup"><span data-stu-id="90cf8-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="90cf8-115">`User Instance=True`Não é permitido ao se conectar a um banco de dados LocalDB.</span><span class="sxs-lookup"><span data-stu-id="90cf8-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="90cf8-116">Você pode baixar o LocalDB de [Microsoft SQL Server o Feature Pack 2012](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="90cf8-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="90cf8-117">Se você for usar o sqlcmd. exe para modificar dados em sua instância de LocalDB, precisará do sqlcmd do SQL Server 2012, que também pode ser obtido do SQL Server Feature Pack 2012.</span><span class="sxs-lookup"><span data-stu-id="90cf8-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="90cf8-118">Criar programaticamente uma instância nomeada</span><span class="sxs-lookup"><span data-stu-id="90cf8-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="90cf8-119">Um aplicativo pode criar uma instância nomeada e especificar um banco de dados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="90cf8-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="90cf8-120">Especifique as instâncias de LocalDB a serem criadas no arquivo app. config, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="90cf8-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="90cf8-121">O número de versão da instância deve ser igual ao número de versão da sua instalação do LocalDB.</span><span class="sxs-lookup"><span data-stu-id="90cf8-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="90cf8-122">Especifique o nome da instância usando a palavra `server` -chave da cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="90cf8-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="90cf8-123">O nome da instância especificado na `server` palavra-chave da cadeia de conexão deve corresponder ao nome especificado no arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="90cf8-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="90cf8-124">Use a `AttachDBFilename` palavra-chave da cadeia de conexão para especificar o. Arquivo MDF.</span><span class="sxs-lookup"><span data-stu-id="90cf8-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90cf8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90cf8-125">See also</span></span>

- <span data-ttu-id="90cf8-126">[SQL Server Features and ADO.NET](sql-server-features-and-adonet.md) (Recursos do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="90cf8-126">[SQL Server Features and ADO.NET](sql-server-features-and-adonet.md)</span></span>
- <span data-ttu-id="90cf8-127">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="90cf8-127">[ADO.NET Overview](../ado-net-overview.md)</span></span>
