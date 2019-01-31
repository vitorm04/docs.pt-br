---
title: Elemento <iriParsing> (configurações de Uri)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: a4d4df8c214efb955f8f9d6678aaf8d56de71ebc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256650"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="ff578-102">\<iriParsing > (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="ff578-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="ff578-103">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="ff578-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="ff578-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="ff578-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="ff578-105">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="ff578-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="ff578-106">\<URI > (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="ff578-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="ff578-107">\<iriParsing></span><span class="sxs-lookup"><span data-stu-id="ff578-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="ff578-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff578-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff578-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff578-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ff578-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ff578-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff578-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff578-111">Attributes</span></span>  
  
|<span data-ttu-id="ff578-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ff578-112">**Element**</span></span>|<span data-ttu-id="ff578-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ff578-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="ff578-114">Especifica se a análise de IRI está habilitada.</span><span class="sxs-lookup"><span data-stu-id="ff578-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="ff578-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ff578-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff578-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff578-116">Child Elements</span></span>  
 <span data-ttu-id="ff578-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ff578-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff578-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff578-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ff578-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ff578-119">**Element**</span></span>|<span data-ttu-id="ff578-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ff578-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ff578-121">uri</span><span class="sxs-lookup"><span data-stu-id="ff578-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="ff578-122">Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="ff578-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff578-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff578-123">Remarks</span></span>  
 <span data-ttu-id="ff578-124">Existente <xref:System.Uri> classe foi estendido no .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="ff578-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="ff578-125">3.0 SP1 e 2.0 SP1 para fornecer suporte a identificadores de recursos internacionais (IRI) e nomes de domínio internacionalizado (IDN).</span><span class="sxs-lookup"><span data-stu-id="ff578-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="ff578-126">Os usuários atuais não verão qualquer mudança do comportamento do .NET Framework 2.0, a menos que eles especificamente habilitarem IRI e IDN dão suporte.</span><span class="sxs-lookup"><span data-stu-id="ff578-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="ff578-127">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff578-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ff578-128">Para habilitar o suporte IRI, duas alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="ff578-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="ff578-129">Adicione a seguinte linha ao arquivo Machine. config no diretório do .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="ff578-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="ff578-130">Especifique se as regras de análise de IRI deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="ff578-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="ff578-131">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="ff578-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="ff578-132">Habilitar a análise de IRI (iriParsing habilitado = `true`) executará a normalização e regras de caractere de verificação de acordo com a mais recentes de IRI na RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="ff578-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="ff578-133">O valor padrão é `false` e normalização e verificação de acordo com RFC 2396 e RFC 3986 de caracteres (para literais IPv6).</span><span class="sxs-lookup"><span data-stu-id="ff578-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="ff578-134">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="ff578-134">Configuration Files</span></span>  
 <span data-ttu-id="ff578-135">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ff578-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff578-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff578-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ff578-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff578-137">Description</span></span>  
 <span data-ttu-id="ff578-138">O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe para dar suporte à análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="ff578-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ff578-139">Código</span><span class="sxs-lookup"><span data-stu-id="ff578-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff578-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff578-140">See also</span></span>
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="ff578-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="ff578-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
