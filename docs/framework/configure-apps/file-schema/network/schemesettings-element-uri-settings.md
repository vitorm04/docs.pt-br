---
title: Elemento <schemeSettings> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154641"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="e472d-102">\<schemeSettings> Element (Uri Settings) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="e472d-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="e472d-103">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="e472d-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[<span data-ttu-id="e472d-104">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="e472d-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e472d-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e472d-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="e472d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<esquemaConfigurações>**</span><span class="sxs-lookup"><span data-stu-id="e472d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e472d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e472d-107">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e472d-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e472d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e472d-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e472d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e472d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e472d-110">Attributes</span></span>  
 <span data-ttu-id="e472d-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e472d-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e472d-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e472d-112">Child Elements</span></span>  
  
|<span data-ttu-id="e472d-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e472d-113">**Element**</span></span>|<span data-ttu-id="e472d-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e472d-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e472d-115">adicionar</span><span class="sxs-lookup"><span data-stu-id="e472d-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e472d-116">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="e472d-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="e472d-117">Claro</span><span class="sxs-lookup"><span data-stu-id="e472d-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e472d-118">Limpa todas as configurações de esquema existentes.</span><span class="sxs-lookup"><span data-stu-id="e472d-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="e472d-119">remover</span><span class="sxs-lookup"><span data-stu-id="e472d-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e472d-120">Remove uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="e472d-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e472d-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e472d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e472d-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e472d-122">**Element**</span></span>|<span data-ttu-id="e472d-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e472d-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e472d-124">Uri</span><span class="sxs-lookup"><span data-stu-id="e472d-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="e472d-125">Contém configurações que especificam como o .NET Framework lida com endereços da Web expressos usando URIs (Uniform Resource Identifiers).</span><span class="sxs-lookup"><span data-stu-id="e472d-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e472d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e472d-126">Remarks</span></span>  
 <span data-ttu-id="e472d-127">Por padrão, <xref:System.Uri?displayProperty=nameWithType> a classe desescapa por cento delimitadores de caminho codificados antes de executar a compactação do caminho.</span><span class="sxs-lookup"><span data-stu-id="e472d-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="e472d-128">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e472d-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e472d-129">Se esse URI for repassado para módulos que não lidam com caracteres codificados por porcentagem corretamente, isso pode resultar na execução do seguinte comando pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="e472d-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="e472d-130">Por essa <xref:System.Uri?displayProperty=nameWithType> razão, a classe primeiro desescapa delimitadores do caminho e, em seguida, aplica compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="e472d-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="e472d-131">O resultado da passagem da <xref:System.Uri?displayProperty=nameWithType> URL maliciosa acima para o construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="e472d-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e472d-132">Esse comportamento padrão pode ser modificado para não delimitar delimitadores de caminho codificados por porcentagem de desfugação usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="e472d-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e472d-133">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="e472d-133">Configuration Files</span></span>  
 <span data-ttu-id="e472d-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e472d-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e472d-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e472d-135">Example</span></span>  
 <span data-ttu-id="e472d-136">O exemplo a seguir mostra <xref:System.Uri> uma configuração usada pela classe para suportar não escapar de limitadores de caminho codificados por cento para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="e472d-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="e472d-137">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="e472d-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="e472d-138">Namespace</span><span class="sxs-lookup"><span data-stu-id="e472d-138">Namespace</span></span>|<span data-ttu-id="e472d-139">Sistema</span><span class="sxs-lookup"><span data-stu-id="e472d-139">System</span></span>|  
|<span data-ttu-id="e472d-140">Nome do Esquema</span><span class="sxs-lookup"><span data-stu-id="e472d-140">Schema Name</span></span>||  
|<span data-ttu-id="e472d-141">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="e472d-141">Validation File</span></span>||  
|<span data-ttu-id="e472d-142">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="e472d-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="e472d-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="e472d-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="e472d-144">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e472d-144">Network Settings Schema</span></span>](index.md)
