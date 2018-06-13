---
title: '&lt;iriParsing&gt; (configurações de Uri) do elemento'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f05f7e35d69f789d3ebb371689aafbc84004b732
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743297"
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="60446-102">&lt;iriParsing&gt; (configurações de Uri) do elemento</span><span class="sxs-lookup"><span data-stu-id="60446-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="60446-103">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="60446-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="60446-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="60446-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="60446-105">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="60446-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="60446-106">\<URI > elemento (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="60446-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="60446-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="60446-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="60446-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60446-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60446-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60446-109">Attributes and Elements</span></span>  
 <span data-ttu-id="60446-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60446-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60446-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="60446-111">Attributes</span></span>  
  
|<span data-ttu-id="60446-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="60446-112">**Element**</span></span>|<span data-ttu-id="60446-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="60446-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="60446-114">Especifica se a análise de IRI está habilitada.</span><span class="sxs-lookup"><span data-stu-id="60446-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="60446-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="60446-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60446-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60446-116">Child Elements</span></span>  
 <span data-ttu-id="60446-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="60446-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60446-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60446-118">Parent Elements</span></span>  
  
|<span data-ttu-id="60446-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="60446-119">**Element**</span></span>|<span data-ttu-id="60446-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="60446-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="60446-121">URI</span><span class="sxs-lookup"><span data-stu-id="60446-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="60446-122">Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="60446-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60446-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="60446-123">Remarks</span></span>  
 <span data-ttu-id="60446-124">Existente <xref:System.Uri> classe foi estendida no .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="60446-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="60446-125">3.0 SP1 e 2.0 SP1 para oferecer suporte a identificadores de recursos internacionais (IRI) e nomes de domínio internacionalizados (IDNS).</span><span class="sxs-lookup"><span data-stu-id="60446-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="60446-126">Os usuários atuais não verão qualquer alteração no comportamento do .NET Framework 2.0, a menos que eles permitem especificamente IRI e IDN suporte.</span><span class="sxs-lookup"><span data-stu-id="60446-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="60446-127">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="60446-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="60446-128">Para habilitar o suporte para IRI, as alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="60446-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="60446-129">Adicione a seguinte linha no arquivo Machine. config no diretório do .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="60446-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="60446-130">Especifique se as regras de análise de IRI deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="60446-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="60446-131">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="60446-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="60446-132">Habilitar a análise de IRI (iriParsing habilitado = `true`) fará a normalização e regras de verificação de acordo com a IRI mais recente de caractere em RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="60446-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="60446-133">O valor padrão é `false` e normalização e verificação de acordo com RFC 2396 e RFC 3986 de caracteres (para literais IPv6).</span><span class="sxs-lookup"><span data-stu-id="60446-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="60446-134">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="60446-134">Configuration Files</span></span>  
 <span data-ttu-id="60446-135">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="60446-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60446-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60446-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="60446-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="60446-137">Description</span></span>  
 <span data-ttu-id="60446-138">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="60446-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="60446-139">Código</span><span class="sxs-lookup"><span data-stu-id="60446-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60446-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60446-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="60446-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="60446-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
