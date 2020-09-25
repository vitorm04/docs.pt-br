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
# <a name="sqlclient-support-for-localdb"></a>Suporte do SqlClient para LocalDB

Do SQL Server code name Denali em diante, uma versão leve do SQL Server, chamada LocalDB, estará disponível. Este tópico descreve como conectar-se a um banco de dados do LocalDB.  
  
## <a name="remarks"></a>Comentários  

 Para obter mais informações sobre o LocalDB, inclusive como instalá-lo e configurar sua instância do LocalDB, confira os Manuais Online do SQL Server.  
  
 Para resumir o que você pode fazer com o LocalDB:  
  
- Crie e inicie instâncias do LocalDB com sqllocaldb.exe ou seu arquivo app.config.  
  
- Use sqlcmd.exe para adicionar e modificar bancos de dados em uma instância do LocalDB. Por exemplo, `sqlcmd -S (localdb)\myinst`.  
  
- Use a palavra-chave da cadeia de conexão `AttachDBFilename` para adicionar um banco de dados à instância do LocalDB. Ao usar `AttachDBFilename`, se você não especificar o nome do banco de dados com a palavra-chave da cadeia de conexão `Database`, o banco de dados será removido da instância do LocalDB quando o aplicativo for fechado.  
  
- Especifique uma instância do LocalDB em sua cadeia de conexão. Por exemplo, o nome da instância é `myInstance`, a cadeia de conexão incluiria:  
  
    `server=(localdb)\\myInstance`  
  
 `User Instance=True` não é permitido ao se conectar a um banco de dados LocalDB.  
  
 Você pode baixar LocalDB do [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065). Se você usar sqlcmd.exe para modificar dados em sua instância LocalDB, precisará do sqlcmd do SQL Server 2012, que você também poderá obter do SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Criar programaticamente uma instância nomeada  

 Um aplicativo pode criar uma instância nomeada e especificar um banco de dados da seguinte maneira:  
  
- Especifique as instâncias LocalDB a serem criadas no arquivo app.config, da maneira a seguir.  O número de versão da instância deve ser igual ao número de versão da sua instalação do LocalDB.  
  
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
  
- Especifique o nome da instância que usa a palavra-chave da cadeia de conexão `server`.  O nome da instância especificado na palavra-chave da cadeia de conexão `server` deve corresponder ao nome especificado no arquivo app.config.  
  
- Use a palavra-chave da cadeia de conexão `AttachDBFilename` para especificar o arquivo .MDF.  
  
## <a name="see-also"></a>Veja também

- [Recursos de SQL Server e ADO.NET](sql-server-features-and-adonet.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
