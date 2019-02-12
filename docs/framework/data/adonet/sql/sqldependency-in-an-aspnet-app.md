---
title: SqlDependency em um aplicativo ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 42eb0a417659776b2cd2fffa9d2fd62e58a4a176
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091975"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency em um aplicativo ASP.NET
O exemplo nesta seção mostra como usar <xref:System.Data.SqlClient.SqlDependency> indiretamente, aproveitando o ASP.NET <xref:System.Web.Caching.SqlCacheDependency> objeto. O <xref:System.Web.Caching.SqlCacheDependency> objeto usa um <xref:System.Data.SqlClient.SqlDependency> para ouvir as notificações e atualizar corretamente o cache.  
  
> [!NOTE]
>  O exemplo de código pressupõe que você habilitou as notificações de consulta, executando os scripts [habilitando notificações de consulta](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>Sobre o aplicativo de exemplo  
 O aplicativo de exemplo usa uma única página da Web do ASP.NET para exibir informações de produto a **AdventureWorks** banco de dados do SQL Server em um <xref:System.Web.UI.WebControls.GridView> controle. Quando a página for carregada, o código grava a hora atual para um <xref:System.Web.UI.WebControls.Label> controle. Em seguida, ele define uma <xref:System.Web.Caching.SqlCacheDependency> do objeto e define as propriedades no <xref:System.Web.Caching.Cache> objeto para armazenar os dados do cache de até três minutos. O código, em seguida, conecta-se ao banco de dados e recupera os dados. Quando a página é carregada e o aplicativo está executando o ASP.NET irá recuperar os dados do cache, você pode confirmar ao observar que o tempo na página não é alterado. Se os dados que estão sendo monitorados forem alterados, ASP.NET invalida o cache e preencher novamente o `GridView` controle com dados atualizados, atualizando o horário exibido no `Label` controle.  
  
## <a name="creating-the-sample-application"></a>Criando o aplicativo de exemplo  
 Siga estas etapas para criar e executar o aplicativo de exemplo:  
  
1.  Crie um novo site da Web do ASP.NET.  
  
2.  Adicionar um <xref:System.Web.UI.WebControls.Label> e um <xref:System.Web.UI.WebControls.GridView> controle para a página Default. aspx.  
  
3.  Abra o módulo de classe da página e adicione as seguintes diretivas:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  Adicione o seguinte código na página de `Page_Load` eventos:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  Adicione dois métodos auxiliares, `GetConnectionString` e `GetSQL`. A cadeia de conexão definida usa a segurança integrada. Você precisará verificar se a conta que você está usando tem as permissões de banco de dados necessários e que o banco de dados de exemplo, **AdventureWorks**, tem notificações habilitadas.
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Testando o aplicativo  
 O aplicativo armazena em cache os dados exibidos no formulário da Web e atualiza a cada três minutos se não houver nenhuma atividade. Se ocorrer uma alteração no banco de dados, o cache é atualizado imediatamente. Execute o aplicativo do Visual Studio, que carrega a página no navegador. O tempo de atualização do cache exibido indica quando o cache foi atualizada pela última vez. Aguardar três minutos e, em seguida, atualize a página, fazendo com que um evento de postback ocorra. Observe que a hora exibida na página foi alterado. Se você atualizar a página em menos de três minutos, o horário exibido na página permanece o mesmo.  
  
 Agora, atualize os dados no banco de dados, usando um comando UPDATE do Transact-SQL e atualize a página. Agora, a hora exibida indica que o cache foi atualizado com os novos dados do banco de dados. Observe que embora o cache é atualizado, o horário exibido na página não é alterado até que ocorra um evento de postback.  
  
## <a name="see-also"></a>Consulte também
- [Notificações de consulta no SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
