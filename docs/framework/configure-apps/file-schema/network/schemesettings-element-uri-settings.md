---
title: Elemento <schemeSettings> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154641"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="c21e4-102">Elemento \<schemeSettings> (Configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="c21e4-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="c21e4-103">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="c21e4-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="c21e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c21e4-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c21e4-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c21e4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c21e4-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c21e4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c21e4-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c21e4-107">Attributes</span></span>  
 <span data-ttu-id="c21e4-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c21e4-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c21e4-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c21e4-109">Child Elements</span></span>  
  
|<span data-ttu-id="c21e4-110">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c21e4-110">**Element**</span></span>|<span data-ttu-id="c21e4-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c21e4-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c21e4-112">adicionar</span><span class="sxs-lookup"><span data-stu-id="c21e4-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="c21e4-113">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="c21e4-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="c21e4-114">formatação</span><span class="sxs-lookup"><span data-stu-id="c21e4-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="c21e4-115">Limpa todas as configurações de esquema existentes.</span><span class="sxs-lookup"><span data-stu-id="c21e4-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="c21e4-116">remove</span><span class="sxs-lookup"><span data-stu-id="c21e4-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="c21e4-117">Remove uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="c21e4-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c21e4-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c21e4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c21e4-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c21e4-119">**Element**</span></span>|<span data-ttu-id="c21e4-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c21e4-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c21e4-121">URI</span><span class="sxs-lookup"><span data-stu-id="c21e4-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="c21e4-122">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="c21e4-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c21e4-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="c21e4-123">Remarks</span></span>  
 <span data-ttu-id="c21e4-124">Por padrão, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="c21e4-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="c21e4-125">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c21e4-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c21e4-126">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="c21e4-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="c21e4-127">Por esse motivo, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa primeiro os delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="c21e4-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="c21e4-128">O resultado da passagem da URL mal-intencionada acima para o <xref:System.Uri?displayProperty=nameWithType> Construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="c21e4-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c21e4-129">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="c21e4-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c21e4-130">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c21e4-130">Configuration Files</span></span>  
 <span data-ttu-id="c21e4-131">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c21e4-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c21e4-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c21e4-132">Example</span></span>  
 <span data-ttu-id="c21e4-133">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a não escapar delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="c21e4-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="c21e4-134">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="c21e4-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="c21e4-135">Namespace</span><span class="sxs-lookup"><span data-stu-id="c21e4-135">Namespace</span></span>|<span data-ttu-id="c21e4-136">Sistema</span><span class="sxs-lookup"><span data-stu-id="c21e4-136">System</span></span>|  
|<span data-ttu-id="c21e4-137">Nome do Esquema</span><span class="sxs-lookup"><span data-stu-id="c21e4-137">Schema Name</span></span>||  
|<span data-ttu-id="c21e4-138">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="c21e4-138">Validation File</span></span>||  
|<span data-ttu-id="c21e4-139">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="c21e4-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="c21e4-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="c21e4-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="c21e4-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="c21e4-141">Network Settings Schema</span></span>](index.md)
