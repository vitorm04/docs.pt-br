---
title: Elemento <clear> para schemeSettings (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 90035c1c9ccdb8ac888aec84e506ccde41748c9f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087441"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="9c423-102">\<limpar > elemento para schemeSettings (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="9c423-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="9c423-103">Limpa todas as configurações de esquema existentes.</span><span class="sxs-lookup"><span data-stu-id="9c423-103">Clears all existing scheme settings.</span></span>  

<span data-ttu-id="9c423-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c423-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9c423-105">&nbsp;&nbsp;[**uri\<** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9c423-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="9c423-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9c423-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="9c423-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**desmarque >**</span><span class="sxs-lookup"><span data-stu-id="9c423-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9c423-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c423-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c423-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c423-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9c423-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c423-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c423-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c423-111">Attributes</span></span>  
 <span data-ttu-id="9c423-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9c423-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c423-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c423-113">Child Elements</span></span>  
 <span data-ttu-id="9c423-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9c423-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c423-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c423-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9c423-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c423-116">Element</span></span>|<span data-ttu-id="9c423-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c423-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c423-118">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="9c423-118">[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="9c423-119">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="9c423-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c423-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c423-120">Remarks</span></span>  
 <span data-ttu-id="9c423-121">Por padrão, a classe <xref:System.Uri?displayProperty=nameWithType> não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="9c423-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="9c423-122">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9c423-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9c423-123">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="9c423-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="9c423-124">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> classe primeiro cancela o escape dos delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="9c423-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="9c423-125">O resultado da passagem da URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> Construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="9c423-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9c423-126">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="9c423-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9c423-127">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="9c423-127">Configuration Files</span></span>  
 <span data-ttu-id="9c423-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="9c423-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c423-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c423-129">Example</span></span>  
 <span data-ttu-id="9c423-130">O exemplo a seguir mostra uma configuração usada pela classe <xref:System.Uri> que limpa todas as configurações de esquema e, em seguida, adiciona suporte para não escape de delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="9c423-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c423-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c423-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="9c423-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="9c423-132">Network Settings Schema</span></span>](index.md)
