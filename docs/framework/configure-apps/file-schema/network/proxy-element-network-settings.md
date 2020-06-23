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
ms.openlocfilehash: 8ae30b8c29dcf3aaa183ff295c7ee8592322797f
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141775"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="a37a9-104">Elemento \<proxy> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="a37a9-104">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="a37a9-105">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="a37a9-105">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="a37a9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a37a9-106">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a37a9-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a37a9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a37a9-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a37a9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a37a9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a37a9-109">Attributes</span></span>  
  
|<span data-ttu-id="a37a9-110">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="a37a9-110">**Attribute**</span></span>|<span data-ttu-id="a37a9-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a37a9-111">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="a37a9-112">Especifica se o proxy é detectado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a37a9-112">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="a37a9-113">O valor padrão é `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="a37a9-113">The default value is `Unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="a37a9-114">Especifica se o proxy é ignorado para os recursos locais.</span><span class="sxs-lookup"><span data-stu-id="a37a9-114">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="a37a9-115">Os recursos locais incluem o servidor local ( `http://localhost` , `http://loopback` ou `http://127.0.0.1` ) e um URI sem um ponto ( `http://webserver` ).</span><span class="sxs-lookup"><span data-stu-id="a37a9-115">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="a37a9-116">O valor padrão é `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="a37a9-116">The default value is `Unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="a37a9-117">Especifica o URI de proxy a ser usado.</span><span class="sxs-lookup"><span data-stu-id="a37a9-117">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="a37a9-118">Especifica o local do script de configuração.</span><span class="sxs-lookup"><span data-stu-id="a37a9-118">Specifies the location of the configuration script.</span></span> <span data-ttu-id="a37a9-119">Não use o `bypassonlocal` atributo com este atributo.</span><span class="sxs-lookup"><span data-stu-id="a37a9-119">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="a37a9-120">Especifica se as configurações de proxy do Internet Explorer devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="a37a9-120">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="a37a9-121">Se definido como `True` , os atributos subsequentes substituirão as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a37a9-121">If set to `True`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="a37a9-122">O valor padrão é `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="a37a9-122">The default value is `Unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a37a9-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a37a9-123">Child Elements</span></span>  
 <span data-ttu-id="a37a9-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a37a9-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a37a9-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a37a9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a37a9-126">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a37a9-126">**Element**</span></span>|<span data-ttu-id="a37a9-127">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a37a9-127">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a37a9-128">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="a37a9-128">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a37a9-129">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="a37a9-129">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="a37a9-130">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="a37a9-130">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a37a9-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="a37a9-131">Remarks</span></span>  
 <span data-ttu-id="a37a9-132">O `proxy` elemento define um servidor proxy para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a37a9-132">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="a37a9-133">Se esse elemento estiver ausente no arquivo de configuração, o .NET Framework usará as configurações de proxy no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a37a9-133">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="a37a9-134">O valor do `proxyaddress` atributo deve ser um URI (Uniform Resource Indicator) bem formado.</span><span class="sxs-lookup"><span data-stu-id="a37a9-134">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="a37a9-135">O `scriptLocation` atributo refere-se à detecção automática de scripts de configuração de proxy.</span><span class="sxs-lookup"><span data-stu-id="a37a9-135">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="a37a9-136">A <xref:System.Net.WebProxy> classe tentará localizar um script de configuração (geralmente chamado WPAD. dat) quando a opção **usar script de configuração automática** estiver selecionada no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a37a9-136">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="a37a9-137">Se `bypassonlocal` é definido como qualquer valor, `scriptLocation` é ignorado.</span><span class="sxs-lookup"><span data-stu-id="a37a9-137">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="a37a9-138">Use o `usesystemdefault` atributo para os aplicativos .NET Framework versão 1,1 que estão migrando para a versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="a37a9-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="a37a9-139">Uma exceção será gerada se o `proxyaddress` atributo especificar um proxy padrão inválido.</span><span class="sxs-lookup"><span data-stu-id="a37a9-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="a37a9-140">A <xref:System.Exception.InnerException%2A> Propriedade na exceção deve ter mais informações sobre a causa raiz do erro.</span><span class="sxs-lookup"><span data-stu-id="a37a9-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a37a9-141">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a37a9-141">Configuration Files</span></span>  
 <span data-ttu-id="a37a9-142">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a37a9-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a37a9-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a37a9-143">Example</span></span>  
 <span data-ttu-id="a37a9-144">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local.</span><span class="sxs-lookup"><span data-stu-id="a37a9-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a37a9-145">Veja também</span><span class="sxs-lookup"><span data-stu-id="a37a9-145">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a37a9-146">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a37a9-146">Network Settings Schema</span></span>](index.md)
