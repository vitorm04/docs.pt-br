---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: aad0bbde964644448fbafc6c628c00c9faaad497
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204756"
---
# \<metadata>

<span data-ttu-id="15dbd-101">Especifica como os metadados de serviço podem ser processados.</span><span class="sxs-lookup"><span data-stu-id="15dbd-101">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="15dbd-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15dbd-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15dbd-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="15dbd-103">Attributes and Elements</span></span>  

 <span data-ttu-id="15dbd-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="15dbd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15dbd-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="15dbd-105">Attributes</span></span>  

 <span data-ttu-id="15dbd-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="15dbd-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="15dbd-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="15dbd-107">Child Elements</span></span>  
  
|<span data-ttu-id="15dbd-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="15dbd-108">Element</span></span>|<span data-ttu-id="15dbd-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="15dbd-109">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="15dbd-110">Especifica todos os importadores de política que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="15dbd-110">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="15dbd-111">Um importador de política é usado para pesquisar declarações de política personalizadas sobre recursos de associação, bem como anexar um elemento de ligação personalizado que implementa os recursos exigidos pela declaração.</span><span class="sxs-lookup"><span data-stu-id="15dbd-111">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="15dbd-112">Especifica todos os importadores WSDL que importam metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="15dbd-112">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="15dbd-113">Um importador WSDL é usado para importar metadados, bem como converter essas informações em várias classes que representam informações de contrato e de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="15dbd-113">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="15dbd-114">Ele pode importar seletivamente informações de contrato e de ponto de extremidade e propriedades que expõem quaisquer erros de importação e aceitam informações de tipo relevantes para o processo de importação e conversão.</span><span class="sxs-lookup"><span data-stu-id="15dbd-114">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="15dbd-115">Ele também dá suporte à importação de informações de associação e propriedades que fornecem acesso a documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="15dbd-115">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15dbd-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="15dbd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="15dbd-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="15dbd-117">Element</span></span>|<span data-ttu-id="15dbd-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="15dbd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="15dbd-119">A seção cliente define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="15dbd-119">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15dbd-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="15dbd-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="15dbd-121">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="15dbd-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="15dbd-122">Clientes</span><span class="sxs-lookup"><span data-stu-id="15dbd-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
