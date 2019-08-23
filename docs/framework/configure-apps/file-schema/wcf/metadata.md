---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 4555dc9c2e0b783de2fb57e47c9aada0d69462e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931314"
---
# <a name="metadata"></a><span data-ttu-id="f5573-101">\<> de metadados</span><span class="sxs-lookup"><span data-stu-id="f5573-101">\<metadata></span></span>
<span data-ttu-id="f5573-102">Especifica como os metadados de serviço podem ser processados.</span><span class="sxs-lookup"><span data-stu-id="f5573-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="f5573-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f5573-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f5573-104">\<client></span><span class="sxs-lookup"><span data-stu-id="f5573-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5573-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5573-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5573-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f5573-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f5573-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f5573-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5573-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="f5573-108">Attributes</span></span>  
 <span data-ttu-id="f5573-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f5573-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5573-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f5573-110">Child Elements</span></span>  
  
|<span data-ttu-id="f5573-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5573-111">Element</span></span>|<span data-ttu-id="f5573-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5573-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5573-113">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="f5573-113">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="f5573-114">Especifica todos os importadores de política que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="f5573-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="f5573-115">Um importador de política é usado para pesquisar declarações de política personalizadas sobre recursos de associação, bem como anexar um elemento de ligação personalizado que implementa os recursos exigidos pela declaração.</span><span class="sxs-lookup"><span data-stu-id="f5573-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="f5573-116">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="f5573-116">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="f5573-117">Especifica todos os importadores WSDL que importam metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="f5573-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="f5573-118">Um importador WSDL é usado para importar metadados, bem como converter essas informações em várias classes que representam informações de contrato e de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f5573-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="f5573-119">Ele pode importar seletivamente informações de contrato e de ponto de extremidade e propriedades que expõem quaisquer erros de importação e aceitam informações de tipo relevantes para o processo de importação e conversão.</span><span class="sxs-lookup"><span data-stu-id="f5573-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="f5573-120">Ele também dá suporte à importação de informações de associação e propriedades que fornecem acesso a documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="f5573-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5573-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f5573-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f5573-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5573-122">Element</span></span>|<span data-ttu-id="f5573-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5573-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5573-124">\<client></span><span class="sxs-lookup"><span data-stu-id="f5573-124">\<client></span></span>](client.md)|<span data-ttu-id="f5573-125">A seção cliente define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="f5573-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5573-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5573-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="f5573-127">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="f5573-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="f5573-128">Clientes</span><span class="sxs-lookup"><span data-stu-id="f5573-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
