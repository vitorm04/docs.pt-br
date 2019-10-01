---
title: Elemento <add> para schemeSettings (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: efd52557ea8b617a39e685ff8ad69bab01322a7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699601"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="2118e-102">\<add > elemento para schemeSettings (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="2118e-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="2118e-103">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="2118e-103">Adds a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="2118e-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2118e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2118e-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2118e-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="2118e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2118e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="2118e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="2118e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2118e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2118e-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2118e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2118e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2118e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="2118e-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2118e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2118e-111">Attributes</span></span>  
  
|<span data-ttu-id="2118e-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="2118e-112">Attribute</span></span>|<span data-ttu-id="2118e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2118e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2118e-114">name</span><span class="sxs-lookup"><span data-stu-id="2118e-114">name</span></span>|<span data-ttu-id="2118e-115">O nome do esquema ao qual essa configuração se aplica.</span><span class="sxs-lookup"><span data-stu-id="2118e-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="2118e-116">Os únicos valores com suporte são Name = "http" e Name = "https".</span><span class="sxs-lookup"><span data-stu-id="2118e-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="2118e-117">{Nome do atributo} Attribute</span><span class="sxs-lookup"><span data-stu-id="2118e-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="2118e-118">Valor</span><span class="sxs-lookup"><span data-stu-id="2118e-118">Value</span></span>|<span data-ttu-id="2118e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2118e-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2118e-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="2118e-120">genericUriParserOptions</span></span>|<span data-ttu-id="2118e-121">As opções do analisador para este esquema.</span><span class="sxs-lookup"><span data-stu-id="2118e-121">The parser options for this scheme.</span></span> <span data-ttu-id="2118e-122">O único valor com suporte é genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="2118e-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2118e-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2118e-123">Child Elements</span></span>  
 <span data-ttu-id="2118e-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2118e-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2118e-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2118e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2118e-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="2118e-126">Element</span></span>|<span data-ttu-id="2118e-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="2118e-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2118e-128">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="2118e-128">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="2118e-129">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="2118e-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2118e-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="2118e-130">Remarks</span></span>  
 <span data-ttu-id="2118e-131">Por padrão, a classe <xref:System.Uri?displayProperty=nameWithType> não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="2118e-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="2118e-132">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2118e-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="2118e-133">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="2118e-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="2118e-134">Por esse motivo, a classe <xref:System.Uri?displayProperty=nameWithType> primeiro cancela o escape dos delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="2118e-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="2118e-135">O resultado da passagem da URL mal-intencionada acima para o construtor da classe <xref:System.Uri?displayProperty=nameWithType> resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="2118e-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="2118e-136">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="2118e-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2118e-137">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="2118e-137">Configuration Files</span></span>  
 <span data-ttu-id="2118e-138">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2118e-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2118e-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2118e-139">Example</span></span>  
 <span data-ttu-id="2118e-140">O exemplo a seguir mostra uma configuração usada pela classe <xref:System.Uri> para dar suporte a não escapar delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="2118e-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2118e-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2118e-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="2118e-142">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2118e-142">Network Settings Schema</span></span>](index.md)
