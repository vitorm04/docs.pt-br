---
title: 'Como: definir a cadeia de conexão'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: a78158c7553c0b479b935e3b94931313df912c2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854650"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="c80eb-102">Como: definir a cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="c80eb-102">How to: Define the Connection String</span></span>

<span data-ttu-id="c80eb-103">Este tópico mostra como definir a cadeia de conexão que é usada ao se conectar a um modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="c80eb-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="c80eb-104">Este tópico se baseia no modelo conceitual de [vendas AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="c80eb-104">This topic is based on the [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="c80eb-105">O modelo de vendas AdventureWorks é usado em todos os tópicos relacionados à tarefa na documentação do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c80eb-105">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="c80eb-106">Este tópico pressupõe que você já tenha configurado o Entity Framework e definido o modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c80eb-106">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c80eb-107">Para obter mais informações, confira [Como: Defina manualmente o modelo e os arquivos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="c80eb-107">For more information, see [How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="c80eb-108">Os procedimentos neste tópico também estão incluídos em [como: Configurar manualmente um projeto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))de Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c80eb-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="c80eb-109">Se você usar o assistente de Modelo de Dados de Entidade em um projeto do Visual Studio, ele gerará automaticamente um arquivo. edmx e configurará o projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c80eb-109">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="c80eb-110">Para obter mais informações, confira [Como: Usar o assistente de Modelo de Dados de Entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c80eb-110">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="c80eb-111">Para definir a cadeia de conexão do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c80eb-111">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="c80eb-112">Abra o arquivo de configuração do aplicativo de projeto (app.config) e adicione a seguinte cadeia de conexão:</span><span class="sxs-lookup"><span data-stu-id="c80eb-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="c80eb-113">Se o seu projeto não tiver um arquivo de configuração de aplicativo, você poderá adicionar um, selecionando **Adicionar novo item** no menu **projeto** , selecionando a categoria **geral** , selecionando **arquivo de configuração de aplicativo**e clicando em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="c80eb-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c80eb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c80eb-114">See also</span></span>

- <span data-ttu-id="c80eb-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="c80eb-115">[Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="c80eb-116">[Como: Criar um novo arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c80eb-116">[How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="c80eb-117">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c80eb-117">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
