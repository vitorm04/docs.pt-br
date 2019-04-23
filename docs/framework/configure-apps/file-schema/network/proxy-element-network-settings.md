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
ms.openlocfilehash: 8df9bbf2615776c2e023f03401785da95b2226eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204816"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="8276b-102">\<proxy > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8276b-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="8276b-103">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="8276b-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="8276b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8276b-104">\<configuration></span></span>  
<span data-ttu-id="8276b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8276b-105">\<system.net></span></span>  
<span data-ttu-id="8276b-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="8276b-106">\<defaultProxy></span></span>  
<span data-ttu-id="8276b-107">\<proxy></span><span class="sxs-lookup"><span data-stu-id="8276b-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8276b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8276b-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8276b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8276b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8276b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8276b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8276b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="8276b-111">Attributes</span></span>  
  
|<span data-ttu-id="8276b-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="8276b-112">**Attribute**</span></span>|<span data-ttu-id="8276b-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="8276b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="8276b-114">Especifica se o proxy é detectado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8276b-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="8276b-115">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="8276b-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="8276b-116">Especifica se o proxy é ignorado para os recursos locais.</span><span class="sxs-lookup"><span data-stu-id="8276b-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="8276b-117">Recursos locais incluem o servidor local (`http://localhost`, `http://loopback`, ou `http://127.0.0.1`) e um URI sem um ponto (`http://webserver`).</span><span class="sxs-lookup"><span data-stu-id="8276b-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="8276b-118">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="8276b-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="8276b-119">Especifica o URI para usar o proxy.</span><span class="sxs-lookup"><span data-stu-id="8276b-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="8276b-120">Especifica o local do script de configuração.</span><span class="sxs-lookup"><span data-stu-id="8276b-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="8276b-121">Não use o `bypassonlocal` atributo com esse atributo.</span><span class="sxs-lookup"><span data-stu-id="8276b-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="8276b-122">Especifica se deve usar as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8276b-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="8276b-123">Se definido como `true`, atributos subsequentes substituirão as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8276b-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="8276b-124">O valor padrão é `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="8276b-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8276b-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8276b-125">Child Elements</span></span>  
 <span data-ttu-id="8276b-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8276b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8276b-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8276b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="8276b-128">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="8276b-128">**Element**</span></span>|<span data-ttu-id="8276b-129">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="8276b-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8276b-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="8276b-130">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="8276b-131">Configura o servidor de proxy de protocolo HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="8276b-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="8276b-132">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8276b-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8276b-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="8276b-133">Remarks</span></span>  
 <span data-ttu-id="8276b-134">O `proxy` elemento define um servidor proxy para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8276b-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="8276b-135">Se esse elemento estiver ausente do arquivo de configuração, o .NET Framework usará as configurações de proxy no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8276b-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="8276b-136">O valor para o `proxyaddress` atributo deve ser um bem formado indicador URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="8276b-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="8276b-137">O `scriptLocation` atributo refere-se a detecção automática de scripts de configuração de proxy.</span><span class="sxs-lookup"><span data-stu-id="8276b-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="8276b-138">O <xref:System.Net.WebProxy> classe tentará localizar um script de configuração (normalmente nomeado WPAD) quando o **usar script de configuração automática** opção for selecionada no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8276b-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="8276b-139">Se `bypassonlocal` é definido como qualquer valor, `scriptLocation` será ignorado.</span><span class="sxs-lookup"><span data-stu-id="8276b-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="8276b-140">Use o `usesystemdefault` atributo para aplicativos do .NET Framework versão 1.1 que estão migrando para a versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="8276b-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="8276b-141">Uma exceção é lançada se o `proxyaddress` atributo especifica um proxy padrão inválido.</span><span class="sxs-lookup"><span data-stu-id="8276b-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="8276b-142">O <xref:System.Exception.InnerException%2A> propriedade sobre a exceção deve ter mais informações sobre a causa do erro.</span><span class="sxs-lookup"><span data-stu-id="8276b-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8276b-143">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="8276b-143">Configuration Files</span></span>  
 <span data-ttu-id="8276b-144">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8276b-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8276b-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8276b-145">Example</span></span>  
 <span data-ttu-id="8276b-146">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignore o proxy para acesso local.</span><span class="sxs-lookup"><span data-stu-id="8276b-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8276b-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8276b-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="8276b-148">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="8276b-148">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
