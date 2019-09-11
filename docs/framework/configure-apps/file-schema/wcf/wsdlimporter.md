---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854763"
---
# <a name="wsdlimporter"></a><span data-ttu-id="3b751-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="3b751-101">\<wsdlImporter></span></span>
<span data-ttu-id="3b751-102">Especifica todos os importadores WSDL que importa metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="3b751-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="3b751-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b751-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3b751-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3b751-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3b751-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="3b751-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="3b751-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de metadados**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="3b751-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="3b751-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> wsdlImporters**](wsdlimporters.md)</span><span class="sxs-lookup"><span data-stu-id="3b751-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)</span></span>  
<span data-ttu-id="3b751-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> wsdlImporter**</span><span class="sxs-lookup"><span data-stu-id="3b751-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b751-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b751-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b751-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3b751-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3b751-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3b751-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b751-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3b751-112">Attributes</span></span>  
  
|<span data-ttu-id="3b751-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3b751-113">Attribute</span></span>|<span data-ttu-id="3b751-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b751-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="3b751-115">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="3b751-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b751-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3b751-116">Child Elements</span></span>  
 <span data-ttu-id="3b751-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3b751-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b751-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3b751-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3b751-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="3b751-119">Element</span></span>|<span data-ttu-id="3b751-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b751-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b751-121">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="3b751-121">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="3b751-122">Especifica todos os importadores WSDL que importa metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="3b751-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b751-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b751-123">Remarks</span></span>  
 <span data-ttu-id="3b751-124">Um importador WSDL é usado para importar metadados, bem como converter essas informações em várias classes que representam informações de contrato e de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3b751-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="3b751-125">Ele pode importar seletivamente informações de contrato e de ponto de extremidade e propriedades que expõem quaisquer erros de importação e aceitam informações de tipo relevantes para o processo de importação e conversão.</span><span class="sxs-lookup"><span data-stu-id="3b751-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="3b751-126">Ele também dá suporte à importação de informações de associação e propriedades que fornecem acesso a documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="3b751-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b751-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b751-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="3b751-128">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="3b751-128">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="3b751-129">Clientes</span><span class="sxs-lookup"><span data-stu-id="3b751-129">Clients</span></span>](../../../wcf/feature-details/clients.md)
