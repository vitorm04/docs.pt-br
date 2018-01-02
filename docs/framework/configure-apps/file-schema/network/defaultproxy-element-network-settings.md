---
title: "&lt;defaultProxy&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d0b09f5c845fc9a18c2a1dd919272c2924478eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultproxygt-element-network-settings"></a><span data-ttu-id="6c65b-102">&lt;defaultProxy&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="6c65b-102">&lt;defaultProxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6c65b-103">Configura o servidor de proxy do protocolo HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="6c65b-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="6c65b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6c65b-104">\<configuration></span></span>  
<span data-ttu-id="6c65b-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="6c65b-105">\<system.net></span></span>  
<span data-ttu-id="6c65b-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="6c65b-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c65b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c65b-107">Syntax</span></span>  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c65b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c65b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6c65b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6c65b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c65b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c65b-110">Attributes</span></span>  
  
|<span data-ttu-id="6c65b-111">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6c65b-111">**Element**</span></span>|<span data-ttu-id="6c65b-112">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6c65b-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="6c65b-113">Especifica se um proxy da web é usado.</span><span class="sxs-lookup"><span data-stu-id="6c65b-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="6c65b-114">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="6c65b-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="6c65b-115">Especifica se as credenciais padrão para este host são usadas para acessar o proxy da web.</span><span class="sxs-lookup"><span data-stu-id="6c65b-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="6c65b-116">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="6c65b-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c65b-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6c65b-117">Child Elements</span></span>  
  
|<span data-ttu-id="6c65b-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6c65b-118">**Element**</span></span>|<span data-ttu-id="6c65b-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6c65b-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6c65b-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="6c65b-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="6c65b-121">Fornece um conjunto de expressões regulares que descrevem os endereços que não usam o proxy.</span><span class="sxs-lookup"><span data-stu-id="6c65b-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="6c65b-122">módulo</span><span class="sxs-lookup"><span data-stu-id="6c65b-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="6c65b-123">Adiciona um novo módulo de proxy para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c65b-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="6c65b-124">proxy</span><span class="sxs-lookup"><span data-stu-id="6c65b-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="6c65b-125">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="6c65b-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c65b-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6c65b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="6c65b-127">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6c65b-127">**Element**</span></span>|<span data-ttu-id="6c65b-128">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6c65b-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6c65b-129">System.NET</span><span class="sxs-lookup"><span data-stu-id="6c65b-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="6c65b-130">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="6c65b-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c65b-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c65b-131">Remarks</span></span>  
 <span data-ttu-id="6c65b-132">Se o elemento defaultProxy estiver vazio, as configurações de proxy do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="6c65b-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="6c65b-133">Esse comportamento é diferente da versão 1.1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c65b-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="6c65b-134">Uma exceção será lançada se o [módulo](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) elemento Especifica um tipo não público, o tipo não é derivada do <xref:System.Net.IWebProxy> classe, ocorreu uma exceção do construtor padrão do objeto ou uma exceção ocorreu enquanto Recuperando o proxy padrão do sistema especificado.</span><span class="sxs-lookup"><span data-stu-id="6c65b-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="6c65b-135">O <xref:System.Exception.InnerException%2A> propriedade sobre a exceção deve ter mais informações sobre a causa do erro.</span><span class="sxs-lookup"><span data-stu-id="6c65b-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6c65b-136">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="6c65b-136">Configuration Files</span></span>  
 <span data-ttu-id="6c65b-137">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6c65b-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c65b-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c65b-138">Example</span></span>  
 <span data-ttu-id="6c65b-139">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local e contoso.com.</span><span class="sxs-lookup"><span data-stu-id="6c65b-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c65b-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c65b-140">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="6c65b-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="6c65b-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
