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
# <a name="sqlclient-support-for-localdb"></a>Suporte do SqlClient para LocalDB
A partir do SQL Server nome do código Denali, uma versão leve do SQL Server, chamada LocalDB, estará disponível. Este tópico discute como se conectar a um banco de dados LocalDB.  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre o LocalDB, incluindo como instalar o LocalDB e configurar sua instância do LocalDB, consulte Manuais Online do SQL Server.  
  
 Para resumir o que você pode fazer com o LocalDB:  
  
- Crie e inicie instâncias do LocalDB com sqllocaldb. exe ou seu arquivo app. config.  
  
- Use sqlcmd. exe para adicionar e modificar bancos de dados em uma instância de LocalDB. Por exemplo: `sqlcmd -S (localdb)\myinst`.  
  
- Use a `AttachDBFilename` palavra-chave da cadeia de conexão para adicionar um banco de dados à instância do LocalDB. Ao usar `AttachDBFilename`, se você não especificar o nome do banco de dados com a `Database` palavra-chave da cadeia de conexão, o banco de dados será removido da instância de LocalDB quando o aplicativo for fechado.  
  
- Especifique uma instância de LocalDB na cadeia de conexão. Por exemplo, o nome da instância `myInstance`é, a cadeia de conexão inclui:  
  
    `server=(localdb)\\myInstance`  
  
 `User Instance=True`Não é permitido ao se conectar a um banco de dados LocalDB.  
  
 Você pode baixar o LocalDB de [Microsoft SQL Server o Feature Pack 2012](https://www.microsoft.com/download/en/details.aspx?id=29065). Se você for usar o sqlcmd. exe para modificar dados em sua instância de LocalDB, precisará do sqlcmd do SQL Server 2012, que também pode ser obtido do SQL Server Feature Pack 2012.  
  
## <a name="programmatically-create-a-named-instance"></a>Criar programaticamente uma instância nomeada  
 Um aplicativo pode criar uma instância nomeada e especificar um banco de dados da seguinte maneira:  
  
- Especifique as instâncias de LocalDB a serem criadas no arquivo app. config, da seguinte maneira.  O número de versão da instância deve ser igual ao número de versão da sua instalação do LocalDB.  
  
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
  
- Especifique o nome da instância usando a palavra `server` -chave da cadeia de conexão.  O nome da instância especificado na `server` palavra-chave da cadeia de conexão deve corresponder ao nome especificado no arquivo app. config.  
  
- Use a `AttachDBFilename` palavra-chave da cadeia de conexão para especificar o. Arquivo MDF.  
  
## <a name="see-also"></a>Consulte também

- [SQL Server Features and ADO.NET](sql-server-features-and-adonet.md) (Recursos do SQL Server e o ADO.NET)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
