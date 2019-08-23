---
title: SqlDependency em um aplicativo ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: a93cb9da44985fa29a4975875564b384117ce76f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938464"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency em um aplicativo ASP.NET
O exemplo nesta seção mostra como usar <xref:System.Data.SqlClient.SqlDependency> indiretamente, aproveitando o objeto ASP.net. <xref:System.Web.Caching.SqlCacheDependency> O <xref:System.Web.Caching.SqlCacheDependency> objeto usa um <xref:System.Data.SqlClient.SqlDependency> para escutar notificações e atualizar corretamente o cache.  
  
> [!NOTE]
> O código de exemplo pressupõe que você habilitou notificações de consulta executando os scripts em [habilitando notificações de consulta](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>Sobre o aplicativo de exemplo  
 O aplicativo de exemplo usa uma única página da Web ASP.net para exibir informações de produto do banco de dados <xref:System.Web.UI.WebControls.GridView> AdventureWorks SQL Server em um controle. Quando a página é carregada, o código grava a hora atual em <xref:System.Web.UI.WebControls.Label> um controle. Em seguida, ele <xref:System.Web.Caching.SqlCacheDependency> define um objeto e define as <xref:System.Web.Caching.Cache> Propriedades no objeto para armazenar os dados de cache por até três minutos. O código, em seguida, se conecta ao banco de dados e os recupera. Quando a página for carregada e o aplicativo estiver em execução, o ASP.NET recuperará os dados do cache, que você pode verificar observando se a hora na página não é alterada. Se os dados que estão sendo monitorados forem alterados, o ASP.net invalida o cache e `GridView` preenche novamente o controle com dados atualizados, atualizando o `Label` tempo exibido no controle.  
  
## <a name="creating-the-sample-application"></a>Criando o aplicativo de exemplo  
 Siga estas etapas para criar e executar o aplicativo de exemplo:  
  
1. Crie um novo site do ASP.NET.  
  
2. Adicione um <xref:System.Web.UI.WebControls.Label> e um <xref:System.Web.UI.WebControls.GridView> controle à página default. aspx.  
  
3. Abra o módulo de classe da página e adicione as seguintes diretivas:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. Adicione o seguinte código ao evento da `Page_Load` página:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. Adicione dois métodos `GetConnectionString` auxiliares e `GetSQL`. A cadeia de conexão definida usa segurança integrada. Você precisará verificar se a conta que você está usando tem as permissões de banco de dados necessárias e se o banco de dados de exemplo **AdventureWorks**tem notificações habilitadas.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Testando o aplicativo  
 O aplicativo armazena em cache os dados exibidos no formulário da Web e os atualiza a cada três minutos, se não houver atividade. Se ocorrer uma alteração no banco de dados, o cache será atualizado imediatamente. Execute o aplicativo no Visual Studio, que carrega a página no navegador. O tempo de atualização do cache exibido indica quando o cache foi atualizado pela última vez. Aguarde três minutos e, em seguida, atualize a página, fazendo com que ocorra um evento de postback. Observe que a hora exibida na página foi alterada. Se você atualizar a página em menos de três minutos, a hora exibida na página permanecerá a mesma.  
  
 Agora, atualize os dados no banco de dado, usando um comando de atualização Transact-SQL e atualize a página. O tempo exibido agora indica que o cache foi atualizado com os novos dados do banco de dado. Observe que, embora o cache seja atualizado, a hora exibida na página não é alterada até que ocorra um evento de postback.  
  
## <a name="see-also"></a>Consulte também

- [Notificações de consulta no SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
