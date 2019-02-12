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
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="eae15-102">SqlDependency em um aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="eae15-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="eae15-103">O exemplo nesta seção mostra como usar <xref:System.Data.SqlClient.SqlDependency> indiretamente, aproveitando o ASP.NET <xref:System.Web.Caching.SqlCacheDependency> objeto.</span><span class="sxs-lookup"><span data-stu-id="eae15-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="eae15-104">O <xref:System.Web.Caching.SqlCacheDependency> objeto usa um <xref:System.Data.SqlClient.SqlDependency> para ouvir as notificações e atualizar corretamente o cache.</span><span class="sxs-lookup"><span data-stu-id="eae15-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eae15-105">O exemplo de código pressupõe que você habilitou as notificações de consulta, executando os scripts [habilitando notificações de consulta](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="eae15-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="eae15-106">Sobre o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="eae15-106">About the Sample Application</span></span>  
 <span data-ttu-id="eae15-107">O aplicativo de exemplo usa uma única página da Web do ASP.NET para exibir informações de produto a **AdventureWorks** banco de dados do SQL Server em um <xref:System.Web.UI.WebControls.GridView> controle.</span><span class="sxs-lookup"><span data-stu-id="eae15-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="eae15-108">Quando a página for carregada, o código grava a hora atual para um <xref:System.Web.UI.WebControls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="eae15-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="eae15-109">Em seguida, ele define uma <xref:System.Web.Caching.SqlCacheDependency> do objeto e define as propriedades no <xref:System.Web.Caching.Cache> objeto para armazenar os dados do cache de até três minutos.</span><span class="sxs-lookup"><span data-stu-id="eae15-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="eae15-110">O código, em seguida, conecta-se ao banco de dados e recupera os dados.</span><span class="sxs-lookup"><span data-stu-id="eae15-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="eae15-111">Quando a página é carregada e o aplicativo está executando o ASP.NET irá recuperar os dados do cache, você pode confirmar ao observar que o tempo na página não é alterado.</span><span class="sxs-lookup"><span data-stu-id="eae15-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="eae15-112">Se os dados que estão sendo monitorados forem alterados, ASP.NET invalida o cache e preencher novamente o `GridView` controle com dados atualizados, atualizando o horário exibido no `Label` controle.</span><span class="sxs-lookup"><span data-stu-id="eae15-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="eae15-113">Criando o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="eae15-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="eae15-114">Siga estas etapas para criar e executar o aplicativo de exemplo:</span><span class="sxs-lookup"><span data-stu-id="eae15-114">Follow these steps to create and run the sample application:</span></span>  
  
1.  <span data-ttu-id="eae15-115">Crie um novo site da Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eae15-115">Create a new ASP.NET Web site.</span></span>  
  
2.  <span data-ttu-id="eae15-116">Adicionar um <xref:System.Web.UI.WebControls.Label> e um <xref:System.Web.UI.WebControls.GridView> controle para a página Default. aspx.</span><span class="sxs-lookup"><span data-stu-id="eae15-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3.  <span data-ttu-id="eae15-117">Abra o módulo de classe da página e adicione as seguintes diretivas:</span><span class="sxs-lookup"><span data-stu-id="eae15-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  <span data-ttu-id="eae15-118">Adicione o seguinte código na página de `Page_Load` eventos:</span><span class="sxs-lookup"><span data-stu-id="eae15-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  <span data-ttu-id="eae15-119">Adicione dois métodos auxiliares, `GetConnectionString` e `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="eae15-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="eae15-120">A cadeia de conexão definida usa a segurança integrada.</span><span class="sxs-lookup"><span data-stu-id="eae15-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="eae15-121">Você precisará verificar se a conta que você está usando tem as permissões de banco de dados necessários e que o banco de dados de exemplo, **AdventureWorks**, tem notificações habilitadas.</span><span class="sxs-lookup"><span data-stu-id="eae15-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span>
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="eae15-122">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="eae15-122">Testing the Application</span></span>  
 <span data-ttu-id="eae15-123">O aplicativo armazena em cache os dados exibidos no formulário da Web e atualiza a cada três minutos se não houver nenhuma atividade.</span><span class="sxs-lookup"><span data-stu-id="eae15-123">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="eae15-124">Se ocorrer uma alteração no banco de dados, o cache é atualizado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="eae15-124">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="eae15-125">Execute o aplicativo do Visual Studio, que carrega a página no navegador.</span><span class="sxs-lookup"><span data-stu-id="eae15-125">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="eae15-126">O tempo de atualização do cache exibido indica quando o cache foi atualizada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="eae15-126">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="eae15-127">Aguardar três minutos e, em seguida, atualize a página, fazendo com que um evento de postback ocorra.</span><span class="sxs-lookup"><span data-stu-id="eae15-127">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="eae15-128">Observe que a hora exibida na página foi alterado.</span><span class="sxs-lookup"><span data-stu-id="eae15-128">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="eae15-129">Se você atualizar a página em menos de três minutos, o horário exibido na página permanece o mesmo.</span><span class="sxs-lookup"><span data-stu-id="eae15-129">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="eae15-130">Agora, atualize os dados no banco de dados, usando um comando UPDATE do Transact-SQL e atualize a página.</span><span class="sxs-lookup"><span data-stu-id="eae15-130">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="eae15-131">Agora, a hora exibida indica que o cache foi atualizado com os novos dados do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="eae15-131">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="eae15-132">Observe que embora o cache é atualizado, o horário exibido na página não é alterado até que ocorra um evento de postback.</span><span class="sxs-lookup"><span data-stu-id="eae15-132">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae15-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eae15-133">See also</span></span>
- [<span data-ttu-id="eae15-134">Notificações de consulta no SQL Server</span><span class="sxs-lookup"><span data-stu-id="eae15-134">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- <span data-ttu-id="eae15-135">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="eae15-135">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
