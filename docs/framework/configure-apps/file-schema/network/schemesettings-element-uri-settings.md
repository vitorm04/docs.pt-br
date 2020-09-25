---
title: Elemento <schemeSettings> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 5a146b854239fd516125e66e05312e27b90c73ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91187011"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="d9d3c-102">Elemento \<schemeSettings> (Configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="d9d3c-102">\<schemeSettings> Element (Uri Settings)</span></span>

<span data-ttu-id="d9d3c-103">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="d9d3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9d3c-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9d3c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9d3c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d9d3c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9d3c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9d3c-107">Attributes</span></span>  

 <span data-ttu-id="d9d3c-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d9d3c-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9d3c-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9d3c-109">Child Elements</span></span>  
  
|<span data-ttu-id="d9d3c-110">**Element**</span><span class="sxs-lookup"><span data-stu-id="d9d3c-110">**Element**</span></span>|<span data-ttu-id="d9d3c-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d9d3c-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d9d3c-112">add</span><span class="sxs-lookup"><span data-stu-id="d9d3c-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="d9d3c-113">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="d9d3c-114">clear</span><span class="sxs-lookup"><span data-stu-id="d9d3c-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="d9d3c-115">Limpa todas as configurações de esquema existentes.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="d9d3c-116">remove</span><span class="sxs-lookup"><span data-stu-id="d9d3c-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="d9d3c-117">Remove uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9d3c-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9d3c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d9d3c-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="d9d3c-119">**Element**</span></span>|<span data-ttu-id="d9d3c-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d9d3c-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d9d3c-121">uri</span><span class="sxs-lookup"><span data-stu-id="d9d3c-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="d9d3c-122">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="d9d3c-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9d3c-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9d3c-123">Remarks</span></span>  

 <span data-ttu-id="d9d3c-124">Por padrão, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="d9d3c-125">Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9d3c-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="d9d3c-126">Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="d9d3c-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="d9d3c-127">Por esse motivo, a <xref:System.Uri?displayProperty=nameWithType> classe não escapa primeiro os delimitadores de caminho e, em seguida, aplica a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="d9d3c-128">O resultado da passagem da URL mal-intencionada acima para o <xref:System.Uri?displayProperty=nameWithType> Construtor de classe resulta no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="d9d3c-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="d9d3c-129">Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d9d3c-130">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="d9d3c-130">Configuration Files</span></span>  

 <span data-ttu-id="d9d3c-131">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d9d3c-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9d3c-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9d3c-132">Example</span></span>  

 <span data-ttu-id="d9d3c-133">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a não escapar delimitadores de caminho codificados por porcentagem para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="d9d3c-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="d9d3c-134">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="d9d3c-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="d9d3c-135">Namespace</span><span class="sxs-lookup"><span data-stu-id="d9d3c-135">Namespace</span></span>|<span data-ttu-id="d9d3c-136">Sistema</span><span class="sxs-lookup"><span data-stu-id="d9d3c-136">System</span></span>|  
|<span data-ttu-id="d9d3c-137">Nome do Esquema</span><span class="sxs-lookup"><span data-stu-id="d9d3c-137">Schema Name</span></span>||  
|<span data-ttu-id="d9d3c-138">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="d9d3c-138">Validation File</span></span>||  
|<span data-ttu-id="d9d3c-139">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="d9d3c-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="d9d3c-140">Veja também</span><span class="sxs-lookup"><span data-stu-id="d9d3c-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="d9d3c-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="d9d3c-141">Network Settings Schema</span></span>](index.md)
