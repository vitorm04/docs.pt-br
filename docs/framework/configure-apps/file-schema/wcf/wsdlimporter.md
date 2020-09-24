---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 82704aa40b508f1b1e2237c9768a7b7599c5c87e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158585"
---
# \<wsdlImporter>

<span data-ttu-id="fb83b-101">Especifica todos os importadores WSDL que importa metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="fb83b-101">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="fb83b-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="fb83b-102">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb83b-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fb83b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="fb83b-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fb83b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb83b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb83b-105">Attributes</span></span>  
  
|<span data-ttu-id="fb83b-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="fb83b-106">Attribute</span></span>|<span data-ttu-id="fb83b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb83b-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="fb83b-108">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="fb83b-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb83b-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fb83b-109">Child Elements</span></span>  

 <span data-ttu-id="fb83b-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fb83b-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb83b-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fb83b-111">Parent Elements</span></span>  
  
|<span data-ttu-id="fb83b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb83b-112">Element</span></span>|<span data-ttu-id="fb83b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb83b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="fb83b-114">Especifica todos os importadores WSDL que importa metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="fb83b-114">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb83b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb83b-115">Remarks</span></span>  

 <span data-ttu-id="fb83b-116">Um importador WSDL é usado para importar metadados, bem como converter essas informações em várias classes que representam informações de contrato e de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fb83b-116">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="fb83b-117">Ele pode importar seletivamente informações de contrato e de ponto de extremidade e propriedades que expõem quaisquer erros de importação e aceitam informações de tipo relevantes para o processo de importação e conversão.</span><span class="sxs-lookup"><span data-stu-id="fb83b-117">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="fb83b-118">Ele também dá suporte à importação de informações de associação e propriedades que fornecem acesso a documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="fb83b-118">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb83b-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb83b-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="fb83b-120">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="fb83b-120">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="fb83b-121">Clientes</span><span class="sxs-lookup"><span data-stu-id="fb83b-121">Clients</span></span>](../../../wcf/feature-details/clients.md)
