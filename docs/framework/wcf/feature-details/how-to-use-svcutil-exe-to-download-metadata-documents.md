---
title: Como usar o Svcutil.exe para baixar documentos de metadados
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 75068608c2b44ab772175aba7af8d8123457fb7c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403553"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="abe6b-102">Como usar o Svcutil.exe para baixar documentos de metadados</span><span class="sxs-lookup"><span data-stu-id="abe6b-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="abe6b-103">Você pode usar Svcutil.exe para baixar os metadados de serviços em execução e salvar os metadados em arquivos locais.</span><span class="sxs-lookup"><span data-stu-id="abe6b-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="abe6b-104">Para esquemas de URL HTTP e HTTPS, Svcutil.exe tenta recuperar metadados usando WS-MetadataExchange e [XML Web Service Discovery](https://go.microsoft.com/fwlink/?LinkId=94950).</span><span class="sxs-lookup"><span data-stu-id="abe6b-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="abe6b-105">Para todos os outros esquemas de URL, Svcutil.exe usa apenas WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="abe6b-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="abe6b-106">Por padrão, Svcutil.exe usa as associações definidas a <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe.</span><span class="sxs-lookup"><span data-stu-id="abe6b-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="abe6b-107">Para configurar a associação usada para WS-MetadataExchange, você deve definir um ponto de extremidade do cliente no arquivo de configuração para Svcutil.exe (svcutil) que usa o `IMetadataExchange` contrato e que tem o mesmo nome como o identificador de URI (Uniform Resource) esquema do endereço do ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="abe6b-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="abe6b-108">Quando em execução Svcutil.exe ao obter metadados para um serviço que expõe dois serviços diferentes de contratos que contêm uma operação de mesmo nome, Svcutil.exe exibe um erro dizendo que "Não é possível obter metadados de..." Por exemplo, se você tiver um serviço que expõe um contrato de serviço chamado ICarService que tem uma operação obter (c de carro) e o mesmo serviço expõe um contrato de serviço chamado IBookService que tem uma operação Get (livro b).</span><span class="sxs-lookup"><span data-stu-id="abe6b-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called ICarService that has an operation Get(Car c) and the same service exposes a service contract called IBookService that has an operation Get(Book b).</span></span> <span data-ttu-id="abe6b-109">Para contornar esse problema, siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="abe6b-109">To work around this issue, do one of the following:</span></span>  
>   
>  -   <span data-ttu-id="abe6b-110">Renomear uma das operações</span><span class="sxs-lookup"><span data-stu-id="abe6b-110">Rename one of the operations</span></span>  
> -   <span data-ttu-id="abe6b-111">Defina o <xref:System.ServiceModel.OperationContractAttribute.Name%2A> para um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="abe6b-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>  
> -   <span data-ttu-id="abe6b-112">Defina um dos namespaces das operações em um namespace diferente usando o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="abe6b-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
### <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="abe6b-113">Para baixar os metadados usando Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="abe6b-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="abe6b-114">Localize a ferramenta Svcutil.exe no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="abe6b-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="abe6b-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="abe6b-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="abe6b-116">No prompt de comando, inicie a ferramenta usando o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="abe6b-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="abe6b-117">Você deve especificar o `/t:metadata` opção para baixar os metadados.</span><span class="sxs-lookup"><span data-stu-id="abe6b-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="abe6b-118">Caso contrário, a configuração e o código de cliente são gerados.</span><span class="sxs-lookup"><span data-stu-id="abe6b-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="abe6b-119">O <`url`> argumento especifica a URL para um ponto de extremidade de serviço que fornece metadados ou para um documento de metadados hospedado online.</span><span class="sxs-lookup"><span data-stu-id="abe6b-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="abe6b-120">O <`epr`> argumento especifica o caminho para um arquivo XML que contém um WS-Addressing `EndpointAddress` para um ponto de extremidade de serviço que dá suporte a WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="abe6b-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="abe6b-121">Para obter mais opções sobre como usar essa ferramenta para download de metadados, consulte [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="abe6b-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abe6b-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="abe6b-122">Example</span></span>  
 <span data-ttu-id="abe6b-123">O comando a seguir baixa documentos de metadados de um serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="abe6b-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="abe6b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abe6b-124">See Also</span></span>  
 [<span data-ttu-id="abe6b-125">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="abe6b-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
