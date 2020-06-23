---
title: Como usar o Svcutil.exe para baixar documentos de metadados
description: Saiba como usar Svcutil.exe para baixar metadados de serviços em execução e salvar os metadados em arquivos locais.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 42df55fe7bbae6d8c977263e05053d8a8fa87aff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246760"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="07674-103">Como usar o Svcutil.exe para baixar documentos de metadados</span><span class="sxs-lookup"><span data-stu-id="07674-103">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="07674-104">Você pode usar Svcutil.exe para baixar metadados de serviços em execução e para salvar os metadados em arquivos locais.</span><span class="sxs-lookup"><span data-stu-id="07674-104">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="07674-105">Para esquemas de URL HTTP e HTTPS, Svcutil.exe tenta recuperar metadados usando o WS-MetadataExchange e a [descoberta de serviço Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="07674-105">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="07674-106">Para todos os outros esquemas de URL, Svcutil.exe usa apenas WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="07674-106">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="07674-107">Por padrão, Svcutil.exe usa as associações definidas na <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe.</span><span class="sxs-lookup"><span data-stu-id="07674-107">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="07674-108">Para configurar a associação usada para WS-MetadataExchange, você deve definir um ponto de extremidade do cliente no arquivo de configuração para Svcutil.exe (svcutil.exe.config) que usa o `IMetadataExchange` contrato e que tem o mesmo nome que o esquema de Uniform Resource Identifier (URI) do endereço do ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="07674-108">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="07674-109">Ao executar Svcutil.exe para obter metadados para um serviço que expõe dois contratos de serviço diferentes que cada um contém uma operação de mesmo nome, Svcutil.exe exibe um erro dizendo "não é possível obter metadados de..." Por exemplo, se você tiver um serviço que expõe um contrato de serviço chamado `ICarService` que tem uma operação `Get(Car c)` e o mesmo serviço expõe um contrato de serviço chamado `IBookService` que tem uma operação `Get(Book b)` .</span><span class="sxs-lookup"><span data-stu-id="07674-109">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="07674-110">Para contornar esse problema, adote uma das seguintes medidas:</span><span class="sxs-lookup"><span data-stu-id="07674-110">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="07674-111">Renomeie uma das operações.</span><span class="sxs-lookup"><span data-stu-id="07674-111">Rename one of the operations.</span></span>
> - <span data-ttu-id="07674-112">Defina <xref:System.ServiceModel.OperationContractAttribute.Name%2A> como um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="07674-112">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="07674-113">Defina um dos namespaces de operações para um namespace diferente usando a <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="07674-113">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="07674-114">Para baixar metadados usando Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="07674-114">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="07674-115">Localize a ferramenta de Svcutil.exe no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="07674-115">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="07674-116">C:\Arquivos de Programas\microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="07674-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="07674-117">No prompt de comando, inicie a ferramenta usando o formato a seguir.</span><span class="sxs-lookup"><span data-stu-id="07674-117">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="07674-118">Você deve especificar a `/t:metadata` opção para baixar metadados.</span><span class="sxs-lookup"><span data-stu-id="07674-118">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="07674-119">Caso contrário, o código do cliente e a configuração serão gerados.</span><span class="sxs-lookup"><span data-stu-id="07674-119">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="07674-120">O `url` argumento <>especifica a URL para um ponto de extremidade de serviço que fornece metadados ou para um documento de metadados hospedado online.</span><span class="sxs-lookup"><span data-stu-id="07674-120">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="07674-121">O `epr` argumento <> especifica o caminho para um arquivo XML que contém um WS-Addressing `EndpointAddress` para um ponto de extremidade de serviço que oferece suporte a WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="07674-121">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="07674-122">Para obter mais opções sobre como usar essa ferramenta para download de metadados, consulte [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="07674-122">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07674-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07674-123">Example</span></span>  
 <span data-ttu-id="07674-124">O comando a seguir baixa os documentos de metadados de um serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="07674-124">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="07674-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="07674-125">See also</span></span>

- [<span data-ttu-id="07674-126">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="07674-126">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
