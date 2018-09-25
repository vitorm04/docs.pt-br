---
title: '&lt;iriParsing&gt; (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 446447f0d279755dbc06e0e3a25d50ad86ad555b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075209"
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="64b22-102">&lt;iriParsing&gt; (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="64b22-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="64b22-103">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="64b22-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="64b22-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="64b22-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="64b22-105">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="64b22-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="64b22-106">\<URI > (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="64b22-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="64b22-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="64b22-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="64b22-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64b22-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64b22-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="64b22-109">Attributes and Elements</span></span>  
 <span data-ttu-id="64b22-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="64b22-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64b22-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="64b22-111">Attributes</span></span>  
  
|<span data-ttu-id="64b22-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="64b22-112">**Element**</span></span>|<span data-ttu-id="64b22-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="64b22-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="64b22-114">Especifica se a análise de IRI está habilitada.</span><span class="sxs-lookup"><span data-stu-id="64b22-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="64b22-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="64b22-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64b22-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="64b22-116">Child Elements</span></span>  
 <span data-ttu-id="64b22-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="64b22-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64b22-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="64b22-118">Parent Elements</span></span>  
  
|<span data-ttu-id="64b22-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="64b22-119">**Element**</span></span>|<span data-ttu-id="64b22-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="64b22-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="64b22-121">URI</span><span class="sxs-lookup"><span data-stu-id="64b22-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="64b22-122">Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="64b22-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64b22-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="64b22-123">Remarks</span></span>  
 <span data-ttu-id="64b22-124">Existente <xref:System.Uri> classe foi estendido no .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="64b22-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="64b22-125">3.0 SP1 e 2.0 SP1 para fornecer suporte a identificadores de recursos internacionais (IRI) e nomes de domínio internacionalizado (IDN).</span><span class="sxs-lookup"><span data-stu-id="64b22-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="64b22-126">Os usuários atuais não verão qualquer mudança do comportamento do .NET Framework 2.0, a menos que eles especificamente habilitarem IRI e IDN dão suporte.</span><span class="sxs-lookup"><span data-stu-id="64b22-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="64b22-127">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="64b22-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="64b22-128">Para habilitar o suporte IRI, duas alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="64b22-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="64b22-129">Adicione a seguinte linha ao arquivo Machine. config no diretório do .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="64b22-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="64b22-130">Especifique se as regras de análise de IRI deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="64b22-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="64b22-131">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="64b22-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="64b22-132">Habilitar a análise de IRI (iriParsing habilitado = `true`) executará a normalização e regras de caractere de verificação de acordo com a mais recentes de IRI na RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="64b22-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="64b22-133">O valor padrão é `false` e normalização e verificação de acordo com RFC 2396 e RFC 3986 de caracteres (para literais IPv6).</span><span class="sxs-lookup"><span data-stu-id="64b22-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="64b22-134">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="64b22-134">Configuration Files</span></span>  
 <span data-ttu-id="64b22-135">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="64b22-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64b22-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64b22-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="64b22-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="64b22-137">Description</span></span>  
 <span data-ttu-id="64b22-138">O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe para dar suporte à análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="64b22-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="64b22-139">Código</span><span class="sxs-lookup"><span data-stu-id="64b22-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64b22-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64b22-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="64b22-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="64b22-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
