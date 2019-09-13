---
title: 'Como: Gerar manualmente classes de serviço de dados do cliente (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: f8d99213a1ef98c48855ba9f561f87a800768c89
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894305"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="9f7af-102">Como: Gerar manualmente classes de serviço de dados do cliente (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9f7af-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
<span data-ttu-id="9f7af-103">O WCF Data Services integra-se com o Visual Studio para permitir que você gere automaticamente classes de serviço de dados do cliente quando você usa a caixa de diálogo **Adicionar referência de serviço** para adicionar uma referência a um serviço de dados em um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f7af-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="9f7af-104">Para obter mais informações, confira [Como: Adicione uma referência](how-to-add-a-data-service-reference-wcf-data-services.md)de serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="9f7af-104">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="9f7af-105">Você também pode gerar manualmente as mesmas classes de serviço de dados do cliente usando a ferramenta de geração `DataSvcUtil.exe`de código,.</span><span class="sxs-lookup"><span data-stu-id="9f7af-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="9f7af-106">Essa ferramenta, que é incluída com o WCF Data Services, gera .NET Framework classes da definição do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="9f7af-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="9f7af-107">Ele também pode ser usado para gerar classes de serviço de dados do arquivo de modelo conceitual (. CSDL) e do arquivo. edmx que representa um modelo de Entity Framework em um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f7af-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="9f7af-108">O exemplo neste tópico cria classes de serviço de dados do cliente com base no serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9f7af-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="9f7af-109">Esse serviço é criado quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9f7af-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="9f7af-110">Alguns exemplos neste tópico exigem o arquivo de modelo conceitual para o modelo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9f7af-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="9f7af-111">Para obter mais informações, confira [Como: Use EdmGen. exe para gerar o modelo e os arquivos](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="9f7af-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="9f7af-112">Alguns exemplos neste tópico exigem o arquivo. edmx para o modelo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9f7af-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="9f7af-113">Para obter mais informações, consulte [visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9f7af-113">For more information, see [.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="9f7af-114">Para gerar C# classes que dão suporte à vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="9f7af-114">To generate C# classes that support data binding</span></span>

- <span data-ttu-id="9f7af-115">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="9f7af-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="9f7af-116">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9f7af-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="9f7af-117">Para gerar Visual Basic classes que dão suporte à associação de dados</span><span class="sxs-lookup"><span data-stu-id="9f7af-117">To generate Visual Basic classes that support data binding</span></span>

- <span data-ttu-id="9f7af-118">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="9f7af-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="9f7af-119">Você deve substituir o valor fornecido para `/uri:` o parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9f7af-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="9f7af-120">Para gerar C# classes com base no URI do serviço</span><span class="sxs-lookup"><span data-stu-id="9f7af-120">To generate C# classes based on the service URI</span></span>

- <span data-ttu-id="9f7af-121">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="9f7af-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="9f7af-122">Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9f7af-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="9f7af-123">Para gerar Visual Basic classes com base no URI do serviço</span><span class="sxs-lookup"><span data-stu-id="9f7af-123">To generate Visual Basic classes based on the service URI</span></span>

- <span data-ttu-id="9f7af-124">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="9f7af-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="9f7af-125">Você deve substituir o valor fornecido para `/uri:` o parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9f7af-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="9f7af-126">Para gerar C# classes com base no arquivo de modelo conceitual (CSDL)</span><span class="sxs-lookup"><span data-stu-id="9f7af-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="9f7af-127">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="9f7af-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="9f7af-128">Para gerar Visual Basic classes com base no arquivo de modelo conceitual (CSDL)</span><span class="sxs-lookup"><span data-stu-id="9f7af-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="9f7af-129">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="9f7af-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="9f7af-130">Para gerar C# classes com base no arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="9f7af-130">To generate C# classes based on the .edmx file</span></span>

- <span data-ttu-id="9f7af-131">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="9f7af-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="9f7af-132">Para gerar Visual Basic classes com base no arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="9f7af-132">To generate Visual Basic classes based on the .edmx file</span></span>

- <span data-ttu-id="9f7af-133">No prompt de comando, execute o seguinte comando sem quebras de linha:</span><span class="sxs-lookup"><span data-stu-id="9f7af-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="9f7af-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f7af-134">See also</span></span>

- <span data-ttu-id="9f7af-135">[Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="9f7af-135">[Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md)</span></span>
- [<span data-ttu-id="9f7af-136">Como: Adicionar uma referência de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="9f7af-136">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="9f7af-137">Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="9f7af-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](wcf-data-service-client-utility-datasvcutil-exe.md)
