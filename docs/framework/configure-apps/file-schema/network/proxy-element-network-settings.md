---
title: Elemento <proxy> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154784"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="76642-102">\<proxy> Element (Configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="76642-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="76642-103">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="76642-103">Defines a proxy server.</span></span>  

<span data-ttu-id="76642-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76642-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76642-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="76642-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="76642-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de proxy padrão**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="76642-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="76642-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>proxy**</span><span class="sxs-lookup"><span data-stu-id="76642-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="76642-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76642-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76642-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="76642-109">Attributes and Elements</span></span>  
 <span data-ttu-id="76642-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="76642-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76642-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="76642-111">Attributes</span></span>  
  
|<span data-ttu-id="76642-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="76642-112">**Attribute**</span></span>|<span data-ttu-id="76642-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="76642-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="76642-114">Especifica se o proxy é detectado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="76642-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="76642-115">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="76642-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="76642-116">Especifica se o proxy é ignorado para os recursos locais.</span><span class="sxs-lookup"><span data-stu-id="76642-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="76642-117">Os recursos locais incluem`http://localhost` `http://loopback`o `http://127.0.0.1`servidor local ( ou`http://webserver`) e um URI sem um período ( ).</span><span class="sxs-lookup"><span data-stu-id="76642-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="76642-118">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="76642-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="76642-119">Especifica o URI proxy a ser usado.</span><span class="sxs-lookup"><span data-stu-id="76642-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="76642-120">Especifica a localização do script de configuração.</span><span class="sxs-lookup"><span data-stu-id="76642-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="76642-121">Não use `bypassonlocal` o atributo com este atributo.</span><span class="sxs-lookup"><span data-stu-id="76642-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="76642-122">Especifica se deve usar as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="76642-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="76642-123">Se definido `true`como , atributos subseqüentes substituirão as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="76642-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="76642-124">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="76642-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76642-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="76642-125">Child Elements</span></span>  
 <span data-ttu-id="76642-126">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="76642-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76642-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="76642-127">Parent Elements</span></span>  
  
|<span data-ttu-id="76642-128">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="76642-128">**Element**</span></span>|<span data-ttu-id="76642-129">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="76642-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="76642-130">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="76642-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="76642-131">Configura o servidor proxy Hypertext Transfer Protocol (HTTP).</span><span class="sxs-lookup"><span data-stu-id="76642-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="76642-132">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="76642-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76642-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="76642-133">Remarks</span></span>  
 <span data-ttu-id="76642-134">O `proxy` elemento define um servidor proxy para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76642-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="76642-135">Se esse elemento estiver ausente do arquivo de configuração, o .NET Framework usará as configurações de proxy no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="76642-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="76642-136">O valor `proxyaddress` para o atributo deve ser um Indicador de Recurso Uniforme (URI) bem formado.</span><span class="sxs-lookup"><span data-stu-id="76642-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="76642-137">O `scriptLocation` atributo refere-se à detecção automática de scripts de configuração proxy.</span><span class="sxs-lookup"><span data-stu-id="76642-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="76642-138">A <xref:System.Net.WebProxy> classe tentará localizar um script de configuração (geralmente chamado Wpad.dat) quando a opção **Usar script de configuração automática** for selecionada no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="76642-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="76642-139">Se `bypassonlocal` for definido como `scriptLocation` valor, é ignorado.</span><span class="sxs-lookup"><span data-stu-id="76642-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="76642-140">Use `usesystemdefault` o atributo para aplicativos .NET Framework versão 1.1 que estão migrando para a versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="76642-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="76642-141">Uma exceção é `proxyaddress` lançada se o atributo especificar um proxy padrão inválido.</span><span class="sxs-lookup"><span data-stu-id="76642-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="76642-142">A <xref:System.Exception.InnerException%2A> propriedade na exceção deve ter mais informações sobre a causa raiz do erro.</span><span class="sxs-lookup"><span data-stu-id="76642-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="76642-143">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="76642-143">Configuration Files</span></span>  
 <span data-ttu-id="76642-144">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="76642-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76642-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76642-145">Example</span></span>  
 <span data-ttu-id="76642-146">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço proxy e ignora o proxy para acesso local.</span><span class="sxs-lookup"><span data-stu-id="76642-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76642-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="76642-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="76642-148">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="76642-148">Network Settings Schema</span></span>](index.md)
