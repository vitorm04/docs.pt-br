---
title: <Uri> (Configurações de Uri)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 1f3573babd2e363a78f0ad454f0ba36c87ba6390
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212135"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="1d1b5-102">\<URI > (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="1d1b5-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="1d1b5-103">Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="1d1b5-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="1d1b5-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="1d1b5-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="1d1b5-105">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="1d1b5-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="1d1b5-106">\<uri></span><span class="sxs-lookup"><span data-stu-id="1d1b5-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="1d1b5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d1b5-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d1b5-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1d1b5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1d1b5-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d1b5-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1d1b5-110">Attributes</span></span>  
 <span data-ttu-id="1d1b5-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d1b5-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1d1b5-112">Child Elements</span></span>  
  
|**<span data-ttu-id="1d1b5-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d1b5-113">Element</span></span>**|**<span data-ttu-id="1d1b5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d1b5-114">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="1d1b5-115">idn</span><span class="sxs-lookup"><span data-stu-id="1d1b5-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="1d1b5-116">Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="1d1b5-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="1d1b5-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="1d1b5-118">Especifica se a análise de identificador de recursos internacionais (IRI) é aplicado a <xref:System.Uri> e se as regras de análise do IRI deve ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="1d1b5-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="1d1b5-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="1d1b5-120">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d1b5-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1d1b5-121">Parent Elements</span></span>  
  
|**<span data-ttu-id="1d1b5-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d1b5-122">Element</span></span>**|**<span data-ttu-id="1d1b5-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d1b5-123">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="1d1b5-124">configuração</span><span class="sxs-lookup"><span data-stu-id="1d1b5-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="1d1b5-125">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d1b5-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d1b5-126">Remarks</span></span>  
 <span data-ttu-id="1d1b5-127">O `uri` elemento contém configurações para os membros a <xref:System.Uri> usada pelas classes de classe a <xref:System.Net> namespace.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="1d1b5-128">As configurações de configuram o suporte a IRI e IDN.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d1b5-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d1b5-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1d1b5-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d1b5-130">Description</span></span>  
 <span data-ttu-id="1d1b5-131">O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe para dar suporte à análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="1d1b5-132">O exemplo também limpa todas as configurações de esquema e, em seguida, adiciona suporte para não escapar delimitadores de caminho codificado por percentual para o esquema de http.</span><span class="sxs-lookup"><span data-stu-id="1d1b5-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1d1b5-133">Código</span><span class="sxs-lookup"><span data-stu-id="1d1b5-133">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d1b5-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d1b5-134">See also</span></span>

- [<span data-ttu-id="1d1b5-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="1d1b5-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
