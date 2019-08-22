---
title: Elemento <schemeSettings> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 46012b15d41422fb3357e57438e320136809ef41
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664005"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="e2cd0-102">\<Elemento de > schemeSettings (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="e2cd0-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="e2cd0-103">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="e2cd0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e2cd0-104">\<configuration></span></span>  
<span data-ttu-id="e2cd0-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="e2cd0-105">\<uri></span></span>  
<span data-ttu-id="e2cd0-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="e2cd0-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2cd0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2cd0-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2cd0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e2cd0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2cd0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2cd0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e2cd0-110">Attributes</span></span>  
 <span data-ttu-id="e2cd0-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e2cd0-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2cd0-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e2cd0-112">Child Elements</span></span>  
  
|<span data-ttu-id="e2cd0-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e2cd0-113">**Element**</span></span>|<span data-ttu-id="e2cd0-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e2cd0-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e2cd0-115">add</span><span class="sxs-lookup"><span data-stu-id="e2cd0-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e2cd0-116">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="e2cd0-117">clear</span><span class="sxs-lookup"><span data-stu-id="e2cd0-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e2cd0-118">Limpa todas as configurações de esquema existentes.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="e2cd0-119">remove</span><span class="sxs-lookup"><span data-stu-id="e2cd0-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e2cd0-120">Remove uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2cd0-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e2cd0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e2cd0-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e2cd0-122">**Element**</span></span>|<span data-ttu-id="e2cd0-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e2cd0-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e2cd0-124">uri</span><span class="sxs-lookup"><span data-stu-id="e2cd0-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="e2cd0-125">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="e2cd0-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2cd0-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e2cd0-126">Remarks</span></span>  
 <span data-ttu-id="e2cd0-127">Por padrão, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="e2cd0-128">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e2cd0-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e2cd0-129">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="e2cd0-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="e2cd0-130">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> a classe não escapa primeiro os delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="e2cd0-131">O resultado da passagem da URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> o construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="e2cd0-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e2cd0-132">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e2cd0-133">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="e2cd0-133">Configuration Files</span></span>  
 <span data-ttu-id="e2cd0-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e2cd0-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2cd0-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2cd0-135">Example</span></span>  
 <span data-ttu-id="e2cd0-136">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a não escapar delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="e2cd0-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="e2cd0-137">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="e2cd0-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="e2cd0-138">Namespace</span><span class="sxs-lookup"><span data-stu-id="e2cd0-138">Namespace</span></span>|<span data-ttu-id="e2cd0-139">Sistema</span><span class="sxs-lookup"><span data-stu-id="e2cd0-139">System</span></span>|  
|<span data-ttu-id="e2cd0-140">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="e2cd0-140">Schema Name</span></span>||  
|<span data-ttu-id="e2cd0-141">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="e2cd0-141">Validation File</span></span>||  
|<span data-ttu-id="e2cd0-142">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="e2cd0-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="e2cd0-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2cd0-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="e2cd0-144">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e2cd0-144">Network Settings Schema</span></span>](index.md)
