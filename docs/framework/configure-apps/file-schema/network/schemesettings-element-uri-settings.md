---
title: Elemento <schemeSettings> (configurações de Uri)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 06cb07b1620a603f0c0cf67a9236be143c2ec4a2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260181"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="f5115-102">\<schemeSettings > (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="f5115-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="f5115-103">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="f5115-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="f5115-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f5115-104">\<configuration></span></span>  
<span data-ttu-id="f5115-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="f5115-105">\<uri></span></span>  
<span data-ttu-id="f5115-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="f5115-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5115-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5115-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5115-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f5115-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f5115-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f5115-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5115-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f5115-110">Attributes</span></span>  
 <span data-ttu-id="f5115-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f5115-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5115-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f5115-112">Child Elements</span></span>  
  
|<span data-ttu-id="f5115-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="f5115-113">**Element**</span></span>|<span data-ttu-id="f5115-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f5115-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f5115-115">add</span><span class="sxs-lookup"><span data-stu-id="f5115-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="f5115-116">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="f5115-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="f5115-117">clear</span><span class="sxs-lookup"><span data-stu-id="f5115-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="f5115-118">Limpa todas as configurações existentes do esquema.</span><span class="sxs-lookup"><span data-stu-id="f5115-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="f5115-119">remove</span><span class="sxs-lookup"><span data-stu-id="f5115-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="f5115-120">Remove uma definição de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="f5115-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5115-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f5115-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f5115-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="f5115-122">**Element**</span></span>|<span data-ttu-id="f5115-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f5115-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f5115-124">uri</span><span class="sxs-lookup"><span data-stu-id="f5115-124">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="f5115-125">Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="f5115-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5115-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5115-126">Remarks</span></span>  
 <span data-ttu-id="f5115-127">Por padrão, o <xref:System.Uri?displayProperty=nameWithType> por cento un-escapes de classe codificado delimitadores de caminho antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="f5115-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="f5115-128">Isso era implementado como um mecanismo de segurança contra ataques, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f5115-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f5115-129">Se esse URI é passado para baixo para módulos de manipulação não % caracteres codificados corretamente, isso poderá resultar no comando a seguir, que está sendo executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="f5115-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="f5115-130">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> delimitadores de caminho primeiro cancelar escapes de classe e, em seguida, aplica-se a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="f5115-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="f5115-131">O resultado de passar a URL mal-intencionado acima para <xref:System.Uri?displayProperty=nameWithType> classe resultados construtor no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="f5115-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f5115-132">Esse comportamento padrão pode ser modificado para não cancelar escape porcentagem codificado delimitadores de caminho usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="f5115-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f5115-133">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="f5115-133">Configuration Files</span></span>  
 <span data-ttu-id="f5115-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f5115-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5115-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5115-135">Example</span></span>  
 <span data-ttu-id="f5115-136">O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe para dar suporte a escape não delimitadores de caminho codificado por percentual para o esquema de http.</span><span class="sxs-lookup"><span data-stu-id="f5115-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="f5115-137">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="f5115-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="f5115-138">Namespace</span><span class="sxs-lookup"><span data-stu-id="f5115-138">Namespace</span></span>|<span data-ttu-id="f5115-139">Sistema</span><span class="sxs-lookup"><span data-stu-id="f5115-139">System</span></span>|  
|<span data-ttu-id="f5115-140">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="f5115-140">Schema Name</span></span>||  
|<span data-ttu-id="f5115-141">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="f5115-141">Validation File</span></span>||  
|<span data-ttu-id="f5115-142">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="f5115-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="f5115-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5115-143">See also</span></span>
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="f5115-144">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="f5115-144">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
