---
title: Trabalhando com a linguagem de definição de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 25d7f49644996d87ddb5d191dc313916c0ca6fbb
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270836"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="0af89-102">Trabalhando com a linguagem de definição de dados</span><span class="sxs-lookup"><span data-stu-id="0af89-102">Working with Data Definition Language</span></span>
<span data-ttu-id="0af89-103">Começando com o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] versão 4, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dá suporte à linguagem de definição de dados (DDL).</span><span class="sxs-lookup"><span data-stu-id="0af89-103">Starting with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="0af89-104">Isso permite que você crie ou exclua uma instância do banco de dados com base na cadeia de conexão e nos metadados do modelo de armazenamento (SSDL).</span><span class="sxs-lookup"><span data-stu-id="0af89-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="0af89-105">Os métodos a seguir no <xref:System.Data.Objects.ObjectContext> usam a cadeia de conexão e o conteúdo SSDL para criar ou excluir o banco de dados, verificar se o banco de dados existe e exibir o script DDL gerado:</span><span class="sxs-lookup"><span data-stu-id="0af89-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  <span data-ttu-id="0af89-106">A execução de comandos DDL pressupõe permissões suficientes.</span><span class="sxs-lookup"><span data-stu-id="0af89-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="0af89-107">Os métodos listados anteriormente delegam a maioria do trabalho para o provedor de dados ADO.NET subjacente.</span><span class="sxs-lookup"><span data-stu-id="0af89-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="0af89-108">É responsabilidade do provedor garantir que a convenção de nomenclatura usada para gerar objetos de banco de dados seja consistente com as convenções usadas nas consultas e atualizações.</span><span class="sxs-lookup"><span data-stu-id="0af89-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="0af89-109">O exemplo a seguir mostra como gerar o banco de dados com base no modelo existente.</span><span class="sxs-lookup"><span data-stu-id="0af89-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="0af89-110">Ele também adiciona um novo objeto de entidade ao contexto de objeto e os salva no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0af89-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0af89-111">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="0af89-111">Procedures</span></span>  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="0af89-112">Para definir um banco de dados com base no modelo existente</span><span class="sxs-lookup"><span data-stu-id="0af89-112">To define a database based on the existing model</span></span>  
  
1.  <span data-ttu-id="0af89-113">Crie um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="0af89-113">Create a console application.</span></span>  
  
2.  <span data-ttu-id="0af89-114">Adicione um modelo existente ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0af89-114">Add an existing model to your application.</span></span>  
  
    1.  <span data-ttu-id="0af89-115">Adicionar um modelo vazio chamado `SchoolModel`.</span><span class="sxs-lookup"><span data-stu-id="0af89-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="0af89-116">Para criar um modelo vazio, consulte a [como: criar um novo. do EDMX arquivo](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) tópico.</span><span class="sxs-lookup"><span data-stu-id="0af89-116">To create an empty model, see the [How to: Create a New .edmx File](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) topic.</span></span>  
  
     <span data-ttu-id="0af89-117">O arquivo SchoolModel.edmx é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0af89-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1.  <span data-ttu-id="0af89-118">Copiar o conceitual, armazenamento e mapeamento de conteúdo para o modelo de escola dos [modelo de escola](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) tópico.</span><span class="sxs-lookup"><span data-stu-id="0af89-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) topic.</span></span>  
  
    2.  <span data-ttu-id="0af89-119">Abra o arquivo SchoolModel.edmx e cole o conteúdo nas marcas `edmx:Runtime`.</span><span class="sxs-lookup"><span data-stu-id="0af89-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3.  <span data-ttu-id="0af89-120">Adicione o seguinte código à função principal.</span><span class="sxs-lookup"><span data-stu-id="0af89-120">Add the following code to your main function.</span></span> <span data-ttu-id="0af89-121">O código inicializa a cadeia de conexão ao servidor de banco de dados, exibe o script DDL, cria o banco de dados, adiciona uma nova entidade ao contexto e salva as alterações no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0af89-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
