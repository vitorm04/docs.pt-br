---
title: Elemento <remove> para schemeSettings (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089157"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="daa09-102">Elemento \<remove> para schemeSettings (Configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="daa09-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="daa09-103">Remove uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="daa09-103">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="daa09-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="daa09-104">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="daa09-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="daa09-105">Attributes and Elements</span></span>  
 <span data-ttu-id="daa09-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="daa09-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="daa09-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="daa09-107">Attributes</span></span>  
  
|<span data-ttu-id="daa09-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="daa09-108">Attribute</span></span>|<span data-ttu-id="daa09-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="daa09-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="daa09-110">name</span><span class="sxs-lookup"><span data-stu-id="daa09-110">name</span></span>|<span data-ttu-id="daa09-111">O nome do esquema ao qual essa configuração se aplica.</span><span class="sxs-lookup"><span data-stu-id="daa09-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="daa09-112">Os únicos valores com suporte são Name = "http" e Name = "https".</span><span class="sxs-lookup"><span data-stu-id="daa09-112">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="daa09-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="daa09-113">Child Elements</span></span>  
 <span data-ttu-id="daa09-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="daa09-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="daa09-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="daa09-115">Parent Elements</span></span>  
  
|<span data-ttu-id="daa09-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="daa09-116">Element</span></span>|<span data-ttu-id="daa09-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="daa09-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="daa09-118">\<schemeSettings>Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="daa09-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="daa09-119">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="daa09-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daa09-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="daa09-120">Remarks</span></span>  
 <span data-ttu-id="daa09-121">Por padrão, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="daa09-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="daa09-122">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="daa09-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="daa09-123">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="daa09-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="daa09-124">Por esse motivo, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa primeiro os delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="daa09-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="daa09-125">O resultado da passagem da URL mal-intencionada acima para o <xref:System.Uri?displayProperty=nameWithType> Construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="daa09-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="daa09-126">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="daa09-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="daa09-127">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="daa09-127">Configuration Files</span></span>  
 <span data-ttu-id="daa09-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="daa09-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="daa09-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="daa09-129">Example</span></span>  
 <span data-ttu-id="daa09-130">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe que remove as configurações de esquema para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="daa09-130">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="daa09-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="daa09-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="daa09-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="daa09-132">Network Settings Schema</span></span>](index.md)
