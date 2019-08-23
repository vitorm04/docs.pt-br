---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 13c9400874f1e02fac3ce0c3010153ad7806288c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915181"
---
# <a name="wsdlimporter"></a><span data-ttu-id="b2c5f-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="b2c5f-101">\<wsdlImporter></span></span>
<span data-ttu-id="b2c5f-102">Especifica todos os importadores WSDL que importa metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="b2c5f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b2c5f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2c5f-104">\<client></span><span class="sxs-lookup"><span data-stu-id="b2c5f-104">\<client></span></span>  
<span data-ttu-id="b2c5f-105">\<> de metadados</span><span class="sxs-lookup"><span data-stu-id="b2c5f-105">\<metadata></span></span>  
<span data-ttu-id="b2c5f-106">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="b2c5f-106">\<wsdlImporters></span></span>  
<span data-ttu-id="b2c5f-107">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="b2c5f-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c5f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2c5f-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2c5f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b2c5f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b2c5f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2c5f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b2c5f-111">Attributes</span></span>  
  
|<span data-ttu-id="b2c5f-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="b2c5f-112">Attribute</span></span>|<span data-ttu-id="b2c5f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2c5f-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="b2c5f-114">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2c5f-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b2c5f-115">Child Elements</span></span>  
 <span data-ttu-id="b2c5f-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2c5f-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b2c5f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b2c5f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2c5f-118">Element</span></span>|<span data-ttu-id="b2c5f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2c5f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2c5f-120">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="b2c5f-120">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="b2c5f-121">Especifica todos os importadores WSDL que importa metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2c5f-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2c5f-122">Remarks</span></span>  
 <span data-ttu-id="b2c5f-123">Um importador WSDL é usado para importar metadados, bem como converter essas informações em várias classes que representam informações de contrato e de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="b2c5f-124">Ele pode importar seletivamente informações de contrato e de ponto de extremidade e propriedades que expõem quaisquer erros de importação e aceitam informações de tipo relevantes para o processo de importação e conversão.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="b2c5f-125">Ele também dá suporte à importação de informações de associação e propriedades que fornecem acesso a documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="b2c5f-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c5f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2c5f-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="b2c5f-127">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="b2c5f-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="b2c5f-128">Clientes</span><span class="sxs-lookup"><span data-stu-id="b2c5f-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
