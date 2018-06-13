---
title: 'Como: gerar manualmente as Classes de serviço de dados do cliente (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 24d19f10e025b765cfc7df73ba80d223fbfa8074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358988"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="87122-102">Como: gerar manualmente as Classes de serviço de dados do cliente (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="87122-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="87122-103"> integra-se com o Visual Studio para que você possa gerar classes de serviço de dados do cliente automaticamente quando você usa o **adicionar referência de serviço** caixa de diálogo para adicionar uma referência a um serviço de dados em um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87122-103"> integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="87122-104">Para obter mais informações, consulte [como: adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="87122-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="87122-105">Você pode gerar manualmente as mesmas classes de serviço de dados do cliente usando a ferramenta de geração de código, `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="87122-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="87122-106">Essa ferramenta, que está incluída no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], gera classes do .NET Framework da definição de serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="87122-106">This tool, which is included with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="87122-107">Ele também pode ser usado para gerar classes de serviço de dados do arquivo de modelo conceitual. (CSDL) e do arquivo. edmx que representa um modelo do Entity Framework em um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87122-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>  
  
 <span data-ttu-id="87122-108">O exemplo neste tópico cria classes de serviço de dados do cliente com base no serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="87122-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="87122-109">Esse serviço é criado quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="87122-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="87122-110">Alguns exemplos neste tópico exigem o arquivo de modelo conceitual para o modelo do Northwind.</span><span class="sxs-lookup"><span data-stu-id="87122-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="87122-111">Para obter mais informações, consulte [como: Use EdmGen.exe para gerar o modelo e os arquivos de mapeamento](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="87122-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="87122-112">Alguns exemplos neste tópico exigem o arquivo. edmx para o modelo do Northwind.</span><span class="sxs-lookup"><span data-stu-id="87122-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="87122-113">Para obter mais informações, consulte [. edmx visão geral do arquivo](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span><span class="sxs-lookup"><span data-stu-id="87122-113">For more information, see [.edmx File Overview](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span></span>  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="87122-114">Para gerar classes c# que dão suporte a associação de dados</span><span class="sxs-lookup"><span data-stu-id="87122-114">To generate C# classes that support data binding</span></span>  
  
-   <span data-ttu-id="87122-115">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87122-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="87122-116">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI da sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="87122-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="87122-117">Para gerar classes do Visual Basic que oferecem suporte à associação de dados</span><span class="sxs-lookup"><span data-stu-id="87122-117">To generate Visual Basic classes that support data binding</span></span>  
  
-   <span data-ttu-id="87122-118">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87122-118">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="87122-119">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI da sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="87122-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="87122-120">Para gerar classes c# com base no URI de serviço</span><span class="sxs-lookup"><span data-stu-id="87122-120">To generate C# classes based on the service URI</span></span>  
  
-   <span data-ttu-id="87122-121">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87122-121">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="87122-122">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI da sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="87122-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="87122-123">Para gerar classes do Visual Basic com base no URI de serviço</span><span class="sxs-lookup"><span data-stu-id="87122-123">To generate Visual Basic classes based on the service URI</span></span>  
  
-   <span data-ttu-id="87122-124">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87122-124">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="87122-125">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI da sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="87122-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="87122-126">Para gerar classes c# baseados no arquivo de modelo conceitual (CSDL)</span><span class="sxs-lookup"><span data-stu-id="87122-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="87122-127">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87122-127">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="87122-128">Para gerar classes do Visual Basic com base no arquivo de modelo conceitual (CSDL)</span><span class="sxs-lookup"><span data-stu-id="87122-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="87122-129">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87122-129">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="87122-130">Para gerar classes c# com base no arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="87122-130">To generate C# classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="87122-131">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87122-131">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="87122-132">Para gerar classes do Visual Basic com base no arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="87122-132">To generate Visual Basic classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="87122-133">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="87122-133">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="87122-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87122-134">See Also</span></span>  
 <span data-ttu-id="87122-135">[Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="87122-135">[Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)</span></span>  
 [<span data-ttu-id="87122-136">Como adicionar uma referência de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="87122-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [<span data-ttu-id="87122-137">Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="87122-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
