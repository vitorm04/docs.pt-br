---
title: Elemento <remove> para schemeSettings (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089157"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="8192d-102">\<remover > elemento para schemeSettings (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="8192d-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="8192d-103">Remove uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="8192d-103">Removes a scheme setting for a scheme name.</span></span>  

<span data-ttu-id="8192d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8192d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8192d-105">&nbsp;&nbsp;[**uri\<** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8192d-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="8192d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8192d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="8192d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**remover >**</span><span class="sxs-lookup"><span data-stu-id="8192d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8192d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8192d-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8192d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8192d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8192d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8192d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8192d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="8192d-111">Attributes</span></span>  
  
|<span data-ttu-id="8192d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="8192d-112">Attribute</span></span>|<span data-ttu-id="8192d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8192d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8192d-114">name</span><span class="sxs-lookup"><span data-stu-id="8192d-114">name</span></span>|<span data-ttu-id="8192d-115">O nome do esquema ao qual essa configuração se aplica.</span><span class="sxs-lookup"><span data-stu-id="8192d-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="8192d-116">Os únicos valores com suporte são Name = "http" e Name = "https".</span><span class="sxs-lookup"><span data-stu-id="8192d-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8192d-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8192d-117">Child Elements</span></span>  
 <span data-ttu-id="8192d-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8192d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8192d-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8192d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8192d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="8192d-120">Element</span></span>|<span data-ttu-id="8192d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8192d-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8192d-122">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="8192d-122">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="8192d-123">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="8192d-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8192d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="8192d-124">Remarks</span></span>  
 <span data-ttu-id="8192d-125">Por padrão, a classe <xref:System.Uri?displayProperty=nameWithType> não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="8192d-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="8192d-126">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8192d-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8192d-127">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="8192d-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="8192d-128">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> classe primeiro cancela o escape dos delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="8192d-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="8192d-129">O resultado da passagem da URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> Construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="8192d-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8192d-130">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="8192d-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8192d-131">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="8192d-131">Configuration Files</span></span>  
 <span data-ttu-id="8192d-132">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8192d-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8192d-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8192d-133">Example</span></span>  
 <span data-ttu-id="8192d-134">O exemplo a seguir mostra uma configuração usada pela classe <xref:System.Uri> que remove as configurações de esquema para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="8192d-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8192d-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8192d-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="8192d-136">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="8192d-136">Network Settings Schema</span></span>](index.md)
