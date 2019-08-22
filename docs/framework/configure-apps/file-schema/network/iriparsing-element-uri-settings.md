---
title: Elemento <iriParsing> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 2c99edf2f1a03e0e510858c106cad43b0eaa27b4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664081"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="ea44f-102">\<Elemento de > iriParsing (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="ea44f-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="ea44f-103">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="ea44f-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="ea44f-104">Hierarquia de esquema</span><span class="sxs-lookup"><span data-stu-id="ea44f-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="ea44f-105">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="ea44f-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="ea44f-106">\<Elemento de > URI (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="ea44f-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="ea44f-107">\<iriParsing></span><span class="sxs-lookup"><span data-stu-id="ea44f-107">\<iriParsing></span></span>](iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="ea44f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea44f-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea44f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ea44f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ea44f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ea44f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea44f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ea44f-111">Attributes</span></span>  
  
|<span data-ttu-id="ea44f-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ea44f-112">**Element**</span></span>|<span data-ttu-id="ea44f-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ea44f-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="ea44f-114">Especifica se a análise de IRI está habilitada.</span><span class="sxs-lookup"><span data-stu-id="ea44f-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="ea44f-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ea44f-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea44f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ea44f-116">Child Elements</span></span>  
 <span data-ttu-id="ea44f-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ea44f-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea44f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ea44f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ea44f-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ea44f-119">**Element**</span></span>|<span data-ttu-id="ea44f-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ea44f-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ea44f-121">uri</span><span class="sxs-lookup"><span data-stu-id="ea44f-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="ea44f-122">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="ea44f-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea44f-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea44f-123">Remarks</span></span>  
 <span data-ttu-id="ea44f-124">A classe <xref:System.Uri> existente foi estendida no .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="ea44f-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="ea44f-125">3,0 SP1 e 2,0 SP1 para fornecer suporte para IRI (identificadores de recursos internacionais) e IDNs (nomes de domínio internacionalizados).</span><span class="sxs-lookup"><span data-stu-id="ea44f-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="ea44f-126">Os usuários atuais não verão nenhuma alteração do comportamento .NET Framework 2,0, a menos que eles especificamente habilitem o suporte a IRI e IDN.</span><span class="sxs-lookup"><span data-stu-id="ea44f-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="ea44f-127">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ea44f-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ea44f-128">Para habilitar o suporte para IRI, as duas alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="ea44f-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="ea44f-129">Adicione a seguinte linha ao arquivo Machine. config no diretório .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="ea44f-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="ea44f-130">Especifique se as regras de análise de IRI devem ser aplicadas.</span><span class="sxs-lookup"><span data-stu-id="ea44f-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="ea44f-131">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="ea44f-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="ea44f-132">Habilitar a análise de IRI (iriParsing Enabled `true`=) fará a normalização e a verificação de caracteres de acordo com as regras de IRI mais recentes no RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="ea44f-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="ea44f-133">O valor padrão é `false` e fará a normalização e a verificação de caracteres de acordo com RFC 2396 e RFC 3986 (para literais IPv6).</span><span class="sxs-lookup"><span data-stu-id="ea44f-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="ea44f-134">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="ea44f-134">Configuration Files</span></span>  
 <span data-ttu-id="ea44f-135">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ea44f-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea44f-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ea44f-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ea44f-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea44f-137">Description</span></span>  
 <span data-ttu-id="ea44f-138">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a análise de IRI e nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="ea44f-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ea44f-139">Código</span><span class="sxs-lookup"><span data-stu-id="ea44f-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea44f-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea44f-140">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="ea44f-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="ea44f-141">Network Settings Schema</span></span>](index.md)
