---
title: Elemento <uri> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697435"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="ffc14-102">Elemento \<uri> (Configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="ffc14-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="ffc14-103">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="ffc14-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="ffc14-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffc14-104">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffc14-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ffc14-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ffc14-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ffc14-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffc14-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ffc14-107">Attributes</span></span>  
 <span data-ttu-id="ffc14-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ffc14-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ffc14-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ffc14-109">Child Elements</span></span>  
  
|<span data-ttu-id="ffc14-110">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ffc14-110">**Element**</span></span>|<span data-ttu-id="ffc14-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ffc14-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ffc14-112">IDN</span><span class="sxs-lookup"><span data-stu-id="ffc14-112">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="ffc14-113">Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.</span><span class="sxs-lookup"><span data-stu-id="ffc14-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="ffc14-114">iriParsing</span><span class="sxs-lookup"><span data-stu-id="ffc14-114">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="ffc14-115">Especifica se a análise do IRI (identificador de recurso internacional) é aplicada <xref:System.Uri> e se as regras de análise de IRI devem ser aplicadas.</span><span class="sxs-lookup"><span data-stu-id="ffc14-115">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="ffc14-116">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="ffc14-116">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="ffc14-117">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="ffc14-117">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ffc14-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ffc14-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ffc14-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ffc14-119">**Element**</span></span>|<span data-ttu-id="ffc14-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ffc14-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ffc14-121">configuração</span><span class="sxs-lookup"><span data-stu-id="ffc14-121">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="ffc14-122">Contém configurações para todos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="ffc14-122">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffc14-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffc14-123">Remarks</span></span>  
 <span data-ttu-id="ffc14-124">O `uri` elemento contém configurações para membros da <xref:System.Uri> classe usada por classes no <xref:System.Net> namespace.</span><span class="sxs-lookup"><span data-stu-id="ffc14-124">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="ffc14-125">As configurações configuram o suporte para IRI e IDN.</span><span class="sxs-lookup"><span data-stu-id="ffc14-125">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffc14-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ffc14-126">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ffc14-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffc14-127">Description</span></span>  
 <span data-ttu-id="ffc14-128">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="ffc14-128">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="ffc14-129">O exemplo também limpa todas as configurações de esquema e, em seguida, adiciona suporte para não escape de delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="ffc14-129">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ffc14-130">Código</span><span class="sxs-lookup"><span data-stu-id="ffc14-130">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ffc14-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="ffc14-131">See also</span></span>

- [<span data-ttu-id="ffc14-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="ffc14-132">Network Settings Schema</span></span>](index.md)
