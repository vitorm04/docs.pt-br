---
title: Elemento <proxy> (Configurações de Rede)
description: O <proxy> elemento de configurações de rede define as opções de servidor proxy no .NET Framework. Este artigo inclui um exemplo.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 0d462fcc92fc1be5ddbc2e76237d8436219c7295
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504531"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="dbb73-104">Elemento \<proxy> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="dbb73-104">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="dbb73-105">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="dbb73-105">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="dbb73-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbb73-106">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbb73-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dbb73-107">Attributes and Elements</span></span>  
 <span data-ttu-id="dbb73-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dbb73-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbb73-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="dbb73-109">Attributes</span></span>  
  
|<span data-ttu-id="dbb73-110">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="dbb73-110">**Attribute**</span></span>|<span data-ttu-id="dbb73-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="dbb73-111">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="dbb73-112">Especifica se o proxy é detectado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="dbb73-112">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="dbb73-113">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="dbb73-113">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="dbb73-114">Especifica se o proxy é ignorado para os recursos locais.</span><span class="sxs-lookup"><span data-stu-id="dbb73-114">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="dbb73-115">Os recursos locais incluem o servidor local ( `http://localhost` , `http://loopback` ou `http://127.0.0.1` ) e um URI sem um ponto ( `http://webserver` ).</span><span class="sxs-lookup"><span data-stu-id="dbb73-115">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="dbb73-116">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="dbb73-116">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="dbb73-117">Especifica o URI de proxy a ser usado.</span><span class="sxs-lookup"><span data-stu-id="dbb73-117">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="dbb73-118">Especifica o local do script de configuração.</span><span class="sxs-lookup"><span data-stu-id="dbb73-118">Specifies the location of the configuration script.</span></span> <span data-ttu-id="dbb73-119">Não use o `bypassonlocal` atributo com este atributo.</span><span class="sxs-lookup"><span data-stu-id="dbb73-119">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="dbb73-120">Especifica se as configurações de proxy do Internet Explorer devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="dbb73-120">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="dbb73-121">Se definido como `true` , os atributos subsequentes substituirão as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="dbb73-121">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="dbb73-122">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="dbb73-122">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbb73-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dbb73-123">Child Elements</span></span>  
 <span data-ttu-id="dbb73-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dbb73-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbb73-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dbb73-125">Parent Elements</span></span>  
  
|<span data-ttu-id="dbb73-126">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="dbb73-126">**Element**</span></span>|<span data-ttu-id="dbb73-127">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="dbb73-127">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dbb73-128">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="dbb73-128">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="dbb73-129">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="dbb73-129">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="dbb73-130">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="dbb73-130">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbb73-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbb73-131">Remarks</span></span>  
 <span data-ttu-id="dbb73-132">O `proxy` elemento define um servidor proxy para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dbb73-132">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="dbb73-133">Se esse elemento estiver ausente no arquivo de configuração, o .NET Framework usará as configurações de proxy no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="dbb73-133">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="dbb73-134">O valor do `proxyaddress` atributo deve ser um URI (Uniform Resource Indicator) bem formado.</span><span class="sxs-lookup"><span data-stu-id="dbb73-134">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="dbb73-135">O `scriptLocation` atributo refere-se à detecção automática de scripts de configuração de proxy.</span><span class="sxs-lookup"><span data-stu-id="dbb73-135">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="dbb73-136">A <xref:System.Net.WebProxy> classe tentará localizar um script de configuração (geralmente chamado WPAD. dat) quando a opção **usar script de configuração automática** estiver selecionada no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="dbb73-136">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="dbb73-137">Se `bypassonlocal` é definido como qualquer valor, `scriptLocation` é ignorado.</span><span class="sxs-lookup"><span data-stu-id="dbb73-137">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="dbb73-138">Use o `usesystemdefault` atributo para os aplicativos .NET Framework versão 1,1 que estão migrando para a versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="dbb73-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="dbb73-139">Uma exceção será gerada se o `proxyaddress` atributo especificar um proxy padrão inválido.</span><span class="sxs-lookup"><span data-stu-id="dbb73-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="dbb73-140">A <xref:System.Exception.InnerException%2A> Propriedade na exceção deve ter mais informações sobre a causa raiz do erro.</span><span class="sxs-lookup"><span data-stu-id="dbb73-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dbb73-141">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="dbb73-141">Configuration Files</span></span>  
 <span data-ttu-id="dbb73-142">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="dbb73-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbb73-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dbb73-143">Example</span></span>  
 <span data-ttu-id="dbb73-144">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local.</span><span class="sxs-lookup"><span data-stu-id="dbb73-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbb73-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="dbb73-145">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="dbb73-146">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="dbb73-146">Network Settings Schema</span></span>](index.md)
