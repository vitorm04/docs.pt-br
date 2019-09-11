---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855233"
---
# <a name="metadata"></a><span data-ttu-id="1ceec-101">\<> de metadados</span><span class="sxs-lookup"><span data-stu-id="1ceec-101">\<metadata></span></span>
<span data-ttu-id="1ceec-102">Especifica como os metadados de serviço podem ser processados.</span><span class="sxs-lookup"><span data-stu-id="1ceec-102">Specifies how service metadata can be processed.</span></span>  
  
<span data-ttu-id="1ceec-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1ceec-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1ceec-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1ceec-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1ceec-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="1ceec-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="1ceec-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de metadados**</span><span class="sxs-lookup"><span data-stu-id="1ceec-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ceec-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ceec-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ceec-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1ceec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1ceec-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1ceec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ceec-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1ceec-110">Attributes</span></span>  
 <span data-ttu-id="1ceec-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1ceec-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1ceec-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1ceec-112">Child Elements</span></span>  
  
|<span data-ttu-id="1ceec-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ceec-113">Element</span></span>|<span data-ttu-id="1ceec-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ceec-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ceec-115">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="1ceec-115">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="1ceec-116">Especifica todos os importadores de política que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="1ceec-116">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="1ceec-117">Um importador de política é usado para pesquisar declarações de política personalizadas sobre recursos de associação, bem como anexar um elemento de ligação personalizado que implementa os recursos exigidos pela declaração.</span><span class="sxs-lookup"><span data-stu-id="1ceec-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="1ceec-118">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="1ceec-118">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="1ceec-119">Especifica todos os importadores WSDL que importam metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="1ceec-119">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="1ceec-120">Um importador WSDL é usado para importar metadados, bem como converter essas informações em várias classes que representam informações de contrato e de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1ceec-120">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="1ceec-121">Ele pode importar seletivamente informações de contrato e de ponto de extremidade e propriedades que expõem quaisquer erros de importação e aceitam informações de tipo relevantes para o processo de importação e conversão.</span><span class="sxs-lookup"><span data-stu-id="1ceec-121">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="1ceec-122">Ele também dá suporte à importação de informações de associação e propriedades que fornecem acesso a documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="1ceec-122">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ceec-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1ceec-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1ceec-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ceec-124">Element</span></span>|<span data-ttu-id="1ceec-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ceec-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ceec-126">\<client></span><span class="sxs-lookup"><span data-stu-id="1ceec-126">\<client></span></span>](client.md)|<span data-ttu-id="1ceec-127">A seção cliente define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="1ceec-127">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ceec-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ceec-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="1ceec-129">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="1ceec-129">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="1ceec-130">Clientes</span><span class="sxs-lookup"><span data-stu-id="1ceec-130">Clients</span></span>](../../../wcf/feature-details/clients.md)
