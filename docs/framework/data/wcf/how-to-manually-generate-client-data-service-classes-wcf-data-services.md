---
title: 'Como: gerar manualmente as Classes de serviço de dados do cliente (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 332c04f50e104a5e1c8bd18c05581b6c0472f82f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501315"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="b68b4-102">Como: gerar manualmente as Classes de serviço de dados do cliente (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="b68b4-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
<span data-ttu-id="b68b4-103">WCF Data Services se integra com o Visual Studio para que você possa gerar classes de serviço de dados do cliente automaticamente quando você usa o **adicionar referência de serviço** caixa de diálogo para adicionar uma referência a um serviço de dados em um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b68b4-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="b68b4-104">Para obter mais informações, consulte [como: adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b68b4-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="b68b4-105">Você pode gerar também manualmente as mesmas classes de serviço de dados do cliente usando a ferramenta de geração de código, `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="b68b4-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="b68b4-106">Essa ferramenta, que está incluída com o WCF Data Services, gera classes do .NET Framework da definição de serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="b68b4-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="b68b4-107">Ele também pode ser usado para gerar classes de serviço de dados do arquivo de modelo conceitual (. CSDL) e do arquivo. edmx que representa um modelo do Entity Framework em um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b68b4-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="b68b4-108">O exemplo neste tópico cria classes de serviço de dados do cliente com base no serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="b68b4-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="b68b4-109">Esse serviço é criado quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b68b4-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="b68b4-110">Alguns exemplos neste tópico requerem o arquivo de modelo conceitual para o modelo do Northwind.</span><span class="sxs-lookup"><span data-stu-id="b68b4-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="b68b4-111">Para obter mais informações, consulte [como: Use EdmGen.exe para gerar arquivos de modelo e mapeamento](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="b68b4-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="b68b4-112">Alguns exemplos neste tópico exigem o arquivo. edmx para o modelo do Northwind.</span><span class="sxs-lookup"><span data-stu-id="b68b4-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="b68b4-113">Para obter mais informações, consulte [visão geral do arquivo. edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span><span class="sxs-lookup"><span data-stu-id="b68b4-113">For more information, see [.edmx File Overview](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="b68b4-114">Para gerar classes c# que dão suporte à vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="b68b4-114">To generate C# classes that support data binding</span></span>

-   <span data-ttu-id="b68b4-115">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="b68b4-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="b68b4-116">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="b68b4-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="b68b4-117">Para gerar classes de Visual Basic que suportam associação de dados</span><span class="sxs-lookup"><span data-stu-id="b68b4-117">To generate Visual Basic classes that support data binding</span></span>

-   <span data-ttu-id="b68b4-118">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="b68b4-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="b68b4-119">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="b68b4-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="b68b4-120">Para gerar classes c# com base no URI de serviço</span><span class="sxs-lookup"><span data-stu-id="b68b4-120">To generate C# classes based on the service URI</span></span>

-   <span data-ttu-id="b68b4-121">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="b68b4-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="b68b4-122">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="b68b4-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="b68b4-123">Para gerar classes do Visual Basic com base no URI de serviço</span><span class="sxs-lookup"><span data-stu-id="b68b4-123">To generate Visual Basic classes based on the service URI</span></span>

-   <span data-ttu-id="b68b4-124">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="b68b4-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="b68b4-125">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="b68b4-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="b68b4-126">Para gerar classes c# baseadas no arquivo de modelo conceitual (CSDL)</span><span class="sxs-lookup"><span data-stu-id="b68b4-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

-   <span data-ttu-id="b68b4-127">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="b68b4-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="b68b4-128">Para gerar classes do Visual Basic com base no arquivo de modelo conceitual (CSDL)</span><span class="sxs-lookup"><span data-stu-id="b68b4-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

-   <span data-ttu-id="b68b4-129">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="b68b4-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="b68b4-130">Para gerar classes c# com base em arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="b68b4-130">To generate C# classes based on the .edmx file</span></span>

-   <span data-ttu-id="b68b4-131">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="b68b4-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="b68b4-132">Para gerar classes do Visual Basic com base em arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="b68b4-132">To generate Visual Basic classes based on the .edmx file</span></span>

-   <span data-ttu-id="b68b4-133">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="b68b4-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="b68b4-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b68b4-134">See Also</span></span>

- <span data-ttu-id="b68b4-135">[Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="b68b4-135">[Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)</span></span>
- [<span data-ttu-id="b68b4-136">Como adicionar uma referência de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="b68b4-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="b68b4-137">Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="b68b4-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)