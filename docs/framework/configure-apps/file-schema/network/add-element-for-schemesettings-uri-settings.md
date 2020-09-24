---
title: Elemento <add> para schemeSettings (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 55fcba41d4dabf8937ebaa11235e9309bcb57952
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149455"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="56f0a-102">Elemento \<add> para schemeSettings (Configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="56f0a-102">\<add> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="56f0a-103">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="56f0a-103">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="56f0a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="56f0a-104">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56f0a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="56f0a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="56f0a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="56f0a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56f0a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="56f0a-107">Attributes</span></span>  
  
|<span data-ttu-id="56f0a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="56f0a-108">Attribute</span></span>|<span data-ttu-id="56f0a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="56f0a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56f0a-110">name</span><span class="sxs-lookup"><span data-stu-id="56f0a-110">name</span></span>|<span data-ttu-id="56f0a-111">O nome do esquema ao qual essa configuração se aplica.</span><span class="sxs-lookup"><span data-stu-id="56f0a-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="56f0a-112">Os únicos valores com suporte são Name = "http" e Name = "https".</span><span class="sxs-lookup"><span data-stu-id="56f0a-112">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="56f0a-113">{Nome do atributo} Attribute</span><span class="sxs-lookup"><span data-stu-id="56f0a-113">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="56f0a-114">Valor</span><span class="sxs-lookup"><span data-stu-id="56f0a-114">Value</span></span>|<span data-ttu-id="56f0a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="56f0a-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56f0a-116">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="56f0a-116">genericUriParserOptions</span></span>|<span data-ttu-id="56f0a-117">As opções do analisador para este esquema.</span><span class="sxs-lookup"><span data-stu-id="56f0a-117">The parser options for this scheme.</span></span> <span data-ttu-id="56f0a-118">O único valor com suporte é genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="56f0a-118">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56f0a-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="56f0a-119">Child Elements</span></span>  

 <span data-ttu-id="56f0a-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="56f0a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56f0a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="56f0a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="56f0a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="56f0a-122">Element</span></span>|<span data-ttu-id="56f0a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="56f0a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56f0a-124">\<schemeSettings> Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="56f0a-124">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="56f0a-125">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="56f0a-125">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56f0a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="56f0a-126">Remarks</span></span>  

 <span data-ttu-id="56f0a-127">Por padrão, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="56f0a-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="56f0a-128">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="56f0a-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="56f0a-129">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="56f0a-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="56f0a-130">Por esse motivo, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa primeiro os delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="56f0a-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="56f0a-131">O resultado da passagem da URL mal-intencionada acima para o <xref:System.Uri?displayProperty=nameWithType> Construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="56f0a-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="56f0a-132">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="56f0a-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="56f0a-133">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="56f0a-133">Configuration Files</span></span>  

 <span data-ttu-id="56f0a-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="56f0a-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56f0a-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56f0a-135">Example</span></span>  

 <span data-ttu-id="56f0a-136">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a não escapar delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="56f0a-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56f0a-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="56f0a-137">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="56f0a-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="56f0a-138">Network Settings Schema</span></span>](index.md)
