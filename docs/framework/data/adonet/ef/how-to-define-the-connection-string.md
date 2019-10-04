---
title: 'Como: definir a cadeia de conexão'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9ce0b427cac17fc338877c5f85d3648d15d5ee14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833948"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="c9c1f-102">Como: definir a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="c9c1f-102">How to: Define the Connection String</span></span>

<span data-ttu-id="c9c1f-103">Este tópico mostra como definir a cadeia de conexão que é usada ao se conectar a um modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="c9c1f-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="c9c1f-104">Este tópico se baseia no modelo conceitual de [vendas AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="c9c1f-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="c9c1f-105">O modelo de vendas AdventureWorks é usado em todos os tópicos relacionados à tarefa na documentação do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c9c1f-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="c9c1f-106">Este tópico pressupõe que você já tenha configurado o Entity Framework e definido o modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c9c1f-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c9c1f-107">Para obter mais informações, confira [Como: Defina manualmente o modelo e os arquivos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="c9c1f-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="c9c1f-108">Os procedimentos neste tópico também estão incluídos em [como: Configurar manualmente um projeto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))de Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c9c1f-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="c9c1f-109">Se você usar o assistente de Modelo de Dados de Entidade em um projeto do Visual Studio, ele gerará automaticamente um arquivo. edmx e configurará o projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c9c1f-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="c9c1f-110">Para obter mais informações, confira [Como: Use o assistente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))de modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="c9c1f-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="c9c1f-111">Para definir a cadeia de conexão do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c9c1f-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="c9c1f-112">Abra o arquivo de configuração do aplicativo de projeto (app.config) e adicione a seguinte cadeia de conexão:</span><span class="sxs-lookup"><span data-stu-id="c9c1f-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="c9c1f-113">Se o seu projeto não tiver um arquivo de configuração de aplicativo, você poderá adicionar um, selecionando **Adicionar novo item** no menu **projeto** , selecionando a categoria **geral** , selecionando **arquivo de configuração de aplicativo**e clicando em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="c9c1f-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9c1f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9c1f-114">See also</span></span>

- <span data-ttu-id="c9c1f-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="c9c1f-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="c9c1f-116">[Como: Criar um novo arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c9c1f-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="c9c1f-117">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c9c1f-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
