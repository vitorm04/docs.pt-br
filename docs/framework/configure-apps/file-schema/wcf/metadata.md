---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: c0c9848d073c799e1f97dd79b375848dfab71e99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191478"
---
# <a name="metadata"></a><span data-ttu-id="beddd-101">\<metadata></span><span class="sxs-lookup"><span data-stu-id="beddd-101">\<metadata></span></span>
<span data-ttu-id="beddd-102">Especifica como os metadados de serviço podem ser processados.</span><span class="sxs-lookup"><span data-stu-id="beddd-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="beddd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="beddd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="beddd-104">\<client></span><span class="sxs-lookup"><span data-stu-id="beddd-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beddd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="beddd-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="beddd-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="beddd-106">Attributes and Elements</span></span>  
 <span data-ttu-id="beddd-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="beddd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="beddd-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="beddd-108">Attributes</span></span>  
 <span data-ttu-id="beddd-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="beddd-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="beddd-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="beddd-110">Child Elements</span></span>  
  
|<span data-ttu-id="beddd-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="beddd-111">Element</span></span>|<span data-ttu-id="beddd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="beddd-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beddd-113">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="beddd-113">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="beddd-114">Especifica todos os importadores de políticas que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="beddd-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="beddd-115">Um importador de política é usado para pesquisar as declarações de política personalizadas sobre recursos de associação, bem como anexar a um elemento de associação personalizado que implementa os recursos que exige que a asserção.</span><span class="sxs-lookup"><span data-stu-id="beddd-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="beddd-116">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="beddd-116">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="beddd-117">Especifica todos os importadores WSDL que importam metadados de descrição linguagem WSDL (Web Services) 1.1 com anexos WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="beddd-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="beddd-118">Um importador WSDL é usado para importar metadados, bem como converter essa informações em várias classes que representam o contrato e informações de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="beddd-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="beddd-119">Ele seletivamente pode importar informações de contrato e o ponto de extremidade e propriedades que expõem os erros de importação e aceitar informações relevantes para o processo de importação e a conversão do tipo.</span><span class="sxs-lookup"><span data-stu-id="beddd-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="beddd-120">Ele também dá suporte a importação de informações de associação e propriedades que fornecem acesso a todos os documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="beddd-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="beddd-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="beddd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="beddd-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="beddd-122">Element</span></span>|<span data-ttu-id="beddd-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="beddd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beddd-124">\<client></span><span class="sxs-lookup"><span data-stu-id="beddd-124">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="beddd-125">A seção de cliente define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="beddd-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="beddd-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="beddd-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="beddd-127">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="beddd-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="beddd-128">Clientes</span><span class="sxs-lookup"><span data-stu-id="beddd-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
