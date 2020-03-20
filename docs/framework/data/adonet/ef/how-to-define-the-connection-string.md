---
title: Como definir a cadeia de conexão
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150565"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="723fc-102">Como definir a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="723fc-102">How to: Define the Connection String</span></span>

<span data-ttu-id="723fc-103">Este tópico mostra como definir a cadeia de conexão que é usada ao se conectar a um modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="723fc-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="723fc-104">Este tópico é baseado no modelo conceitual [AdventureWorks Sales.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="723fc-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="723fc-105">O Modelo de Vendas AdventureWorks é usado em todos os tópicos relacionados à tarefa na documentação Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="723fc-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="723fc-106">Este tópico pressupõe que você já configurou o Framework entity e definiu o Modelo de Vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="723fc-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="723fc-107">Para obter mais informações, [consulte Como definir manualmente os arquivos de modelo e mapeamento](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="723fc-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="723fc-108">Os procedimentos neste tópico também estão incluídos em [Como: Configurar manualmente um Projeto Estrutura de Entidades](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="723fc-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="723fc-109">Se você usar o Assistente de Modelo de Dados de Entidade em um projeto do Visual Studio, ele gerará automaticamente um arquivo .edmx e configurará o projeto para usar o Framework entity.</span><span class="sxs-lookup"><span data-stu-id="723fc-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="723fc-110">Para obter mais informações, consulte [Como: Usar o Assistente do Modelo de Dados da Entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="723fc-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="723fc-111">Para definir a cadeia de conexão do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="723fc-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="723fc-112">Abra o arquivo de configuração do aplicativo de projeto (app.config) e adicione a seguinte cadeia de conexão:</span><span class="sxs-lookup"><span data-stu-id="723fc-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="723fc-113">Se o seu projeto não tiver um arquivo de configuração de aplicativo, você pode adicionar um selecionando **Adicionar novo item** no menu **Projeto,** selecionando a categoria **Geral,** selecionando **Arquivo de configuração de aplicativo**e, em seguida, clicando em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="723fc-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="723fc-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="723fc-114">See also</span></span>

- <span data-ttu-id="723fc-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="723fc-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="723fc-116">[Como: Criar um novo arquivo .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="723fc-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="723fc-117">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="723fc-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
