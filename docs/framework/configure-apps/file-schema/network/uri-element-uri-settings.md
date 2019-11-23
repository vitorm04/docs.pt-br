---
title: Elemento <uri> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697435"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="da4ae-102">Elemento de > URI de \<(configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="da4ae-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="da4ae-103">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="da4ae-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[<span data-ttu-id="da4ae-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="da4ae-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="da4ae-105">URI de **\<** de &nbsp;de &nbsp;></span><span class="sxs-lookup"><span data-stu-id="da4ae-105">&nbsp;&nbsp;**\<uri>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da4ae-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da4ae-106">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da4ae-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="da4ae-107">Attributes and Elements</span></span>  
 <span data-ttu-id="da4ae-108">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="da4ae-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da4ae-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="da4ae-109">Attributes</span></span>  
 <span data-ttu-id="da4ae-110">None.</span><span class="sxs-lookup"><span data-stu-id="da4ae-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da4ae-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="da4ae-111">Child Elements</span></span>  
  
|<span data-ttu-id="da4ae-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="da4ae-112">**Element**</span></span>|<span data-ttu-id="da4ae-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="da4ae-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="da4ae-114">idn</span><span class="sxs-lookup"><span data-stu-id="da4ae-114">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="da4ae-115">Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.</span><span class="sxs-lookup"><span data-stu-id="da4ae-115">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="da4ae-116">iriParsing</span><span class="sxs-lookup"><span data-stu-id="da4ae-116">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="da4ae-117">Especifica se a análise do IRI (identificador de recurso internacional) é aplicada ao <xref:System.Uri> e se as regras de análise do IRI devem ser aplicadas.</span><span class="sxs-lookup"><span data-stu-id="da4ae-117">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="da4ae-118">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="da4ae-118">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="da4ae-119">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="da4ae-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da4ae-120">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="da4ae-120">Parent Elements</span></span>  
  
|<span data-ttu-id="da4ae-121">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="da4ae-121">**Element**</span></span>|<span data-ttu-id="da4ae-122">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="da4ae-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="da4ae-123">configuração</span><span class="sxs-lookup"><span data-stu-id="da4ae-123">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="da4ae-124">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="da4ae-124">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da4ae-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="da4ae-125">Remarks</span></span>  
 <span data-ttu-id="da4ae-126">O elemento `uri` contém configurações para membros da classe <xref:System.Uri> usada por classes no namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="da4ae-126">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="da4ae-127">As configurações configuram o suporte para IRI e IDN.</span><span class="sxs-lookup"><span data-stu-id="da4ae-127">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da4ae-128">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="da4ae-128">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="da4ae-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="da4ae-129">Description</span></span>  
 <span data-ttu-id="da4ae-130">O exemplo a seguir mostra uma configuração usada pela classe <xref:System.Uri> para dar suporte a análise IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="da4ae-130">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="da4ae-131">O exemplo também limpa todas as configurações de esquema e, em seguida, adiciona suporte para não escape de delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="da4ae-131">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="da4ae-132">Código</span><span class="sxs-lookup"><span data-stu-id="da4ae-132">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da4ae-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da4ae-133">See also</span></span>

- [<span data-ttu-id="da4ae-134">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="da4ae-134">Network Settings Schema</span></span>](index.md)
