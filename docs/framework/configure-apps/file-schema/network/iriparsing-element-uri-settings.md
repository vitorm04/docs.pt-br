---
title: Elemento <iriParsing> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698100"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="2906a-102">\<iriParsing > elemento (configurações de URI)</span><span class="sxs-lookup"><span data-stu-id="2906a-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="2906a-103">Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="2906a-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[<span data-ttu-id="2906a-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2906a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2906a-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2906a-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="2906a-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<iriParsing >**</span><span class="sxs-lookup"><span data-stu-id="2906a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2906a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2906a-107">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2906a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2906a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2906a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2906a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2906a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2906a-110">Attributes</span></span>  
  
|<span data-ttu-id="2906a-111">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2906a-111">**Element**</span></span>|<span data-ttu-id="2906a-112">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2906a-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="2906a-113">Especifica se a análise de IRI está habilitada.</span><span class="sxs-lookup"><span data-stu-id="2906a-113">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="2906a-114">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="2906a-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2906a-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2906a-115">Child Elements</span></span>  
 <span data-ttu-id="2906a-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2906a-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2906a-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2906a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2906a-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2906a-118">**Element**</span></span>|<span data-ttu-id="2906a-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2906a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2906a-120">uri</span><span class="sxs-lookup"><span data-stu-id="2906a-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="2906a-121">Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).</span><span class="sxs-lookup"><span data-stu-id="2906a-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2906a-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="2906a-122">Remarks</span></span>  
 <span data-ttu-id="2906a-123">A classe <xref:System.Uri> existente foi estendida em .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="2906a-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="2906a-124">3,0 SP1 e 2,0 SP1 para fornecer suporte para IRI (identificadores de recursos internacionais) e IDNs (nomes de domínio internacionalizados).</span><span class="sxs-lookup"><span data-stu-id="2906a-124">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="2906a-125">Os usuários atuais não verão nenhuma alteração do comportamento .NET Framework 2,0, a menos que eles especificamente habilitem o suporte a IRI e IDN.</span><span class="sxs-lookup"><span data-stu-id="2906a-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="2906a-126">Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2906a-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2906a-127">Para habilitar o suporte para IRI, as duas alterações a seguir são necessárias:</span><span class="sxs-lookup"><span data-stu-id="2906a-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="2906a-128">Adicione a seguinte linha ao arquivo Machine. config no diretório .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="2906a-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="2906a-129">Especifique se as regras de análise de IRI devem ser aplicadas.</span><span class="sxs-lookup"><span data-stu-id="2906a-129">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="2906a-130">Isso pode ser feito no arquivo machine.config ou em app.config.</span><span class="sxs-lookup"><span data-stu-id="2906a-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="2906a-131">Habilitar a análise de IRI (iriParsing Enabled `true`=) fará a normalização e a verificação de caracteres de acordo com as regras de IRI mais recentes no RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="2906a-131">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="2906a-132">O valor padrão é `false` e fará a normalização e a verificação de caracteres de acordo com RFC 2396 e RFC 3986 (para literais IPv6).</span><span class="sxs-lookup"><span data-stu-id="2906a-132">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="2906a-133">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="2906a-133">Configuration Files</span></span>  
 <span data-ttu-id="2906a-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2906a-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2906a-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2906a-135">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2906a-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="2906a-136">Description</span></span>  
 <span data-ttu-id="2906a-137">O exemplo a seguir mostra uma configuração usada pela classe <xref:System.Uri> para dar suporte à análise IRI e a nomes IDN.</span><span class="sxs-lookup"><span data-stu-id="2906a-137">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2906a-138">Código</span><span class="sxs-lookup"><span data-stu-id="2906a-138">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2906a-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2906a-139">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="2906a-140">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2906a-140">Network Settings Schema</span></span>](index.md)
