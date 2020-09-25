---
title: 'Como: tornar arquivos de modelo e mapeamento recursos inseridos'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 8496dcad5422d1a45af52e58325efd360768da34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198282"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="ee394-102">Como: tornar arquivos de modelo e mapeamento recursos inseridos</span><span class="sxs-lookup"><span data-stu-id="ee394-102">How to: Make Model and Mapping Files Embedded Resources</span></span>

<span data-ttu-id="ee394-103">O Entity Framework permite que você implante arquivos de modelo e de mapeamento como recursos incorporados de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee394-103">The Entity Framework enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="ee394-104">O assembly com o modelo inserido e os arquivos de mapeamento devem ser carregados no mesmo domínio de aplicativo que a conexão de entidade.</span><span class="sxs-lookup"><span data-stu-id="ee394-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="ee394-105">Para saber mais, confira [Cadeias de conexão](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="ee394-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="ee394-106">Por padrão, as ferramentas de Modelo de Dados de Entidade inserem o modelo e os arquivos de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="ee394-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="ee394-107">Ao definir manualmente o modelo e os arquivos de mapeamento, use este procedimento para garantir que os arquivos sejam implantados como recursos incorporados junto com um aplicativo Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ee394-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an Entity Framework application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee394-108">Para manter os recursos inseridos, você deverá repetir este procedimento sempre que os arquivos de modelo e mapeamento forem modificados.</span><span class="sxs-lookup"><span data-stu-id="ee394-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="ee394-109">Para inserir os arquivos de modelo e mapeamento</span><span class="sxs-lookup"><span data-stu-id="ee394-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="ee394-110">Em **Gerenciador de soluções**, selecione o arquivo conceitual (. CSDL).</span><span class="sxs-lookup"><span data-stu-id="ee394-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="ee394-111">No painel **Propriedades** , defina **ação de compilação** como **recurso incorporado**.</span><span class="sxs-lookup"><span data-stu-id="ee394-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="ee394-112">Repita as etapas 1 e 2 para o arquivo de armazenamento (.ssdl) e o arquivo de mapeamento (.msl).</span><span class="sxs-lookup"><span data-stu-id="ee394-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="ee394-113">Em **Gerenciador de soluções**, clique duas vezes no arquivo App.config e modifique o `Metadata` parâmetro no `connectionString` atributo com base em um dos seguintes formatos:</span><span class="sxs-lookup"><span data-stu-id="ee394-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="ee394-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="ee394-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="ee394-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="ee394-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="ee394-116">Para saber mais, confira [Cadeias de conexão](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="ee394-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee394-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee394-117">Example</span></span>  

 <span data-ttu-id="ee394-118">A cadeia de conexão a seguir faz referência a arquivos de mapeamento e modelo inseridos para o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="ee394-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="ee394-119">Esta cadeia de conexão é armazenada no arquivo App.config do projeto.</span><span class="sxs-lookup"><span data-stu-id="ee394-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ee394-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="ee394-120">See also</span></span>

- [<span data-ttu-id="ee394-121">Modelando e mapeando</span><span class="sxs-lookup"><span data-stu-id="ee394-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="ee394-122">Como: definir a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="ee394-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="ee394-123">Como: criar uma cadeia de conexão EntityConnection</span><span class="sxs-lookup"><span data-stu-id="ee394-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="ee394-124">[Ferramentas de Modelo de Dados de Entidade de ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ee394-124">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
