---
title: Como usar o Svcutil.exe para baixar documentos de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 102b605b0b985d433092482cf55b0994c33d58ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="aae87-102">Como usar o Svcutil.exe para baixar documentos de metadados</span><span class="sxs-lookup"><span data-stu-id="aae87-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="aae87-103">Você pode usar o Svcutil.exe para baixar os metadados da execução de serviços e para salvar os metadados em arquivos locais.</span><span class="sxs-lookup"><span data-stu-id="aae87-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="aae87-104">Para esquemas de URL HTTP e HTTPS, o Svcutil.exe tenta recuperar metadados de WS-MetadataExchange e [XML Web Service Discovery](http://go.microsoft.com/fwlink/?LinkId=94950).</span><span class="sxs-lookup"><span data-stu-id="aae87-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](http://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="aae87-105">Para todos os outros esquemas de URL, Svcutil.exe usa apenas o WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="aae87-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="aae87-106">Por padrão, o Svcutil.exe usa as associações definidas no <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe.</span><span class="sxs-lookup"><span data-stu-id="aae87-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="aae87-107">Para configurar a associação usada para WS-MetadataExchange, você deve definir um ponto de extremidade do cliente no arquivo de configuração para Svcutil.exe (svcutil.exe.config) que usa o `IMetadataExchange` contrato e que tem o mesmo nome como o identificador de URI (Uniform Resource) esquema de endereço de ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="aae87-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="aae87-108">Ao executar o Svcutil.exe para obter metadados para um serviço que expõe dois serviços diferentes contratos que contêm uma operação de mesmo nome, Svcutil.exe exibe um erro dizendo "Não é possível obter metadados de..." Por exemplo, se você tiver um serviço que expõe um contrato de serviço chamado ICarService que tem uma operação obter (Car c) e o mesmo serviço expõe um contrato de serviço chamado IBookService que tem uma operação Get (catálogo b).</span><span class="sxs-lookup"><span data-stu-id="aae87-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called ICarService that has an operation Get(Car c) and the same service exposes a service contract called IBookService that has an operation Get(Book b).</span></span> <span data-ttu-id="aae87-109">Para contornar esse problema, siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="aae87-109">To work around this issue, do one of the following:</span></span>  
>   
>  -   <span data-ttu-id="aae87-110">Renomear uma das operações</span><span class="sxs-lookup"><span data-stu-id="aae87-110">Rename one of the operations</span></span>  
> -   <span data-ttu-id="aae87-111">Definir o <xref:System.ServiceModel.OperationContractAttribute.Name%2A> para um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="aae87-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>  
> -   <span data-ttu-id="aae87-112">Defina um dos namespaces as operações em um namespace diferente usando o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="aae87-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
### <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="aae87-113">Para baixar os metadados usando Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="aae87-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="aae87-114">Localize a ferramenta Svcutil.exe no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="aae87-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="aae87-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="aae87-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="aae87-116">No prompt de comando, inicie a ferramenta usando o formato a seguir.</span><span class="sxs-lookup"><span data-stu-id="aae87-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="aae87-117">Você deve especificar o `/t:metadata` opção para fazer o download de metadados.</span><span class="sxs-lookup"><span data-stu-id="aae87-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="aae87-118">Caso contrário, a configuração e o código do cliente são gerados.</span><span class="sxs-lookup"><span data-stu-id="aae87-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="aae87-119">O <`url`> argumento especifica a URL para um ponto de extremidade de serviço que fornece metadados ou para um documento de metadados hospedada online.</span><span class="sxs-lookup"><span data-stu-id="aae87-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="aae87-120">O <`epr`> argumento especifica o caminho para um arquivo XML que contém o WS-Addressing `EndpointAddress` para um ponto de extremidade de serviço que dá suporte ao WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="aae87-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="aae87-121">Para obter mais opções sobre como usar essa ferramenta para download de metadados, consulte [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aae87-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aae87-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aae87-122">Example</span></span>  
 <span data-ttu-id="aae87-123">O comando a seguir faz o download de documentos de metadados de um serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="aae87-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="aae87-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aae87-124">See Also</span></span>  
 <span data-ttu-id="aae87-125">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)]</span><span class="sxs-lookup"><span data-stu-id="aae87-125">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span></span>
