---
title: Elemento <add> para schemeSettings (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 027c7aaffea7950739f532309255d77afa031ada
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659548"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="e513b-102">\<Adicionar > elemento para schemeSettings (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="e513b-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="e513b-103">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="e513b-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="e513b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e513b-104">\<configuration></span></span>  
<span data-ttu-id="e513b-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="e513b-105">\<uri></span></span>  
<span data-ttu-id="e513b-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="e513b-106">\<schemeSettings></span></span>  
<span data-ttu-id="e513b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e513b-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e513b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e513b-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e513b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e513b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e513b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="e513b-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e513b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e513b-111">Attributes</span></span>  
  
|<span data-ttu-id="e513b-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="e513b-112">Attribute</span></span>|<span data-ttu-id="e513b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e513b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e513b-114">name</span><span class="sxs-lookup"><span data-stu-id="e513b-114">name</span></span>|<span data-ttu-id="e513b-115">O nome do esquema ao qual essa configuração se aplica.</span><span class="sxs-lookup"><span data-stu-id="e513b-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="e513b-116">Os únicos valores com suporte são Name = "http" e Name = "https".</span><span class="sxs-lookup"><span data-stu-id="e513b-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="e513b-117">{Nome do atributo} Attribute</span><span class="sxs-lookup"><span data-stu-id="e513b-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="e513b-118">Valor</span><span class="sxs-lookup"><span data-stu-id="e513b-118">Value</span></span>|<span data-ttu-id="e513b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e513b-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e513b-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="e513b-120">genericUriParserOptions</span></span>|<span data-ttu-id="e513b-121">As opções do analisador para este esquema.</span><span class="sxs-lookup"><span data-stu-id="e513b-121">The parser options for this scheme.</span></span> <span data-ttu-id="e513b-122">O único valor com suporte é genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="e513b-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e513b-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e513b-123">Child Elements</span></span>  
 <span data-ttu-id="e513b-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e513b-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e513b-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e513b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e513b-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e513b-126">Element</span></span>|<span data-ttu-id="e513b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e513b-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e513b-128">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="e513b-128">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="e513b-129">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="e513b-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e513b-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="e513b-130">Remarks</span></span>  
 <span data-ttu-id="e513b-131">Por padrão, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="e513b-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="e513b-132">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e513b-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e513b-133">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="e513b-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="e513b-134">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> a classe não escapa primeiro os delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="e513b-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="e513b-135">O resultado da passagem da URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> o construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="e513b-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e513b-136">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="e513b-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e513b-137">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="e513b-137">Configuration Files</span></span>  
 <span data-ttu-id="e513b-138">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e513b-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e513b-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e513b-139">Example</span></span>  
 <span data-ttu-id="e513b-140">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a não escapar delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="e513b-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e513b-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e513b-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="e513b-142">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e513b-142">Network Settings Schema</span></span>](index.md)
