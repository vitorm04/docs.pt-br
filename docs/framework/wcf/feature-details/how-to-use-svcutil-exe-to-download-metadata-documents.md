---
title: Como usar o Svcutil.exe para baixar documentos de metadados
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 359cdb58ef65c9fb69c0ecfc759f70164a369cce
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212110"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="44bc1-102">Como usar o Svcutil.exe para baixar documentos de metadados</span><span class="sxs-lookup"><span data-stu-id="44bc1-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="44bc1-103">Você pode usar svcutil. exe para baixar metadados de serviços em execução e para salvar os metadados em arquivos locais.</span><span class="sxs-lookup"><span data-stu-id="44bc1-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="44bc1-104">Para esquemas de URL HTTP e HTTPS, svcutil. exe tenta recuperar metadados usando o WS-MetadataExchange e a [descoberta de serviço Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="44bc1-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="44bc1-105">Para todos os outros esquemas de URL, svcutil. exe usa apenas WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="44bc1-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="44bc1-106">Por padrão, svcutil. exe usa as associações definidas na classe <xref:System.ServiceModel.Description.MetadataExchangeBindings>.</span><span class="sxs-lookup"><span data-stu-id="44bc1-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="44bc1-107">Para configurar a associação usada para WS-MetadataExchange, você deve definir um ponto de extremidade do cliente no arquivo de configuração para SvcUtil. exe (svcutil. exe. config) que usa o contrato de `IMetadataExchange` e que tem o mesmo nome que o esquema de Uniform Resource Identifier (URI) do endereço do ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="44bc1-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="44bc1-108">Ao executar svcutil. exe para obter metadados para um serviço que expõe dois contratos de serviço diferentes que cada um contém uma operação de mesmo nome, svcutil. exe exibe um erro dizendo "não é possível obter metadados de...". Por exemplo, se você tiver um serviço que expõe um contrato de serviço chamado `ICarService` que tem uma operação `Get(Car c)` e o mesmo serviço expõe um contrato de serviço chamado `IBookService` que tem uma operação `Get(Book b)`.</span><span class="sxs-lookup"><span data-stu-id="44bc1-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="44bc1-109">Para contornar esse problema, adote uma das seguintes medidas:</span><span class="sxs-lookup"><span data-stu-id="44bc1-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="44bc1-110">Renomeie uma das operações.</span><span class="sxs-lookup"><span data-stu-id="44bc1-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="44bc1-111">Defina o <xref:System.ServiceModel.OperationContractAttribute.Name%2A> para um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="44bc1-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="44bc1-112">Defina um dos namespaces de operações para um namespace diferente usando a propriedade <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="44bc1-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="44bc1-113">Para baixar metadados usando svcutil. exe</span><span class="sxs-lookup"><span data-stu-id="44bc1-113">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="44bc1-114">Localize a ferramenta svcutil. exe no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="44bc1-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="44bc1-115">C:\Arquivos de Programas\microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="44bc1-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="44bc1-116">No prompt de comando, inicie a ferramenta usando o formato a seguir.</span><span class="sxs-lookup"><span data-stu-id="44bc1-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="44bc1-117">Você deve especificar a opção `/t:metadata` para baixar metadados.</span><span class="sxs-lookup"><span data-stu-id="44bc1-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="44bc1-118">Caso contrário, o código do cliente e a configuração serão gerados.</span><span class="sxs-lookup"><span data-stu-id="44bc1-118">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="44bc1-119">O argumento <`url`> especifica a URL para um ponto de extremidade de serviço que fornece metadados ou para um documento de metadados hospedado online.</span><span class="sxs-lookup"><span data-stu-id="44bc1-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="44bc1-120">O argumento <`epr`> especifica o caminho para um arquivo XML que contém um `EndpointAddress` WS-Addressing para um ponto de extremidade de serviço que oferece suporte a WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="44bc1-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="44bc1-121">Para obter mais opções sobre como usar essa ferramenta para download de metadados, consulte [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="44bc1-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44bc1-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44bc1-122">Example</span></span>  
 <span data-ttu-id="44bc1-123">O comando a seguir baixa os documentos de metadados de um serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="44bc1-123">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="44bc1-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="44bc1-124">See also</span></span>

- [<span data-ttu-id="44bc1-125">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="44bc1-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
