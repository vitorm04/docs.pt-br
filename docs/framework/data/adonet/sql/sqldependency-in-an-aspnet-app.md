---
title: SqlDependency em um aplicativo ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: f3e28adc2cf7c24cee9ee344eb78404f01b79793
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780725"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="86da9-102">SqlDependency em um aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="86da9-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="86da9-103">O exemplo nesta seção mostra como usar <xref:System.Data.SqlClient.SqlDependency> indiretamente, aproveitando o objeto ASP.net. <xref:System.Web.Caching.SqlCacheDependency></span><span class="sxs-lookup"><span data-stu-id="86da9-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="86da9-104">O <xref:System.Web.Caching.SqlCacheDependency> objeto usa um <xref:System.Data.SqlClient.SqlDependency> para escutar notificações e atualizar corretamente o cache.</span><span class="sxs-lookup"><span data-stu-id="86da9-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86da9-105">O código de exemplo pressupõe que você habilitou notificações de consulta executando os scripts em [habilitando notificações de consulta](enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="86da9-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="86da9-106">Sobre o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="86da9-106">About the Sample Application</span></span>  
 <span data-ttu-id="86da9-107">O aplicativo de exemplo usa uma única página da Web ASP.net para exibir informações de produto do banco de dados <xref:System.Web.UI.WebControls.GridView> AdventureWorks SQL Server em um controle.</span><span class="sxs-lookup"><span data-stu-id="86da9-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="86da9-108">Quando a página é carregada, o código grava a hora atual em <xref:System.Web.UI.WebControls.Label> um controle.</span><span class="sxs-lookup"><span data-stu-id="86da9-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="86da9-109">Em seguida, ele <xref:System.Web.Caching.SqlCacheDependency> define um objeto e define as <xref:System.Web.Caching.Cache> Propriedades no objeto para armazenar os dados de cache por até três minutos.</span><span class="sxs-lookup"><span data-stu-id="86da9-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="86da9-110">O código, em seguida, se conecta ao banco de dados e os recupera.</span><span class="sxs-lookup"><span data-stu-id="86da9-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="86da9-111">Quando a página for carregada e o aplicativo estiver em execução, o ASP.NET recuperará os dados do cache, que você pode verificar observando se a hora na página não é alterada.</span><span class="sxs-lookup"><span data-stu-id="86da9-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="86da9-112">Se os dados que estão sendo monitorados forem alterados, o ASP.net invalida o cache e `GridView` preenche novamente o controle com dados atualizados, atualizando o `Label` tempo exibido no controle.</span><span class="sxs-lookup"><span data-stu-id="86da9-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="86da9-113">Criando o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="86da9-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="86da9-114">Siga estas etapas para criar e executar o aplicativo de exemplo:</span><span class="sxs-lookup"><span data-stu-id="86da9-114">Follow these steps to create and run the sample application:</span></span>  
  
1. <span data-ttu-id="86da9-115">Crie um novo site do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="86da9-115">Create a new ASP.NET Web site.</span></span>  
  
2. <span data-ttu-id="86da9-116">Adicione um <xref:System.Web.UI.WebControls.Label> e um <xref:System.Web.UI.WebControls.GridView> controle à página default. aspx.</span><span class="sxs-lookup"><span data-stu-id="86da9-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3. <span data-ttu-id="86da9-117">Abra o módulo de classe da página e adicione as seguintes diretivas:</span><span class="sxs-lookup"><span data-stu-id="86da9-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. <span data-ttu-id="86da9-118">Adicione o seguinte código ao evento da `Page_Load` página:</span><span class="sxs-lookup"><span data-stu-id="86da9-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. <span data-ttu-id="86da9-119">Adicione dois métodos `GetConnectionString` auxiliares e `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="86da9-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="86da9-120">A cadeia de conexão definida usa segurança integrada.</span><span class="sxs-lookup"><span data-stu-id="86da9-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="86da9-121">Você precisará verificar se a conta que você está usando tem as permissões de banco de dados necessárias e se o banco de dados de exemplo **AdventureWorks**tem notificações habilitadas.</span><span class="sxs-lookup"><span data-stu-id="86da9-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span>
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="86da9-122">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="86da9-122">Testing the Application</span></span>  
 <span data-ttu-id="86da9-123">O aplicativo armazena em cache os dados exibidos no formulário da Web e os atualiza a cada três minutos, se não houver atividade.</span><span class="sxs-lookup"><span data-stu-id="86da9-123">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="86da9-124">Se ocorrer uma alteração no banco de dados, o cache será atualizado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="86da9-124">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="86da9-125">Execute o aplicativo no Visual Studio, que carrega a página no navegador.</span><span class="sxs-lookup"><span data-stu-id="86da9-125">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="86da9-126">O tempo de atualização do cache exibido indica quando o cache foi atualizado pela última vez.</span><span class="sxs-lookup"><span data-stu-id="86da9-126">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="86da9-127">Aguarde três minutos e, em seguida, atualize a página, fazendo com que ocorra um evento de postback.</span><span class="sxs-lookup"><span data-stu-id="86da9-127">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="86da9-128">Observe que a hora exibida na página foi alterada.</span><span class="sxs-lookup"><span data-stu-id="86da9-128">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="86da9-129">Se você atualizar a página em menos de três minutos, a hora exibida na página permanecerá a mesma.</span><span class="sxs-lookup"><span data-stu-id="86da9-129">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="86da9-130">Agora, atualize os dados no banco de dado, usando um comando de atualização Transact-SQL e atualize a página.</span><span class="sxs-lookup"><span data-stu-id="86da9-130">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="86da9-131">O tempo exibido agora indica que o cache foi atualizado com os novos dados do banco de dado.</span><span class="sxs-lookup"><span data-stu-id="86da9-131">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="86da9-132">Observe que, embora o cache seja atualizado, a hora exibida na página não é alterada até que ocorra um evento de postback.</span><span class="sxs-lookup"><span data-stu-id="86da9-132">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86da9-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86da9-133">See also</span></span>

- [<span data-ttu-id="86da9-134">Notificações de consulta no SQL Server</span><span class="sxs-lookup"><span data-stu-id="86da9-134">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- <span data-ttu-id="86da9-135">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="86da9-135">[ADO.NET Overview](../ado-net-overview.md)</span></span>
