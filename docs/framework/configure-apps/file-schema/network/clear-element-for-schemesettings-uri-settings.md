---
title: Elemento <clear> para schemeSettings (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 90035c1c9ccdb8ac888aec84e506ccde41748c9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087441"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="7362a-102">Elemento \<clear> para schemeSettings (Configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="7362a-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="7362a-103">Limpa todas as configurações de esquema existentes.</span><span class="sxs-lookup"><span data-stu-id="7362a-103">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="7362a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7362a-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7362a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7362a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7362a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7362a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7362a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="7362a-107">Attributes</span></span>  
 <span data-ttu-id="7362a-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7362a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7362a-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7362a-109">Child Elements</span></span>  
 <span data-ttu-id="7362a-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7362a-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7362a-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7362a-111">Parent Elements</span></span>  
  
|<span data-ttu-id="7362a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="7362a-112">Element</span></span>|<span data-ttu-id="7362a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7362a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7362a-114">\<schemeSettings>Elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="7362a-114">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="7362a-115">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="7362a-115">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7362a-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="7362a-116">Remarks</span></span>  
 <span data-ttu-id="7362a-117">Por padrão, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="7362a-117">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="7362a-118">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7362a-118">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="7362a-119">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="7362a-119">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="7362a-120">Por esse motivo, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa primeiro os delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="7362a-120">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="7362a-121">O resultado da passagem da URL mal-intencionada acima para o <xref:System.Uri?displayProperty=nameWithType> Construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="7362a-121">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="7362a-122">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="7362a-122">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7362a-123">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="7362a-123">Configuration Files</span></span>  
 <span data-ttu-id="7362a-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="7362a-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7362a-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7362a-125">Example</span></span>  
 <span data-ttu-id="7362a-126">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe que limpa todas as configurações de esquema e, em seguida, adiciona suporte para não escape de delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="7362a-126">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7362a-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7362a-127">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="7362a-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="7362a-128">Network Settings Schema</span></span>](index.md)
