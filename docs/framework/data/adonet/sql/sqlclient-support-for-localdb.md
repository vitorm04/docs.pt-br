---
title: Suporte do SqlClient para LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 33368ca4b2dc5397087d29e515db6c1094e350bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="sqlclient-support-for-localdb"></a>Suporte do SqlClient para LocalDB
A partir do SQL Server Codinome Denali, uma versão leve do SQL Server, denominada LocalDB, estarão disponível. Este tópico discute como se conectar a um banco de dados LocalDB.  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre o LocalDB, inclusive como instalá-lo e configurar sua instância do LocalDB, consulte os Manuais Online do SQL Server.  
  
 Para resumir o que você pode fazer com LocalDB:  
  
-   Criar e iniciar as instâncias de LocalDB com sqllocaldb.exe ou seu arquivo App. config.  
  
-   Use sqlcmd.exe para adicionar e modificar bancos de dados em uma instância de LocalDB. Por exemplo, `sqlcmd -S (localdb)\myinst`.  
  
-   Use o `AttachDBFilename` palavra-chave de cadeia de caracteres de conexão para adicionar um banco de dados para sua instância LocalDB. Ao usar `AttachDBFilename`, se você não especificar o nome do banco de dados com o `Database` palavra-chave cadeia de caracteres de conexão, o banco de dados será removido da instância do LocalDB quando o aplicativo for fechado.  
  
-   Especifique uma instância de LocalDB em sua cadeia de conexão. Por exemplo, o nome da instância é `myInstance`, inclui a cadeia de caracteres de conexão:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True` não é permitida durante a conexão com um banco de dados LocalDB.  
  
 Você pode baixar o LocalDB do [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065). Se você usar sqlcmd.exe para modificar dados em sua instância de LocalDB, será necessário sqlcmd do SQL Server 2012, você também pode obter do SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Criar programaticamente uma instância nomeada  
 Um aplicativo pode criar uma instância nomeada e especificar um banco de dados da seguinte maneira:  
  
-   Especifique as instâncias de LocalDB para criar o arquivo App. config, da seguinte maneira.  O número de versão da instância deve ser igual ao número de versão da instalação do LocalDB.  
  
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
  
-   Especifique o nome da instância usando o `server` palavra-chave de cadeia de caracteres de conexão.  O nome de instância especificado o `server` palavra-chave de cadeia de caracteres de conexão deve corresponder ao nome especificado no arquivo App. config.  
  
-   Use o `AttachDBFilename` palavra-chave de cadeia de caracteres de conexão para especificar o. Arquivo MDF.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Features and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md) (Recursos do SQL Server e o ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
