---
title: Como tornar arquivos de modelo e mapeamento recursos inseridos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98fb3ada369279a34ed08110644aabcbbe72a501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="ee11d-102">Como tornar arquivos de modelo e mapeamento recursos inseridos</span><span class="sxs-lookup"><span data-stu-id="ee11d-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="ee11d-103">O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permite que você implante o modelo e arquivos de mapeamento como recursos incorporados de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee11d-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="ee11d-104">O assembly com o modelo inserido e os arquivos de mapeamento devem ser carregados no mesmo domínio de aplicativo que a conexão de entidade.</span><span class="sxs-lookup"><span data-stu-id="ee11d-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="ee11d-105">Para obter mais informações, consulte [cadeias de caracteres de Conexão](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="ee11d-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="ee11d-106">Por padrão, o [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] ferramentas incorporem o modelo e os arquivos de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="ee11d-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="ee11d-107">Quando você definir manualmente o modelo e os arquivos de mapeamento, use este procedimento para garantir que os arquivos são implantados como recursos incorporados junto com um [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee11d-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee11d-108">Para manter os recursos inseridos, você deverá repetir este procedimento sempre que os arquivos de modelo e mapeamento forem modificados.</span><span class="sxs-lookup"><span data-stu-id="ee11d-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="ee11d-109">Para inserir os arquivos de modelo e mapeamento</span><span class="sxs-lookup"><span data-stu-id="ee11d-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="ee11d-110">Em **Solution Explorer**, selecione o arquivo (. CSDL) conceitual.</span><span class="sxs-lookup"><span data-stu-id="ee11d-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="ee11d-111">No **propriedades** painel, defina **ação de compilação** para **recurso inserido**.</span><span class="sxs-lookup"><span data-stu-id="ee11d-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="ee11d-112">Repita as etapas 1 e 2 para o arquivo de armazenamento (.ssdl) e o arquivo de mapeamento (.msl).</span><span class="sxs-lookup"><span data-stu-id="ee11d-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="ee11d-113">Em **Solution Explorer**, duas vezes no arquivo App. config e, em seguida, modificar o `Metadata` parâmetro no `connectionString` atributo baseado em um dos seguintes formatos:</span><span class="sxs-lookup"><span data-stu-id="ee11d-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="ee11d-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="ee11d-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="ee11d-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="ee11d-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="ee11d-116">Para obter mais informações, consulte [cadeias de caracteres de Conexão](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="ee11d-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee11d-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee11d-117">Example</span></span>  
 <span data-ttu-id="ee11d-118">A seguinte cadeia de conexão faz referência modelo inserido e arquivos de mapeamento para o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="ee11d-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="ee11d-119">Esta cadeia de conexão é armazenada no arquivo App.config do projeto.</span><span class="sxs-lookup"><span data-stu-id="ee11d-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="ee11d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee11d-120">See Also</span></span>  
 [<span data-ttu-id="ee11d-121">Modelando e mapeando</span><span class="sxs-lookup"><span data-stu-id="ee11d-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="ee11d-122">Como: definir a cadeia de caracteres de Conexão</span><span class="sxs-lookup"><span data-stu-id="ee11d-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [<span data-ttu-id="ee11d-123">Como: criar uma cadeia de caracteres de Conexão EntityConnection</span><span class="sxs-lookup"><span data-stu-id="ee11d-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 <span data-ttu-id="ee11d-124">[ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ee11d-124">[ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)</span></span>
