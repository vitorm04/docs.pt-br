---
title: Elemento <Uri> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 80d71da5ca680872e4948fa8ff135fbbdf08cffe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663972"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="07f8f-102">\<Elemento de > URI (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="07f8f-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="07f8f-103">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="07f8f-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="07f8f-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="07f8f-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="07f8f-105">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="07f8f-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="07f8f-106">\<uri></span><span class="sxs-lookup"><span data-stu-id="07f8f-106">\<uri></span></span>](uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="07f8f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07f8f-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07f8f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="07f8f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="07f8f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="07f8f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07f8f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="07f8f-110">Attributes</span></span>  
 <span data-ttu-id="07f8f-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="07f8f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="07f8f-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="07f8f-112">Child Elements</span></span>  
  
|<span data-ttu-id="07f8f-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="07f8f-113">**Element**</span></span>|<span data-ttu-id="07f8f-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="07f8f-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="07f8f-115">idn</span><span class="sxs-lookup"><span data-stu-id="07f8f-115">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="07f8f-116">Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.</span><span class="sxs-lookup"><span data-stu-id="07f8f-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="07f8f-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="07f8f-117">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="07f8f-118">Especifica se a <xref:System.Uri> análise do IRI (identificador de recurso internacional) é aplicada e se as regras de análise de IRI devem ser aplicadas.</span><span class="sxs-lookup"><span data-stu-id="07f8f-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="07f8f-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="07f8f-119">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="07f8f-120">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="07f8f-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07f8f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="07f8f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="07f8f-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="07f8f-122">**Element**</span></span>|<span data-ttu-id="07f8f-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="07f8f-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="07f8f-124">configuração</span><span class="sxs-lookup"><span data-stu-id="07f8f-124">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="07f8f-125">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="07f8f-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07f8f-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="07f8f-126">Remarks</span></span>  
 <span data-ttu-id="07f8f-127">O `uri` elemento contém configurações para membros <xref:System.Uri> da classe <xref:System.Net> usada por classes no namespace.</span><span class="sxs-lookup"><span data-stu-id="07f8f-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="07f8f-128">As configurações configuram o suporte para IRI e IDN.</span><span class="sxs-lookup"><span data-stu-id="07f8f-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07f8f-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07f8f-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="07f8f-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="07f8f-130">Description</span></span>  
 <span data-ttu-id="07f8f-131">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="07f8f-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="07f8f-132">O exemplo também limpa todas as configurações de esquema e, em seguida, adiciona suporte para não escape de delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="07f8f-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="07f8f-133">Código</span><span class="sxs-lookup"><span data-stu-id="07f8f-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07f8f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07f8f-134">See also</span></span>

- [<span data-ttu-id="07f8f-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="07f8f-135">Network Settings Schema</span></span>](index.md)
