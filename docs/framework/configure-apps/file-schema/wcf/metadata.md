---
title: '&lt;metadados&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06444f30ab06f04644a7a6c5ad596388ecceeaf1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmetadatagt"></a><span data-ttu-id="f5213-102">&lt;metadados&gt;</span><span class="sxs-lookup"><span data-stu-id="f5213-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="f5213-103">Especifica como os metadados de serviço podem ser processado.</span><span class="sxs-lookup"><span data-stu-id="f5213-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="f5213-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f5213-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f5213-105">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="f5213-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5213-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5213-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
                 <wsdlImporters>  
                      <wsdlImporter type="string" />  
                 </wsdlImporters>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5213-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f5213-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f5213-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f5213-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5213-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f5213-109">Attributes</span></span>  
 <span data-ttu-id="f5213-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f5213-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5213-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f5213-111">Child Elements</span></span>  
  
|<span data-ttu-id="f5213-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5213-112">Element</span></span>|<span data-ttu-id="f5213-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5213-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5213-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="f5213-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="f5213-115">Especifica todos os importadores de políticas que controlam a importação de declarações de políticas personalizadas sobre associações.</span><span class="sxs-lookup"><span data-stu-id="f5213-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="f5213-116">Um importador de política é usado para declarações de políticas personalizadas sobre associação de recursos de pesquisa, bem como anexar um elemento de associação personalizada que implementa os recursos que requer a asserção.</span><span class="sxs-lookup"><span data-stu-id="f5213-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="f5213-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="f5213-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="f5213-118">Especifica todos os importadores WSDL que importam metadados de WSDL Web Services Description Language () 1.1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="f5213-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="f5213-119">O importador de WSDL é usado para importar metadados, bem como converter que informações em várias classes que representam o contrato e informações de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f5213-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="f5213-120">Seletivamente pode importar informações de contrato e o ponto de extremidade e propriedades que expõem os erros de importação e aceitam informações relevantes para o processo de importação e a conversão do tipo.</span><span class="sxs-lookup"><span data-stu-id="f5213-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="f5213-121">Ele também oferece suporte a importação de informações de associação e propriedades que fornecem acesso a todos os documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="f5213-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5213-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f5213-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f5213-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5213-123">Element</span></span>|<span data-ttu-id="f5213-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5213-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5213-125">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="f5213-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="f5213-126">A seção de cliente define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="f5213-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5213-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5213-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="f5213-128">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="f5213-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="f5213-129">Clientes</span><span class="sxs-lookup"><span data-stu-id="f5213-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
