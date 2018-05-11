---
title: '&lt;wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 33c2b0e4286ce746f745e4aebe10fd4bbd96810f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="4435c-102">&lt;wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="4435c-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="4435c-103">Especifica todos os importadores WSDL que importa os metadados de WSDL Web Services Description Language () 1.1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="4435c-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="4435c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4435c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4435c-105">\<client></span><span class="sxs-lookup"><span data-stu-id="4435c-105">\<client></span></span>  
<span data-ttu-id="4435c-106">\<metadados ></span><span class="sxs-lookup"><span data-stu-id="4435c-106">\<metadata></span></span>  
<span data-ttu-id="4435c-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="4435c-107">\<wsdlImporters></span></span>  
<span data-ttu-id="4435c-108">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="4435c-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4435c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4435c-109">Syntax</span></span>  
  
```xml  
<metadata>  
  <wsdlImporters>  
    <wsdlImporter type="string" />  
  </wsdlImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4435c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4435c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4435c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4435c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4435c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4435c-112">Attributes</span></span>  
  
|<span data-ttu-id="4435c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="4435c-113">Attribute</span></span>|<span data-ttu-id="4435c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4435c-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="4435c-115">O tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="4435c-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4435c-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4435c-116">Child Elements</span></span>  
 <span data-ttu-id="4435c-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4435c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4435c-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4435c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4435c-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="4435c-119">Element</span></span>|<span data-ttu-id="4435c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="4435c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4435c-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="4435c-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="4435c-122">Especifica todos os importadores WSDL que importa os metadados de WSDL Web Services Description Language () 1.1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="4435c-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4435c-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="4435c-123">Remarks</span></span>  
 <span data-ttu-id="4435c-124">O importador de WSDL é usado para importar metadados, bem como converter que informações em várias classes que representam o contrato e informações de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4435c-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="4435c-125">Seletivamente pode importar informações de contrato e o ponto de extremidade e propriedades que expõem os erros de importação e aceitam informações relevantes para o processo de importação e a conversão do tipo.</span><span class="sxs-lookup"><span data-stu-id="4435c-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="4435c-126">Ele também oferece suporte a importação de informações de associação e propriedades que fornecem acesso a todos os documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="4435c-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4435c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4435c-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="4435c-128">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="4435c-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="4435c-129">Clientes</span><span class="sxs-lookup"><span data-stu-id="4435c-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
